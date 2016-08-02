---
layout: post
title: Data binding in DropDownList control for Syncfusion ASP.NET MVC
description: Describes about the data binding in DropDownList control for Syncfusion ASP.NET MVC
platform: MVC
control: DropDownList
documentation: ug
keywords: DropDownList, dropdown, data binding, Local data, Remote data

---

# Data Binding

To populate data in the DropDownList control, define DataSource property with associated fields. You can bind any list data and other remote services in the DropDownList.

## Fields

The following properties provides you a way to bind either local or remote data to the DropDownList control.
<table>
    <tr>
        <th>
            Properties
            <br/>
        </th>
        <th>
            Description
            <br/>
        </th>
    </tr>
    <tr>
        <td>
            DataSource
            <br/>
        </td>
        <td>
            The data source contains the list of data for generating the popup list items.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            Query
            <br/>
        </td>
        <td>
            It specifies the query to retrieve the data from the online server.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            Fields
            <br/>
        </td>
        <td>
            It specifies the mapping fields for the data items of the DropDownList control.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            ID
            <br/>
        </td>
        <td>
            It specifies the ID of the tag.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            Text
            <br/>
        </td>
        <td>
            It specifies the text content of the tag.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            Value
            <br/>
        </td>
        <td>
            It specifies the value of the tag.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            Category
            <br/>
        </td>
        <td>
            It is used to categorize the items based on a specific field. The value mapped to this field must be able to group the popup items.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            ImageUrl
            <br/>
        </td>
        <td>
            It defines the image location.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            ImageAttributes
            <br/>
        </td>
        <td>
            It defines the image attributes such as height, width, styles, etc.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            SpriteCssClass
            <br/>
        </td>
        <td>
            It defines the sprite CSS for the image tag to add a prefix icon to all popup items.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            HtmlAttributes
            <br/>
        </td>
        <td>
            It defines the HTML attributes such as class and styles for an item.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            Selected
            <br/>
        </td>
        <td>
            This field defines the tag value to be selected initially. Corresponding field mapped has Boolean values to select the list items on control creation. The data with value true in this field is selected automatically when the control is initialized with checkbox.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            TableName
            <br/>
        </td>
        <td>
            It defines the table name for the tag value or displays text while rendering remote data.
            <br/>
        </td>
    </tr>
</table>

## Local Data

Define a List data and initialize the control with DataSource property. Specify the column names in the Fields property. <br/>

