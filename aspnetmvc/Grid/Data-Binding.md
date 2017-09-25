---
layout: post
title: DataBinding with Grid widget for Syncfusion Essential JS
description: How to bind in-memory JSON and remote web services in Grid
platform: ejmvc
control: Grid
documentation: ug
--- 
# Data Binding

Grid `DataSource` property allows to bind datasource as the instance of one of the following types.
   
*	Collection that implements IEnumerable or IEnumerable&lt;T&gt;.
*	DataTable.
*	ITypedList.
*	REST Service URL as string.
*	Table – Allows to bind HTML Table and it accepts table template script "ID".
*	ORM components such as Entity Framework/Linq to SQL.
     
We can also bind the above type of datasource by using lambda Expressions of Grid `DataSource` Property.
  
In the following section, let us see on how to bind various datasources to Grid using `DataSource` API.
  
## IEnumerable
 
The Grid can be bound with either non-generic collection or generic collection that implements [IEnumerable](https://msdn.microsoft.com/en-us/library/system.collections.ienumerable.aspx) interface. It can be assigned to Grid’s `DataSource` property.
    
N> When using `DataSource` builder, the IEnumerable datasource can be passed as parameter either directly to the `DataSource` builder or to the `Json` property of the `DataSource` builder.  
  
The following code example describes the above behavior.
  
{% tabs %} 
{% highlight razor %}

       @(Html.EJ().Grid<Person>("Grid")
            .Datasource((IEnumerable<Person>)ViewBag.datasource)
            .Columns(col => 
            {
                col.Field(p => p.FirstName).HeaderText("First Name").TextAlign(TextAlign.Left).Add();
                col.Field(p => p.LastName).HeaderText("Last Name").TextAlign(TextAlign.Left).Add();
                col.Field(p => p.Email).HeaderText("Email").TextAlign(TextAlign.Left).Add();
            }))
{% endhighlight  %}
{% highlight c# %}

       namespace Grid.Controllers
         {    
         public class HomeController : Controller
          {        
           public ActionResult Index()
            {
            List<Person> Persons = new List<Person>();
            Persons.Add(new Person() { FirstName = "John", LastName = "Beckett", Email = "john@syncfusion.com" });
            Persons.Add(new Person() { FirstName = "Ben", LastName = "Beckett", Email = "ben@syncfusion.com" });
            Persons.Add(new Person() { FirstName = "Andrew", LastName = "Beckett", Email = "andrew@syncfusion.com" });
            ViewBag.datasource = Persons;
            return View();
            }
          }
        }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img1.png)

##  DataTable

A DataTable, which represents one table of in-memory relational data that has in-built schema to work easily with data column and data row objects.

Binding DataTable to Grid is a very simpler way that you only need to set DataTable model to Grid `DataSource` API.

The following code example describes the above behavior.

{% tabs %} 
{% highlight razor %}

         @(Html.EJ().Grid<object>("FlatGrid")
                .Datasource((System.Data.DataTable)ViewBag.dataSource)
         )
{% endhighlight  %}
{% highlight c# %}
        
        namespace EJGrid.Controllers
         {
          public class HomeController : Controller
           {
            public ActionResult Index()
            {
              DataTable dt = new DataTable("Table1");
              DataColumn cl = new DataColumn("No");
              dt.Columns.Add(cl);
              cl = new DataColumn("Name");
              dt.Columns.Add(cl);

              DataRow dataRow = dt.NewRow();
              dataRow[0] = 1;
              dataRow[1] = "John";
              dt.Rows.Add(dataRow);
              
              dataRow = dt.NewRow();
              dataRow[0] = 2;
              dataRow[1] = "Smith";
              dt.Rows.Add(dataRow);

              dataRow = dt.NewRow();
              dataRow[0] = 3;
              dataRow[1] = "Tomps";
              dt.Rows.Add(dataRow);

              dataRow = dt.NewRow();
              dataRow[0] = 4;
              dataRow[1] = "Hanar";
              dt.Rows.Add(dataRow);

              dataRow = dt.NewRow();
              dataRow[0] = 5;
              dataRow[1] = "Reek";
              dt.Rows.Add(dataRow);

              ViewBag.dataSource = dt;
             return View();
            }
          }
       }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img2.png)

##  Entity Framework

The collection of business objects generated from Entity Framework ORM can be used as Grid`s datasource. The Grid can be used with Entity Framework using either code first technique or Database first technique.

The following code example describes the above behavior.

{% tabs %} 
{% highlight razor %}

        @(Html.EJ().Grid<OrdersView>("Grid")
                 .Datasource((IEnumerable<OrdersView>)ViewBag.datasource)
                 .AllowPaging()
                 .Columns(col =>
                  {
                     col.Field(p => p.OrderID).HeaderText("Order ID").TextAlign(TextAlign.Right).Add();
                     col.Field(p => p.CustomerID).HeaderText("Customer ID").Add();
                     col.Field(p => p.EmployeeID).HeaderText("Employee ID").TextAlign(TextAlign.Right).Add();
                     col.Field(p => p.Freight).HeaderText("Freight").Format("{0:C2}").TextAlign(TextAlign.Right).Add();
                 })
              )
{% endhighlight  %}
{% highlight c# %}
            
         namespace Grid.Controllers
        {    
          public class HomeController : Controller
          {
           public ActionResult Index()
           {
            ViewBag.datasource = new NORTHWNDEntities().OrdersView.ToList();
            return View();
           }
         }
        }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img3.png)

See Also

For more information on creating and consuming Entity Framework, please refer this [link]( https://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc). 


## LINQ to SQL

The LINQ to SQL can be used as the data source of the Grid. And the Object Relation class which is used to map with Relational table, can be used as the type of the Grid to leverage the Data Annotation.
      
The following code example describes the above behavior.

{% tabs %} 
{% highlight razor %}
       
        @(Html.EJ().Grid<OrdersView>("Grid")
            .Datasource((IEnumerable<OrdersView>)ViewBag.datasource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field(p => p.OrderID).HeaderText("Order ID").TextAlign(TextAlign.Right).Add();
                col.Field(p => p.CustomerID).HeaderText("Customer ID").Add();
                col.Field(p => p.EmployeeID).HeaderText("Employee ID").TextAlign(TextAlign.Right).Add();
                col.Field(p => p.Freight).HeaderText("Freight").Format("{0:C2}").TextAlign(TextAlign.Right).Add();
            }))
{% endhighlight  %}
{% highlight c# %}    
        
      namespace Grid.Controllers
       {    
        public class HomeController : Controller
         {
        public ActionResult Index()
         {
            ViewBag.datasource = new NorthwindDataContext().OrdersViews.ToList();
            return View();
          }
        }    
      }
{% endhighlight  %}
{% endtabs %}      

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img4.png)

See Also

For more information on using LINQ to SQL please refer to this [link]( http://weblogs.asp.net/scottgu/using-linq-to-sql-part-1)


##  ITypedList Binding 
      
ITypedList provides functionality to discover the schema for a binding list, where the properties available to bind differ from the public properties of the object to bind.

To implement ITypedList binding, create a generic type named class that derives from ITypedList interface. Define the named class based on properties descriptor of the Grid Model class, to return list according to the custom implementation.

Create a collection of ITypedList and bind it to Grid using `DataSource` property.

The following code example describes the above behavior.

{% tabs %} 
{% highlight razor %} 

     @(Html.EJ().Grid<object>("FlatGrid")
         .Datasource((IEnumerable<object>)ViewBag.dataSource)
         .AllowPaging()
         .Columns(col =>
        {
            col.Field("OrderID").Add();
            col.Field("CustomerID").Add();
            col.Field("Freight").Add();
            col.Field("ShipCountry").Add();
            col.Field("ShipCity").Add();
        })
     )
{% endhighlight  %}
{% highlight c# %} 

         [Serializable()]
         public class SortableBindingList<T> : BindingList<T>, ITypedList
         {
          [NonSerialized()]
          private PropertyDescriptorCollection properties;
          public SortableBindingList()
             : base()
            {
               // Get the 'shape' of the list. 
              // Only get the public properties marked with Browsable = true.
             PropertyDescriptorCollection propertyDescriptorCollection = TypeDescriptor.GetProperties(
                 typeof(T),
                 new Attribute[] { new BrowsableAttribute(true) });

             // Sort the properties.
             properties = propertyDescriptorCollection.Sort();
            }
          public PropertyDescriptorCollection GetItemProperties(PropertyDescriptor[] listAccessors)
          {
             PropertyDescriptorCollection propertyDescriptorCollection;
             if (listAccessors != null && listAccessors.Length > 0)
             {
                // Return child list shape.
                propertyDescriptorCollection = ListBindingHelper.GetListItemProperties(listAccessors[0].PropertyType);
             }
             else
             {
                // Return properties in sort order.
                propertyDescriptorCollection = properties;
             }
             return propertyDescriptorCollection;
          }
          // This method is only used in the design-time Framework 
         // and by the obsolete DataGrid control.
         public string GetListName(PropertyDescriptor[] listAccessors)
         {
           return typeof(T).Name;
         }
      }

     namespace EJGrid.Controllers
     {
      public class HomeController : Controller
       {
         public ActionResult Index()
         {
            var data = OrderRepository.GetAllRecords();
            SortableBindingList<EditableOrder> order = new SortableBindingList<EditableOrder>();
            
            foreach (var temp in data)
            {
                order.Add(temp);
            }
            ViewBag.dataSource = order;
            return View();
          }
        }
      }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img5.png)

See Also

For more information on ITypedList interface please refer to this [link](https://msdn.microsoft.com/en-us/library/System.ComponentModel.ITypedList.aspx).

##  Complex Binding

The Grid can display nested or navigation properties in the column that would provide the way to display the field from another entity. The complex property can be provided in the `Field` property builder either as string value concatenated by dot or using lambda Expression.   

N> 1. To use lambda Expression, the Grid should be associated with some business object and `Field` definition using lambda expression will not work for dynamic object.
N> 2. To display navigation properties using complex binding, the corresponding property should be eager loaded. Lazy loading is not supported for complex binding. 
  
The following code example describes the above behavior.

{% tabs %} 
{% highlight razor %}
        
        @(Html.EJ().Grid<Person>("Grid")
            .Datasource((IEnumerable<Person>)ViewBag.datasource)
            .Columns(col => 
            {
                col.Field(p => p.FirstName).HeaderText("First Name").TextAlign(TextAlign.Left).Add();
                col.Field(p => p.LastName).HeaderText("Last Name").TextAlign(TextAlign.Left).Add();
                col.Field(p => p.Designation.Position).HeaderText("Designation").TextAlign(TextAlign.Left).Add();
                col.Field(p => p.Email).HeaderText("Email").TextAlign(TextAlign.Left).Add();
            })
          )
{% endhighlight  %}
{% highlight c# %} 
       
        namespace Grid.Controllers
        {    
          public class HomeController : Controller
           {        
           public ActionResult Index()
            {
             List<Person> Persons = new List<Person>();
            Persons.Add(new Person() { FirstName = "John", LastName = "Beckett", Email = "john@syncfusion.com", Designation = new Designation{ Position = "Manager"  } });
            Persons.Add(new Person() { FirstName = "Ben", LastName = "Beckett", Email = "ben@syncfusion.com", Designation = new Designation{ Position = "Asst. Manager" } });
            Persons.Add(new Person() { FirstName = "Andrew", LastName = "Beckett", Email = "andrew@syncfusion.com", Designation = new Designation{ Position = "Engineer"  } });
            ViewBag.datasource = Persons;
            return View();
           }
         }
       }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img6.png)

W> A navigation property that represents the "many" end of a relationship cannot be specified using lambda expression. Instead `Field` name can be provide as string in such as case.
  
##  WCF DataService / OData Service

WCF Data Services is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of representational state transfer (REST).

To consume WCF DataService in Grid control, provide the service link directly to the Grid `DataSource` property.

We have an online OData Service `http://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders` created specifically for Syncfusion Controls

The following code example describes the above behavior.

{% tabs %} 
{% highlight razor %}
    
        @(Html.EJ().Grid<object>("FlatGrid")
            .Datasource("http://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders")
            .AllowPaging()
            .Columns(col =>
             {
               col.Field("OrderID").Add();
               col.Field("EmployeeID").Add();
               col.Field("CustomerID").Add();
               col.Field("ShipCountry").Add();
               col.Field("Freight").Add();
           })
         )
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img7.png)

