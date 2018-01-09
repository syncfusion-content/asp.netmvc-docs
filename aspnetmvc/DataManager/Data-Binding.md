---
layout: post
title: Data Binding | AutoComplete | ASP.NET MVC | Syncfusion
description: data binding
platform: ejmvc
control: DataManager
documentation: ug
keywords: JSON data, OData, OData4, WebAPI, Web Method, Data Binding
---

# Data Binding

## Local 

A data source can be bound to a Grid through the DataManager. The DataManager supports JSON array binding. It is useful to bind records in a client-side by using JSON data that is very helpful in Single Page Application (SPA) and in feature rich web application. To achieve this, you can refer to the following code example.

{% tabs %}

{% highlight CSHTML %}

//connection local reference

@(Html.EJ().DataManager("FlatData").URL("Home/DataSource").Adaptor(AdaptorType.UrlAdaptor))

@(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")
        .DataManagerID("FlatData")
        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).where('CustomerID', 'equal', 'VINET').take(5)")
        //where(fieldName, operator, value, [ignoreCase])
        .Columns(col =>
        {
            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();

        })
)

{% endhighlight %}

{% highlight C# %}

public class HomeController : Controller
{
    public ActionResult Index()
    {
        return View();
    }
    public ActionResult DataSource(Syncfusion.JavaScript.DataManager dataManagerObj)
    {
        var DataSource = OrderRepository.GetAllRecords();
        DataResult result = new DataResult();
        result.result = DataSource.Skip(dataManagerObj.Skip).Take(dataManagerObj.Take).ToList();
        result.count = DataSource.Count();
        return Json(result, JsonRequestBehavior.AllowGet);
    }
    public class DataResult
    {
        public IEnumerable<EditableOrder> result { get; set; }
        public int count { get; set; }
    }

}

{% endhighlight %}

{% endtabs %} 

The result of the above code example is illustrated as follows.

![](Data-Binding_images/Data-Binding_img1.png)

Binding local data to grid
{:.caption}

## REST Services

## OData binding

OData is a standardized protocol for creating and consuming data. You can retrieve data from OData service by using DataManager. You can refer to the following code example of remote Data binding by using the OData service.


{% highlight CSHTML %}

    @Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/").Adaptor(AdaptorType.ODataAdaptor).CrossDomain(true)

    @(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")

            .DataManagerID("FlatData")
            .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).take(5)")
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
                col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
                col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
            })
    )

{% endhighlight %}


The result of the above code example is illustrated as follows.

![](Data-Binding_images/Data-Binding_img2.png)

OData binding
{:.caption}

## OData V4

The OData v4 is an improved version of OData protocols and the DataManager can also retrieve and consume OData v4 services.  For more details on OData v4 Services, refer to the [odata documentation](http://www.odata.org/documentation/).

You can refer to the following code example for consuming OData v4 services and bind the result to the Grid. In the the following code, crossDomain is enabled to make cross domain request.

{% highlight html %}

    @Html.EJ().DataManager("FlatData").URL("http://services.odata.org/V4/Northwind/Northwind.svc/Orders").Adaptor(AdaptorType.ODataV4Adaptor).CrossDomain(true)

    @(Html.EJ().Grid<object>("FlatGrid")
            .DataManagerID("FlatData")
            .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).take(5)")
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
                col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
                col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
            })
    )

{% endhighlight %}

The request and response to the service from the DataManager are illustrated as follows.

The result of the above code example is illustrated as follows.

![](Data-Binding_images/Data-Binding_img3.png)


OData v4 request and response
{:.caption}

![](Data-Binding_images/Data-Binding_img4.png)

OData v4 binding
{:.caption}

## WebAPI binding

The Web API is a programmatic interface to define the request and response messages system that is mostly exposed in JSON or XML. The DataManager contains default adaptor to handle the Web API request and responses. The WebApiAdaptor is discussed briefly in the Adaptor section.

Refer to the following code example for consuming the Web API data by using the DataManager.

{% highlight CSHTML %}

    @Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/UGService/api/Orders").Adaptor(AdaptorType.WebApiAdaptor).CrossDomain(true)

    @(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")
            .DataManagerID("FlatData")
            .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).where('CustomerID', 'equal', 'VINET').take(5)")
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
                col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
                col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
            })
    )

{% endhighlight %}

The request to the Web API and response is illustrated as follows.

![](Data-Binding_images/Data-Binding_img5.png)

Web API adaptor request and response
{:.caption}

The result for the above code example is illustrated as follows.

![](Data-Binding_images/Data-Binding_img6.png)

Web API data binding
{:.caption}

## Other Web Services binding