N> The columns are bounded automatically when the fields are specified with the default names like id, text, etc...

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Employee>)ViewData["LocalDataSource"]).DropDownListFields(Df => Df.Text("Text").Value("Country").Category("Role").ImageUrl("Image").ImageAttributes("ImgAttr"))
		
	{% endhighlight %}
    
    {% highlight css %}

    	.imgId {
        	margin: 0;
        	padding: 3px 10px 3px 3px;
        	border: 0 none;
        	width: 60px;
        	height: 60px;
        	float: none;
    	}

    {% endhighlight %}
    
    {% highlight c# %}
        public ActionResult Index()
        {
            List<Employee> EmpData = new List<Employee>();
            EmpData.Add(new Employee
            {
                Text = "Erik Linden",
                Role = "Executive",
                Country = "England",
                Image = "../Content/Employees/3.png",
                ImgAttr = "class='imgId'"
            });
            EmpData.Add(new Employee
            {
                Text = "John Linden",
                Role = "Representative",
                Country = "Norway",
                Image = "../Content/Employees/6.png",
                ImgAttr = "class='imgId'"
            });
            EmpData.Add(new Employee
            {
                Text = "Louis",
                Role = "Representative",
                Country = "Australia",
                Image = "../Content/Employees/7.png",
                ImgAttr = "class='imgId'"
            });
            EmpData.Add(new Employee
            {
                Text = "Lawrence",
                Role = "Executive",
                Country = "India",
                Image = "../Content/Employees/8.png",
                ImgAttr = "class='imgId'"
            });
            ViewData["LocalDataSource"] = EmpData;
            return View();
        }
        public class Employee
        {
            public string Text { get; set; }
            public string Role { get; set; }
            public string Country { get; set; }
            public string Image { get; set; }
            public string ImgAttr { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}


![](DataBinding_images/DataBinding_img1.jpeg)

N> Images for this sample are available in (installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\JavaScript\samples\web\themes\images<br/> 

## SQL Data Binding

Fetch the Data from SQL data source and initialize the control with DataSource property. Specify the column names in the Fields property. 

{% tabs %}

	{% highlight html %}
    
        @Html.EJ().DropDownList("selectEmp").Datasource((IEnumerable<Object>)ViewBag.Data).DropDownListFields(df => df.ID("Id").Text("Name").Value("Designation")).Width("150px")
		
	{% endhighlight %}
    
    {% highlight c# %}
        public ActionResult DropdownlistFeatures()
        {
            List<Employee> data = new List<Employee>();
            SqlConnection con = new SqlConnection(@"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=|DataDirectory|\SampleDB.mdf;Integrated Security=True");
            using (con)
            {
                con.Open();
                SqlDataReader myReader = null;
                SqlCommand myCommand = new SqlCommand("select * From [Table]",
                                                         con);
                myReader = myCommand.ExecuteReader();
                if (myReader.Read())
                {
                    
                        data.Add(new Employee(myReader["Name"].ToString(), myReader["Designation"].ToString()));
                    
                }
                con.Close();
                ViewBag.Data = data;
                
            }
            return View();
         }
        public class Employee
        {
            public string Name { get; set; }
            public string Designation { get; set; }
            public Employee(string name, string deg)
            {
                this.Name = name;
                this.Designation = deg;
            
            }
        }
    {% endhighlight %}
    
{% endtabs %}

## LINQ Data Binding

Language-Integrated Query (LINQ) is not only about retrieving data. It is also a powerful tool for transforming data. By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.

Defines model class

{% highlight C# %}

    public class Employee
    {
        public string name { set; get; }
        public string empID { set; get; }
        public string desgination { set; get; }
        public Employee() { }
        public Employee(string ename, string eid, string edesg)
        {
            name = ename;
            empID = eid;
            desgination = edesg;
        }
        
    }

{% endhighlight %}

In code behind, fetch the data from Employee class and assigned to the DropDownList as follows

{% highlight C# %}

    public ActionResult DropdownlistFeatures()
    {

        List<Employee> data = new List<Employee>() { };
        data.Add(new Employee("Nancy", "E11011", "Technical Writer"));
        data.Add(new Employee("Angel", "E11012", "Professor"));
        data.Add(new Employee("Daniah", "E11013", "Dancer"));
        data.Add(new Employee("Jenifer", "E11014", "Beautician"));
        data.Add(new Employee("Prince", "E11015", "Developer"));

        var db = from result in data
                    select result;

        ViewBag.dataSource = db.ToList();
        return View();
    }
    
{% endhighlight %}

{% highlight html %}

    @Html.EJ().DropDownList("selectCar").Datasource((IEnumerable<Employee>)ViewBag.datasource).DropDownListFields(df => df.ID("empID").Text("name").Value("desgination")).WatermarkText("Select a Student").Width("100%")

{% endhighlight %}

## XmlDataSource

XmlDataSource is used to work with XML documents. The following steps explain the details about the data binding from XmlDataSource

Step 1: Create an xml Data source as follows

{% highlight xml %}

    <?xml version="1.0" encoding="utf-8" ?>
    <Students>
    <Student>
        <Name>Abhishek</Name>
        <Location>Dhanbad</Location>
    </Student>
    <Student>
        <Name>Aman</Name>
        <Location>Samastipur</Location>
    </Student>
    <Student>
        <Name>Vicky</Name>
        <Location>Munger</Location>
    </Student>
    <Student>
        <Name>Chandan</Name>
        <Location>Bhagalpur</Location>
    </Student>
    <Student>
        <Name>Ravi</Name>
        <Location>Dhanbad</Location>
    </Student>
    </Students>
    
{% endhighlight %}

Step 2: Read data from the XML file

{% highlight C# %}

    using System.Xml;
    using DataBinding.Models;
    public ActionResult DropdownlistFeatures()
    {
        List<Product> data = new List<Product>();
        
        using (XmlReader reader = XmlReader.Create("D:/Sample/MVC/DataBinding/DataBinding/App_Data/XMLData.xml"))
        {
            while (reader.Read())
            {
                if (reader.IsStartElement())
                {
                    switch (reader.Name.ToString())
                    {
                        case "Name":
                            data.Add(new Product { name = reader.ReadString() });
                            break;
                    }
                }
            }
        }

    ViewBag.data = data;
    return View();
    }
    
{% endhighlight %}

Step 3: Assign the data to the DropDownList’s DataSource property. Specify the column names in the fields property.

{% highlight Razor %}

    @using DataBinding.Models
    @Html.EJ().DropDownList("selectCar").Datasource((IEnumerable<Product>)ViewBag.data).DropDownListFields(df => df.Text("name").Value("name")).WatermarkText("Select a Student").Width("100%")   

{% endhighlight %}

## EntityDataSource

Bind data to the DropDownList through Entity Framework. Please follow the below steps.

1.	Create an entity data model
Please refer the [link](http://www.entityframeworktutorial.net/EntityFramework5/create-dbcontext-in-entity-framework5.aspx) for more information

2.	Refer the entity data model to your project and bind the data to the DropDownList

In code behind, create an object for the Entity mode (NORTHWNDEntities) and fetch the data from the Employees class and stored it to the List.
Assign the data to the DropDownList’s DataSource property. Specify the column names in the fields property.


{% highlight C# %}

    public ActionResult DropdownlistFeatures()
    {
        NORTHWNDEntities sample = new NORTHWNDEntities();
        var dataset = sample.Employees
                    .Select(x => new Employee
                    {
                        EmployeeID = x.EmployeeID,
                        FirstName = x.FirstName                     
                    }).ToList();
        ViewBag.DataSource = dataset;
    }
    public class Employee
    {
        public int EmployeeID { get; set; }
        public string FirstName { get; set; }
    }

{% endhighlight %}

{% highlight Razor %}

    @Html.EJ().DropDownList("selectEmp").Datasource((IEnumerable<Object>)ViewBag. DataSource).DropDownListFields(df => df.Text("FirstName ").Value("EmployeeID ")).Width("150px")

{% endhighlight %}

## AccessDataSource

The data can also be bound to the DropDownList using OLEDB database as depicted below.

{% highlight Razor %}

    Html.EJ().DropDownList("selectEmp").Datasource((IEnumerable<Object>)ViewBag. DataSource).DropDownListFields(df => df.ID("Id").Text("Name").Value("Designation")).Width("150px")

{% endhighlight %}

The server-side code to retrieve and bind the data to DropDownList are as follows. Also, define a class with all the required fields as depicted in the below code example.

{% highlight C# %}

    public ActionResult DropdownlistFeatures()
    {            

        OleDbConnection conn = new OleDbConnection(@"Provider=Microsoft.Jet.OLEDB.4.0;Data Source=|DataDirectory|\Database.mdb");
        conn.Open();
        OleDbCommand cmd = new OleDbCommand(" SELECT * from [Employees]", conn);
        OleDbDataReader reader = null;
        List<EmpDetails> data = new List<EmpDetails>();
        reader = cmd.ExecuteReader();
        while (reader.Read())
        {
            data.Add(new EmpDetails(reader["Name"].ToString(), reader["Designation"].ToString()));
            
        }
        conn.Close();
        ViewBag. DataSource = data;
        

    }
    public class EmpDetails
    {
        public string Name { get; set; }
        public string Designation { get; set; }
        public EmpDetails(string name, string deg)
        {
            this.Name = name;
            this.Designation = deg;

        }
    }
    
{% endhighlight %}

## Linq to SQL Data Binding

The LINQ to SQL can be used as the data source of the DropDownList in which the data model of a relational database is mapped to an object model and allow us to use the LINQ technology to access SQL database.

To create LINQ to SQL classes
•	Right-click the App_Code folder and then click Add New Item.
•	Under Installed templates, select Linq to SQL Classes template, type a name for the .dbml file, and then click Add.
•	The Object Relational Designer window is displayed.
•	In Server Explorer, drag the database table into the Object Relational Designer window.
•	The table and its columns are represented as an entity in the designer window.

![](DataBinding_images/LinqtoSql.jpg)

In code behind, fetch the data from classes and stored it to the Viewbag as follows

{% highlight C# %}
    
    ViewBag.dataSource = new SampleDataContext().Customers.ToList();
    
{% endhighlight %}

{% highlight html %}

    @Html.EJ().DropDownList("customers").Datasource((IEnumerable<Customer>)ViewBag.dataSource).DropDownListFields(df => df.Text("CompanyName").Value("CustomerID")).WatermarkText("Select a Customer").Width("100%")
    
{% endhighlight %}
    
![](DataBinding_images/LinqtoSql2.jpg)

## Remote data 

To bind remote data to the DropDownList, you can assign a service data as an instance of DataManager to the Datasource property.

### OData

OData is a standardized protocol for creating and consuming data. You can provide the [OData service](http://www.odata.org/) URL directly to the Datasource URL property.

{% highlight html %}
               
       @Html.EJ().DropDownList("DropDownList1").Datasource(ds => ds.URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders")).DropDownListFields(df=>df.Text("ShipCountry").Value("OrderID"))
		
{% endhighlight %}
           
          
## OData Version 4

For OData Version 4 support ODataV4Adaptor should be used. By using URL property of Datasource, you can bind OData Version 4 Service link and specify  Adaptor value as enum AdaptorType.ODataV4Adaptor.

 
For further details about OData service please refer [the link](http://www.odata.org/).

{% highlight html %}

     @Html.EJ().DropDownList("DropDownList1").Datasource(ds => ds.URL("http://services.odata.org/V4/Northwind/Northwind.svc/Regions/").Adaptor(AdaptorType.ODataV4Adaptor)).DropDownListFields(df => df.Text("RegionDescription").Value("RegionID"))
     
{% endhighlight %}
           
           
![](DataBinding_images/DataBinding_img2.jpeg)

N> Events associated with remote data bind is listed [here](http://help.syncfusion.com/js/api/ejdropdownlist#events). 

## WebAPI

Using WebApiAdaptor, you can bind WebApi service’s data to DropDownList. The data from WebApi service must be returned as an object that has property “Items” with its value as data source and another property “Count” with its value as dataSource’s total records count.

{% highlight html %}

     @Html.EJ().DropDownList("DropDownList1").Datasource(ds => ds.URL("/api/Orders").Adaptor(AdaptorType.WebApiAdaptor)).DropDownListFields(df => df.Text("Name").Value("EmployeeID"))
     
{% endhighlight %}

{% highlight c# %}

    public class OrdersController : ApiController
    {
        NorthwindDataContext db = new NorthwindDataContext();
        
        // GET api/<controller>       
        public PageResult<EmployeePhoto> Get(ODataQueryOptions opts)
        {
            List<EmployeePhoto> emp = db.EmployeePhotos.ToList();            

            return new PageResult<EmployeePhoto>(emp as IEnumerable<EmployeePhoto>, null, emp.Count);
        }
    } 

{% endhighlight %}

![](DataBinding_images/DataBinding_img3.jpeg)

## Virtual Scrolling 

To improve the performance when displaying large data set, you can use “AllowVirtualScrolling” and VirtualScrollMode property. This retrieves only a fixed amount of list items and loads remaining data on scrolling. The items will be fetched via AJAX request.

This supports two modes of virtualization. They are,

* Normal Mode
* Continuous Mode

I> 1. Sorting and Grouping is not supported with Virtual Scrolling
I> 2. “VirtualScrollMode” property accepts Syncfusion.JavaScript.VirtualScrollMode enum value.

### Normal Mode

It loads the data on scrolling the list of items. This can be achieved by setting Syncfusion.JavaScript.VirtualScrollMode.Normal value to the VirtualScrollMode property.

{% highlight html %}

     @Html.EJ().DropDownList("DropDownList1").Datasource(ds => ds.URL("http://mvc.syncfusion.com/services/Northwnd.svc/Orders")).DropDownListFields(df => df.Text("ShipName").Value("ShipCountry")).AllowVirtualScrolling(true).VirtualScrollMode(VirtualScrollMode.Normal).ItemsCount(7)
     
{% endhighlight %}


### Continuous Mode

It loads the set of items when the scroller reaches at the end. This behaves like infinity scrolling. So when scroll reaches the end, it will fetch the remaining set of items and bind with your DropDownList. This can be achieved by setting Syncfusion.JavaScript.Continuous value to the "VirtualScrollMode" property.

N> In both modes, set of items will be fetched based on the count specified in the ItemsCount property and next set of items will be loaded on scrolling.

{% highlight html %}

     @Html.EJ().DropDownList("DropDownList1").Datasource(ds => ds.URL("http://mvc.syncfusion.com/services/Northwnd.svc/Orders")).DropDownListFields(df => df.Text("ShipName").Value("ShipCountry")).AllowVirtualScrolling(true).VirtualScrollMode(VirtualScrollMode.Continuous).ItemsCount(7)
     
{% endhighlight %}