See Also

To create WCF Data Service in your web application refer [here](https://msdn.microsoft.com/en-us/library/cc668184.aspx).

##  ODataV4 Service

ODataV4Adaptor is used for consuming data from OData V4 Service. To consume OData V4 service, set the service link to the `URL` property of Grid `DataSource` and set `AdaptorType.ODataV4Adaptor` to the `Adaptor` Property of Grid `DataSource`

W> ODL supports to parse the `$search` query option, however, Web API OData doesn’t support it so far. 

The following code example describes the above behavior.

{% tabs %} 
{% highlight razor %}

         @(Html.EJ().Grid<object>("FlatGrid")
             .Datasource(datasource => datasource.URL("http://services.odata.org/v4/northwind/northwind.svc/Orders").Adaptor(AdaptorType.ODataV4Adaptor))
             .AllowPaging()
             .Columns(col =>
             {
              col.Field("OrderID").Add();
              col.Field("EmployeeID").Add();
              col.Field("CustomerID").Add();
              col.Field("ShipCountry").Add();
              col.Field("Freight").Add();
            })
          )
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img8.png)

##  Web API Service

Web API Adaptor is used for processing request and response messages from Web API Service.

To consume Web API service, set the service link to the `URL` property of Grid `DataSource` and you can set adaptor type as `AdaptorType.WebApiAdaptor` to the `Adaptor` Property of Grid `DataSource`

 I> The datasource from Web API service must be returned as object that has property `Items` with its value as datasource and another property `Count` with its value as datasource’s total records count.

