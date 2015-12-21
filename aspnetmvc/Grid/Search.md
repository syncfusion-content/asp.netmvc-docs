---
layout: post
title: Searching with Grid widget for Syncfusion Essential MVC
description: How to enable search opition and its functionalities
platform: ejmvc
control: Grid
documentation: ug
--- 
# Searching

The grid has an option to search its content using the JavaScript method [`search`](http://help.syncfusion.com/js/api/ejgrid#methods:search "search") with search key as parameter. Also, it provides an option to integrate Search text box in grid toolbar, by adding `search` toolbar item in [`toolbarSetting.toolbarItems`](http://help.syncfusion.com/js/api/ejgrid#members:toolbarsettings-toolbaritems "toolbarSetting.toolbarItems") property.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight CSHTML %}

	  @(Html.EJ().Grid<OrdersView>("Searching")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .ToolbarSettings(toolbar => { toolbar.ShowToolbar().ToolbarItems(items => { items.AddTool(ToolBarItems.Search); }); })
            .AllowSearching()           
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();   
			    col.Field("CustomerID").HeaderText("Customer ID").Add();
		        col.Field("ShipCountry").HeaderText("Ship Country").Add(); 
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();    
            })
		)

{% endhighlight  %}
{% highlight C# %}
		
		 namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public ActionResult Searching()
             {
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
              }
          }
       }

{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example.

![](Searching_images/searching_img1.png)


## Initial Searching

While initializing the grid, there is an option to display only the searched data in grid. To perform initial searching, define `fields`, `operator`, `key` and `ignoreCase` in `searchSettings` property.

 N> `key` value must be passed as `string`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight CSHTML %}

	  @(Html.EJ().Grid<OrdersView>("Selection")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .ToolbarSettings(toolbar => { toolbar.ShowToolbar().ToolbarItems(items => { items.AddTool(ToolBarItems.Search); }); })
            .AllowSearching()  
			.SearchSettings(col => { col.Fields(search => { search.Add("CustomerID"); }).Operator(Operator.Contains).Key("ra").IgnoreCase(false); })         
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();   
			    col.Field("CustomerID").HeaderText("Customer ID").Add();
		        col.Field("ShipCountry").HeaderText("Ship Country").Add(); 
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();    
            })
		)

{% endhighlight  %}
{% highlight C# %}
		
		 namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public ActionResult Selection()
             {
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
              }
          }
       }

{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example.

![](Searching_images/searching_img2.png)


List of supported operators in searching.

<table colspan="1">
 <tr>
<td>
ej.FilterOperators.equal</td></tr>
<tr>
<td>
ej.FilterOperators.notEqual</td></tr>
<tr>
<td>
ej.FilterOperators.startsWith</td></tr>
<tr>
<td>
ej.FilterOperators.endsWith</td></tr>
<tr>
<td>
ej.FilterOperators.contains</td></tr>
</table>