The DataManager can also retrieve data from the ASP.NET Web methods and ASP.NET MVC Controller`s action. You can achieve this by using the UrlAdaptor of the DataManager. The UrlAdaptor is discussed briefly in the adaptor section.  By default, the URL Adaptor is used when accessing remote data. 

Refer to the following code example to know how the DataManager can be used to consume data from the web method.

Create a sample using ASP.NET Web Services

{% highlight html %}

    public class WebService1 : System.Web.Services.WebService
    {
        static string cons = ConfigurationManager.ConnectionStrings["SQLConnectionString"].ConnectionString;
        static SqlConnection con = new SqlConnection(cons);

        [WebMethod]
        public DataTable Get()
        {
            SqlCommand getData = new SqlCommand();
            getData.CommandText = "USP_DEV_ChangeLog_Select"; // Stored procedure for retrieve data from suppliers table
            getData.CommandType = CommandType.StoredProcedure;
            getData.Connection = con;
            if (con.State != ConnectionState.Open)
                con.Open();
            DataTable sqlData = new DataTable();
            SqlDataAdapter sqlAdapter = new SqlDataAdapter(getData);
            sqlData.TableName = "Suppliers";
            sqlAdapter.Fill(sqlData);
            return sqlData;
        }
    }

{% endhighlight %}

In the above code snippet, we have created web services by using the ASP.NET web service and bound dataSource to Grid, in code behind GetDataSource method.

{% highlight html %}

    [WebMethod]
    [ScriptMethod(ResponseFormat = ResponseFormat.Json)] // Return the JSON formatted result
    public static object GetDataSource()
    {
        CRUD_Service.WebService1 service = new CRUD_Service.WebService1();
        var sqlData = service.Get();   // Get data from web services
        DataResult result = new DataResult();
        List<EditableCustomer> data = (from demand in sqlData.AsEnumerable() // Perform skip take for on demand load paging
                                        select new EditableCustomer
                                        {
                                            OrderID = demand.ItemArray[0].ToString(),
                                            CustomerID = demand.ItemArray[1].ToString(),
                                            EmployeeID = demand.ItemArray[5].ToString(),
                                            Freight = demand.ItemArray[7].ToString(),
                                            ShipCity = demand.ItemArray[8].ToString()
                                        }).ToList();

        con.Close();
        return data;
    }

{% endhighlight %}

{% highlight CSHTML %}

    @Html.EJ().DataManager("FlatData").URL("WebService1.asmx/GetDataSource"))

    @(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")
            .DataManagerID("FlatData")
            .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).take(5)")
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
                col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
                col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();

            })
    )

{% endhighlight  %}

![](Data-Binding_images/Data-Binding_img7.png)

ASP.NET Web service binding
{:.caption}

## Complex Data Sorting

You can perform a data operation based on nested column data and bind to the data control. Here, if you want to perform the server side data operation for the nested dataSource like sorting, grouping, filtering, searching, take, or skip then we have to define the generic type of dataSource.

{% highlight CSHTML %}

@(Html.EJ().Grid<object>("FlatGrid")
        .Datasource(ds => ds.URL("GetData").Adaptor(AdaptorType.UrlAdaptor))
                .ToolbarSettings(toolBar => toolBar.ShowToolbar().ToolbarItems(items =>
                {
                    items.AddTool(ToolBarItems.ExcelExport);
                    items.AddTool(ToolBarItems.WordExport);
                    items.AddTool(ToolBarItems.PdfExport);
                }))
                .AllowSorting()
        .AllowPaging()
        .IsResponsive()

             .Columns(col =>
             {
                 col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(90).Add();
                 col.Field("CustomerID").HeaderText("Customer ID").Width(90).Add();
                 col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
                 col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
                 col.Field("ShipCity").HeaderText("Ship City").TextAlign(TextAlign.Right).Width(80).Add();
                 for (int i = 0; i < 2; i++)
                 {
                     col.Field("customer." + i + ".CustomerNumber").HeaderText("Customer Number " + i).Width(60).Add();
                     col.Field("customer." + i + ".OtherAddress").HeaderText("Customer Address2 " + i).Width(60).Add();
                 }
             })
)

{%endhighlight%}

{% highlight c# %}

public ActionResult GetData(Syncfusion.JavaScript.DataManager dataManager)
        {
            BindDataSource();
            IEnumerable<Orders> Data =order;             
            Syncfusion.JavaScript.DataSources.DataOperations operation = new Syncfusion.JavaScript.DataSources.DataOperations();
                       if (dataManager.Sorted != null && dataManager.Sorted.Count > 0) //Sorting
            {
                Data = operation.PerformSorting(Data,dataManager.Sorted);
            }

            int count=Data.AsQueryable().Count();

            return Json(new { result = Data, count = count }, JsonRequestBehavior.AllowGet);
        }

{%endhighlight%}

![](MVC_Sorting_images/complexdata.png)