DataOperation queries such as sorting, filtering, etc., would be sent to Web API Service corresponding to Grid actions performed and they need to be handled manually as Web API Service does not process it by default.

 N> In ASP.NET core default casing as camelCase.So, we need to return the data as JSON and the JSON object must contain a property as `result` with dataSource as its value and one more property `count` with the dataSource total records count as its value.
 
The following code example describes the above behavior.
    
{% tabs %} 
{% highlight razor %}
    
        @(Html.EJ().Grid<object>("FlatGrid")
             .Datasource(datasource => datasource.URL("/api/Orders").Adaptor(AdaptorType.WebApiAdaptor))
             .AllowPaging()
             .Columns(col =>
              {
               col.Field("OrderID").Add();
               col.Field("EmployeeID").Add();
               col.Field("CustomerID").Add();
               col.Field("ShipCountry").Add();
               col.Field("Freight").Add();
              })
            )
{% endhighlight  %}
{% highlight c# %} 
    
        namespace EJGrid.Controllers
         {
          public class OrdersController: ApiController 
           { 
            // GET: api/Orders 
            NORTHWNDEntities db = new NORTHWNDEntities(); 
            public object Get() 
           { 
             var queryString = HttpContext.Current.Request.QueryString; 
             int skip = Convert.ToInt32(queryString["$skip"]); 
             int take = Convert.ToInt32(queryString["$top"]); 
             var data = db.Orders.ToList(); 
             return new { Items = data.Skip(skip).Take(take), Count = data.Count() }; 
            } 
          } 
        }
{% endhighlight  %}
{% endtabs %}        

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img9.png)

