---
layout: post
title: Grouping in ASP.NET MVC Grid Control | Syncfusion
description: Learn here about Grouping support in Syncfusion Essential ASP.NET MVC Grid Control, its elements, and more.
platform: ejmvc
control: Grid
documentation: ug
---
# Grouping in ASP.NET MVC Grid

The Grid control has options to group the records based on the required column. When grouping is applied, grouped records are organized into a hierarchical structure to facilitate easier expand and collapse of records. To enable grouping, set `AllowGrouping` property as `true`.

Columns can be grouped by simply dragging the column header and drop on the group drop area or simply click the group button which is displayed in the column. By default, sorting is done while grouping the column.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

     @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
            }))      
{% endhighlight  %}

{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public ActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %}  

The following output is displayed as a result of the above code example.

![ASP.NET MVC Grid Initial Grouping](Grouping_images/Grouping_img1.png)


## Initial Grouping

While initializing the grid itself, there is an option to group the column and display it in a hierarchical structure. To enable initial grouping, set array of column's `Field` name to be grouped in `GroupedColumns` property  of `GroupSettings`.

The following code example describes the above behavior.
            
{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.GroupedColumns(col => { col.Add("ShipCountry"); }); })
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
            }))      

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public ActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %}  

The following output is displayed as a result of the above code example.

![ASP.NET MVC Grid Multi-Column Grouping](Grouping_images/Grouping_img2.png)


## Multi-Column Grouping

Group multiple columns by simply drag and drop the columns one by one from column header into group drop area.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.GroupedColumns(col => { col.Add("ShipCountry"); col.Add("CustomerID"); }); })
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
            }))      

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public ActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %}  

The following output is displayed as a result of the above code example.

![ASP.NET MVC Grid Group Buttons](Grouping_images/Grouping_img3.png)


## Group Buttons

To do grouping easily without doing drag and drop column header by setting `ShowToggleButton` property of `GroupSettings` as `true`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.ShowToggleButton(true); })
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
            }))      

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public ActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %}  

The following output is displayed as a result of the above code example.

![ASP.NET MVC Grid Hide Ungroup Button](Grouping_images/Grouping_img4.png)


## Hide Ungroup Button

Hide ungroup button from grouped columns which is in the group drop area by setting the `ShowUngroupButton` property of `GroupSettings` as `false`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.ShowUngroupButton(false); })
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
            }))      

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public ActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %}  

The following output is displayed as a result of the above code example.

![ASP.NET MVC Grid Hide Grouped Column](Grouping_images/Grouping_img5.png)


## Hide Grouped Column

While grouping a particular column, there is an option to hide the grouped columns from grid. To enable hide grouped column option, set `ShowGroupedColumn` property of `GroupSettings` as `false`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.ShowGroupedColumn(false); })
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
            }))      

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public ActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %}  

The following output is displayed as a result of the above code example.

![ASP.NET MVC Grid AutoSize Drop Area](Grouping_images/Grouping_img6.png)


## AutoSize Drop Area

Drag any column header and move it to the group drop area, then its portion expands smoothly. Stop this animation by setting `EnableDropAreaAutoSizing` property of `GroupSettings` as `false`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.EnableDropAreaAutoSizing(false); })
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
            }))      

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public ActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %}  

The following output is displayed as a result of the above code example.

![ASP.NET MVC Grid Hide Drop Area](Grouping_images/Grouping_img7.png)


## Hide Drop Area 

To avoid ungrouping or further grouping of a column after an initial column grouping by setting `ShowDropArea` property of `GroupSettings` as `false`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.ShowDropArea(false).GroupedColumns(col => { col.Add("ShipCountry"); }); })
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
            }))      

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public ActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %}  

The following output is displayed as a result of the above code example.

![ASP.NET MVC Grid Group Caption Format](Grouping_images/Grouping_img8.png)


## Group Caption Format/Group Caption Template

Using `CaptionFormat` property of `GroupSettings` you can render any type of JsRender templates or customizing the group caption text. 

You can use JsRender syntax in the template.For more information about JsRender syntax, please refer [the link](https://www.jsviews.com/#jsrapi "the link").

N>  1. It's a standard way to enclose the `template` within the `script` tag with `type` as "text/x-jsrender". 
N>  2. Using locale property of `GroupCaptionFormat`, you can only customize the default group caption text.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

     @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.CaptionFormat("#template"); })
            .ClientSideEvents(eve => { eve.ActionComplete("complete"); })
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
            }))  

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public ActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
 
{% highlight js %}            
     
     <script id="template" type="text/x-jsrender">
                "{{"{{"}}:field{{}}}}-"{{"{{"}}:key{{}}}}
                  <button id="btn" class="btn">Collapse</button>
     </script>

     <script>
             function complete(args) {
                 $(".btn").ejButton({
                 click: "btnClick"
                });
             }
             function btnClick(args) {
                 var gridObj = $("#FlatGrid").data("ejGrid");
                 gridObj.expandCollapse(this.element.parent().prev());
                 $("#btn").ejButton("model.text", args.model.text == "Collapse" ? "Expand" : "Collapse");
             }
    </script>    

{% endhighlight  %}    
{% endtabs %}  

The following output is displayed as a result of the above code example.

![ASP.NET MVC Grid grouped records count in server-side](Grouping_images/Grouping_img9.png)


![ASP.NET MVC Grid server-side](Grouping_images/Grouping_img10.png)

## Handling grouped records count in server-side    

When binding remote data to grid with on-demand data loading, only current page data knowledge is available to grid and so grouped records count would be shown based on current Page only. 

This can be rectified when binding data to grid using [UrlAdaptor](https://help.syncfusion.com/aspnetmvc/grid/data-adaptors#url-adaptor) of DataManager. The grouped column values should be passed into the `groupDs` property of return object from server-side along with datasource and count.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

@(Html.EJ().Grid<OrdersView>("Grouping")

  .Datasource(datasource => datasource.URL("/Grid/UrlDataSource").Adaptor("UrlAdaptor"))
  .AllowSorting()
  .AllowGrouping()
  .GroupSettings(group => { group.GroupedColumns(col => { col.Add("EmployeeID"); }); })
  .AllowPaging()
  .Columns(col =>
{
    col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
    col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
    col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
    col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
    col.Field("OrderDate").HeaderText("Order Date").TextAlign(TextAlign.Right).Width(80).Format("{0:MM/dd/yyyy}").Add();
})
) 

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public ActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
                public ActionResult UrlDataSource(DataManager dm)
                 {
                    IEnumerable DataSource = new NorthwindDataContext().OrdersViews.ToList();
                    int count = DataSource.AsQueryable().Count();
                    IEnumerable GroupDs = new List<object>(); ;
                    DataOperations ds = new DataOperations();
                    List<string> str = new List<string>();
                    if (dm.Group != null)
                        GroupDs = ds.PerformSelect(DataSource, dm.Group); //Pass grouped column records
                    if (dm.Sorted != null)
                        DataSource = ds.PerformSorting(DataSource, dm.Sorted);
                    DataSource = ds.PerformSkip(DataSource, dm.Skip);
                    DataSource = DataSource.AsQueryable().Take(dm.Take);
                    return Json(new {result = DataSource, count =count, groupDs = GroupDs }, JsonRequestBehavior.AllowGet);
                 }  
             }     
        } 
{% endhighlight  %}   
{% endtabs %}  

The following output is displayed as a result of the above code example.

![ASP.NET MVC Grid Handling grouped records](Grouping_images/Grouping_img11.png)







