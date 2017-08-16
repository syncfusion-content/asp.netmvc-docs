---
layout: post
title: WebAPI Batch Edit | DataManager | ASP.NET MVC | Syncfusion
description: WebAPI Batch Edit
platform: ejmvc
control: DataManager
documentation: ug
keywords: Insert of Records, Delete, Update, Read, Remove, Add Fields

---

# WebAPI Batch Edit

WebAPI Batch Editing is a unique feature, where requests to add, remove and change are handled altogether at a time rather than passing the request separately for each operation.Use the Save changes button to process all changes at once and cancel button to discard the changes.


## Configuration
Below are listed the steps for you to follow when configuring the DataManager for ASP.NET MVC to do batch updates.

In order to using batch in Web API, you should register a route with a batch handler or create an OWIN server. The below code creates the server and configures a web API route and a batch route.

{% highlight C# %}

using Microsoft.Owin;
using Owin;
using System.Web.Http;
using System.Web.Http.Batch;


[assembly: OwinStartupAttribute(typeof(Sample.Startup))]
namespace Sample
{
    public partial class Startup
    {
        public void Configuration(IAppBuilder app)
        {
            ConfigureAuth(app);

            HttpConfiguration config = new HttpConfiguration();

            config.MapHttpAttributeRoutes();


            HttpServer server = new HttpServer(config);
            config.Routes.MapHttpBatchRoute(
              routeName: "batch",
              routeTemplate: "api/batch",
              batchHandler: new DefaultHttpBatchHandler(server));

            app.UseWebApi(config);

            app.UseStaticFiles();
        }
    }
}


{% endhighlight %}

Web API uses route templates to determine which controller and action method to execute. At least one route template must be added into route table in order to handle various HTTP requests.

Route (WebApiConfig.cs):

{% highlight C# %}


config.Routes.MapHttpRoute(
                name: "api",
                routeTemplate: "api/{controller}/{id}",
                defaults: new { id = RouteParameter.Optional }
            );


{% endhighlight %}

Add a new class to the ~/Models folder. Name it Employee.

{% highlight C# %}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;

namespace Sample.Models
{
    interface IEmployeeRepository
    {
        IEnumerable<Employee> GetAll();
        Employee Get(int EmployeeID);
        Employee Add(Employee employee);
        void Remove(int EmployeeID);
        bool Update(Employee employee);
    }
    public class Employee
    {
        public int EmployeeID { get; set; }
        public string FirstName { get; set; }
        public string LastName { get; set; }

        public Employee()
        {

        }
        public Employee(int id, string LN, string FN)
        {
            this.EmployeeID = id;
            this.LastName = LN;
            this.FirstName = FN;

        }
    }
}

{% endhighlight %}

Add a new Repository Data Model class. Name it EmployeeRepository.

{% highlight C# %}


using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;

namespace Sample.Models
{
    public class EmployeeRepository : IEmployeeRepository
    {
        private List<Employee> employee = new List<Employee>();
       
        public EmployeeRepository()
        {
            employee.Add(new Employee(1, "Davolio", "Nancy"));
            employee.Add(new Employee(2, "Fuller", "Andrew"));
            employee.Add(new Employee(3, "Leverling", "Janet"));
            employee.Add(new Employee(4, "Peacock", "Margaret"));
            employee.Add(new Employee(5, "Buchanan", "Steven"));
        }

        public IEnumerable<Employee> GetAll()
        {
            return employee;
        }

        public Employee Get(int id)
        {
            return employee.Find(p => p.EmployeeID == id);
        }

        public Employee Add(Employee eObj)
        {
            if (eObj == null)
            {
                throw new ArgumentNullException("eObj");
            }
            employee.Add(eObj);
            return eObj;
        }

        public void Remove(int id)
        {
            employee.RemoveAll(p => p.EmployeeID == id);
        }

        public bool Update(Employee eObj)
        {
            if (eObj == null)
            {
                throw new ArgumentNullException("eObj");
            }
            int index = employee.FindIndex(p => p.EmployeeID == eObj.EmployeeID);
            if (index == -1)
            {
                return false;
            }
            employee.RemoveAt(index);
            employee.Add(eObj);
            return true;
        }
    }
}


{% endhighlight %}

Add a new ApiController name it as EmployeeController.cs and add a new Post/Put/Delete method which will return the Employee as JSON. The DataManager will make requests to this action based on route name.


{% highlight C# %}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Net;
using System.Net.Http;
using System.Web.Http;
using Sample.Models;
using System.Web;
using System.Threading.Tasks;

namespace Sample.Controllers
{
    public class EmployeeController : ApiController
    {
        static readonly IEmployeeRepository repository = new EmployeeRepository();
        [Route("get")]
        public async Task<object> Get()
        {
            await Task.Delay(1000);

            var queryString = HttpContext.Current.Request.QueryString;
            var data = repository.GetAll().ToList();
            return new { Items = data, Count = data.Count() };
        }
       

        public Employee GetEmployee(int id)
        {
            Employee employee = repository.Get(id);
            if (employee == null)
            {
                throw new HttpResponseException(HttpStatusCode.NotFound);
            }
            return employee;
        }

        [Route("post")]
        public async Task<IHttpActionResult> Post([FromBody] Employee employee)
        {

            if (employee == null)
            {
                return BadRequest(ModelState);
            }
            employee = repository.Add(employee);
            return Content(HttpStatusCode.OK, employee);
        }

        [Route("put")]
        public async Task<IHttpActionResult> Put([FromBody] Employee employee)
        {

            await Task.Delay(1000);
            if (employee == null)
            {
                return BadRequest(ModelState);
            }
            else 
            {

                if (!repository.Update(employee))
                {
                    throw new HttpResponseException(HttpStatusCode.NotFound);
                }
                return Content(HttpStatusCode.OK, employee);
            }
            
        }

        [Route("delete/{id}")]
        public async Task<IHttpActionResult> Delete(int id)
        {

            Employee employee = repository.Get(id);
            await Task.Delay(1000);
            if (employee == null)
            {
                return NotFound();
            }
            else
            {
                repository.Remove(id);
                return StatusCode(HttpStatusCode.OK);
            }
        }

    }
}


{% endhighlight %}

In the view, configure the Data manager to use the Post/Put/Delete methods created in the previous steps.

{% highlight C# %}

@(Html.EJ().DataManager("FlatData").BatchURL("/api/batch").UpdateURL("/put").RemoveURL("/delete").InsertURL("/post").Adaptor(AdaptorType.WebApiAdaptor))

@(Html.EJ().Grid<Sample.Models.Employee>("FlatGrid")
        .DataManagerID("FlatData")
        .Query("new ej.Query().select(['EmployeeID', 'FirstName', 'LastName'])")
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().EditMode(EditMode.Batch); })
                .ToolbarSettings(toolbar =>
                {
                    toolbar.ShowToolbar().ToolbarItems(items =>
                    {
                        items.AddTool(ToolBarItems.Add);
                        items.AddTool(ToolBarItems.Edit);
                        items.AddTool(ToolBarItems.Delete);
                        items.AddTool(ToolBarItems.Update);
                        items.AddTool(ToolBarItems.Cancel);
                    });
                })
        .Columns(col =>
        {
            col.Field("EmployeeID").HeaderText("EmployeeID").IsPrimaryKey(true).Width(75).Add();
            col.Field("FirstName").HeaderText("FirstName").Width(80).Add();
            col.Field("LastName").HeaderText("LastName").Add();
        })
)


{% endhighlight %}

Run the sample and perform batch operation. You can notice that the changes are reflected in the Database Table too.