##  HTML Table binding

HTML table can be set as a data source for grid. The ID of the HTML table should be assigned to the `Table` property of the `DataSource` API.

I> HTML table is the only valid element to use through `DataManager`.
  
The following code example describes the above behavior.
 
{% tabs %}  
{% highlight razor %}

        @(Html.EJ().Grid<object>("Grid")
              .Datasource(datasource => datasource.Table("#GridTable"))            
              .Columns(col =>
               {
                col.Field("Laptop").HeaderText("Laptop").TextAlign(TextAlign.Left).Add();
                col.Field("Model").HeaderText("Model").TextAlign(TextAlign.Left).Add();
                col.Field("Price").HeaderText("Price").Add();
                col.Field("OS").HeaderText("OS").TextAlign(TextAlign.Left).Add();
                col.Field("RAM").HeaderText("RAM").TextAlign(TextAlign.Left).Add();
                col.Field("ScreenSize").HeaderText("Screen size").Add();
              })
           )
{% endhighlight  %}
{% highlight js %}
    
      <script id="GridTable" type="text/template">
       <table>
          <thead>
               <tr>
                  <th>Laptop</th>
                  <th>Model</th>
                  <th>Price</th>
                  <th>OS</th>
                  <th>RAM</th>
                  <th>ScreenSize</th>
              </tr>
          </thead>
          <tbody>
             <tr>
                 <td>Dell Vostro</td>
                 <td>2520</td>
                 <td>39990</td>
                 <td>Windows 8</td>
                 <td>4GB</td>
                 <td>15.6</td>
             </tr>
             <tr>
                 <td>HP Pavilion Sleekbook</td>
                 <td>14-B104AU</td>
                 <td>22800</td>
                 <td>Windows 8</td>
                 <td>2GB</td>
                 <td>14</td>
             </tr>
             <tr>
                 <td>Sony Vaio</td>
                 <td>E14A15</td>
                 <td>42500</td>
                 <td>Windows 7 Home Premium</td>
                 <td>4GB DDR3 RAM</td>
                 <td>14</td>
             </tr>
             <tr>
                 <td>Lenovo</td>
                 <td>Yoga 13</td>
                 <td>57000</td>
                 <td>Windows 8 RT</td>
                 <td>2GB DDR3 RAM</td>
                 <td>11.6</td>
             </tr>
             <tr>
                 <td>Toshiba</td>
                 <td>L850-Y3110</td>
                 <td>57700</td>
                 <td>Windows 8 SL</td>
                 <td>8GB DDR3 RAM</td>
                 <td>15.6</td>
             </tr>
            </tbody>
          </table>
       </script>
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img10.png)

##  Miscellaneous

###  Load On Demand

By default, Grid with remote data binding will work in `On-Demand` concept for which either `Paging` or `VirtualScrolling` feature should be enabled in Grid. It helps improving performance of loading a large data set.

The following code example describes the above behavior.

 {% tabs %}  
 {% highlight razor %} 
 
         @(Html.EJ().Grid<object>("FlatGrid")
             .Datasource("http://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders")
             .AllowPaging()
             .Columns(col =>
              {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("ShipCountry").Add();
                col.Field("Freight").Add();
              })
           )
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img11.png)

###  Load at once

`Load at once` concept in Grid can be used to load all data from remote service at a single request and all further Grid action will be performed at client-side on the cached data.

`Offline` property of Grid `DataSource` is used to enable `Load at once` in Grid control

The following code example describes the above behavior.

{% tabs %}  
{% highlight razor %} 
        
         @(Html.EJ().Grid<object>("FlatGrid")
              .Datasource(datasource =>   datasource.URL("http://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders").Offline(true))              
              .AllowPaging()
              .Columns(col =>
              {
                 col.Field("OrderID").Add();
                 col.Field("EmployeeID").Add();
                 col.Field("CustomerID").Add();
                 col.Field("ShipCountry").Add();
                 col.Field("Freight").Add();
               })
            )
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img12.png)

###  Data caching

The `DataManager` can cache loaded data. The caching functionality can be enabled by setting the `EnableCaching` property in `DataManager`.
    
The `TimeTillExpiration` and `CachingPageSize` properties are used to control the expiration time of data and the cache page size settings respectively.

N> window`s localStorage is used to cache the loaded data. 

The following code example describes the above behavior.

{% tabs %}  
{% highlight razor %} 
   
          @(Html.EJ().Grid<OrdersView>("Grid")
                .Datasource(datasource => datasource.URL(@Url.Action("DataSource"))
                .EnableCaching()
                .CachingPageSize(4)
                .TimeTillExpiration(120000)
                .Adaptor(AdaptorType.UrlAdaptor))
                .AllowPaging()
                .Columns(col =>
                 {
                    col.Field(p => p.OrderID).HeaderText("Order ID").Add();
                    col.Field(p => p.CustomerID).HeaderText("Customer ID").TextAlign(TextAlign.Left).Add();
                    col.Field(p => p.EmployeeID).HeaderText("Employee ID").Add();
                    col.Field(p => p.Freight).HeaderText("Freight").Format("{0:C2}").Add();
                 })
             )
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img13.png)

###  Custom request parameters and HTTP Header

####  Adding request parameters

The ‘addParams’ function in DataManager’s Query class can be used to add additional custom parameter in data requests. The Grid has an option to set default Query which can be used to add custom parameter.
      
The following code example describes the above behavior.

{% tabs %}  
{% highlight razor %} 
 
      @(Html.EJ().Grid<OrdersView>("Grid")
            .Datasource(datasource => datasource.URL(@Url.Action("DataSource"))
            .Adaptor(AdaptorType.UrlAdaptor))
            .Query("ej.Query().addParams('Syncfusion', true)")
            .AllowPaging()
            .Columns(col =>
             {
                col.Field(p => p.OrderID).HeaderText("Order ID").Add();
                col.Field(p => p.CustomerID).HeaderText("Customer ID").TextAlign(TextAlign.Left).Add();
                col.Field(p => p.EmployeeID).HeaderText("Employee ID").Add();
                col.Field(p => p.Freight).HeaderText("Freight").Format("{0:C2}").Add();
            })
          )
{% endhighlight  %}
{% endtabs %}

E> Attempting to add custom parameters with key name same as any default AJAX parameters used by `DataManager` will results in error.

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img14.png)

####  Adding custom HTTP headers

The Custom header can be added through `DataManager` `Headers` options. While performing, CRUD operations, the `addParams` cannot be used to send additional parameters to the server in such cases the parameters can be send as custom header.

The following code example describes the above behavior.

{% tabs %}  
{% highlight razor %} 
        
           @(Html.EJ().Grid<OrdersView>("Grid")
                 .Datasource(datasource => datasource.URL(@Url.Action("DataSource"))
                 .Headers(new { Syncfusion = false })
                 .Adaptor(AdaptorType.UrlAdaptor))
                 .AllowPaging()
                 .Columns(col =>
                 {
                   col.Field(p => p.OrderID).HeaderText("Order ID").Add();
                   col.Field(p => p.CustomerID).HeaderText("Customer ID").TextAlign(TextAlign.Left).Add();
                   col.Field(p => p.EmployeeID).HeaderText("Employee ID").Add();
                   col.Field(p => p.Freight).HeaderText("Freight").Format("{0:C2}").Add();
                })
              )
{% endhighlight  %}
{% endtabs %}

N>  To add custom headers to the DataManager through JavaScript, refer to this [link]( https://www.syncfusion.com/kb/5963)

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img15.png)

###  Handling HTTP Errors

During server interaction from the Grid, there may occur some server-side exceptions and you can acquire those error messages or exception details in client-side using `ActionFailure` event of Grid control.

The argument passed to the `ActionFailure` Grid event contains the error details returned from server. Please refer the following table for some error details that would be acquired in client-side event arguments.
              
<table>
<tr>
<th>Parameter</th>
<th>Description</th>
</tr>
<tr>
<td>arguments.error.status</td>
<td>It returns the response error code.</td></tr>
<tr>
<td>arguments.error.statusText</td>
<td>It returns the error message.</td>
</tr>
 </table>
              
The following code example describes the above behavior.

{% tabs %}  
{% highlight razor %} 

        @(Html.EJ().Grid<OrdersView>("Grid")
                   .Datasource(datasource => datasource.URL(@Url.Action("DataSources"))
                   .Adaptor(AdaptorType.UrlAdaptor))
                   .Columns(col =>
                   {
                       col.Field(p => p.OrderID).HeaderText("Order ID").Add();
                       col.Field(p => p.CustomerID).HeaderText("Customer ID").TextAlign(TextAlign.Left).Add();
                       col.Field(p => p.EmployeeID).HeaderText("Employee ID").Add();
                       col.Field(p => p.Freight).HeaderText("Freight").Format("{0:C2}").Add();
                   })
                    .ClientSideEvents(event => event.ActionFailure("OnActionFailure"))
              )
{% endhighlight  %}
{% highlight js %}

             <script>
                 function OnActionFailure(args) {
                     alert(args.error.status + " : " + args.error.statusText);
                 }
             </script>
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img16.png)