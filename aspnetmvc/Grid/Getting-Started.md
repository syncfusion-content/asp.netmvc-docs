---
layout: post
title: Getting started with Grid widget for Syncfusion Essential ASP.NET MVC
description: How to create the Grid, data bind, enable paging, grouping, filtering and add summaries
platform: ejmvc
control: Grid
documentation: ug
---

# Getting Started

This section explains briefly about how to create a Grid in your application with ASP.NET MVC, and also explains about how to enable basic grid operations like paging, filtering, grouping and summary. The following screenshot illustrates the grid control.

![](Getting-Started_images/Getting-Started_img.png)

## Create your first grid in MVC

The following steps explain creating first grid with an empty datasource:

1.  Create Syncfusion ASP.NET MVC application. You can refer to [MVC Getting Started documentation](http://help.syncfusion.com/aspnetmvc/getting-started) to create a new project and add necessary dll’s and script files.
2.  Add a grid control in view file with an empty datasource as like as follows. In `Columns` definition, the `TextAlign` property allows you to align text of the columns, the `Width` property is used to define width of the columns and `Format` property allows you to format the particular columns value.

{% highlight razor %}
	
    @(Html.EJ().Grid<object>("FlatGrid")

	.Columns(col =>

	{

        col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Width(75).Add();

		col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();

		col.Field("ShipName").HeaderText("Ship Name").Width(100).Add();

		col.Field("ShipCity").HeaderText("Ship City").Width(100).Add();

		col.Field("Freight").Format("{0:c3}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();
	})
    )
		 
{% endhighlight  %}
   
You can execute the above code sample to render an empty grid is rendered with specified column headers.

![](Getting-Started_images/Getting-Started_img2.png)

## Data binding

You can bind the data to grid control using the `DataSource` property.

{% highlight razor %}


    @(Html.EJ().Grid<object>("FlatGrid")

    .Datasource((IEnumerable<object>)ViewBag.datasource)
    
    .Columns(col =>

    {

	   col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Width(75).Add();

	   col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();

	   col.Field("ShipName").HeaderText("Ship Name").Width(100).Add();

	   col.Field("ShipCity").HeaderText("Ship City").Width(100).Add();

	   col.Field("Freight").Format("{0:c3}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();

    })

    )

{% endhighlight  %}

{% highlight c# %} 
        
          namespace MVCSampleBrowser.Controllers
           {
            public class GridController : Controller
              { 
               public ActionResult Paging()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.datasource = DataSource;
                   return View();
                 }
              }   
            } 

{% endhighlight  %}

![](Getting-Started_images/Getting-Started_img3.png)


## Enable paging

The [`Paging`](http://help.syncfusion.com/aspnetmvc/grid/paging) feature can be enabled by the `AllowPaging` property of grid control. This adds the pager in the bottom of the grid, using that pager you can display the grid records in paged view. The page size can be customized using the `PageSize`
and `PageSettings` property.

{% highlight razor %}

    @(Html.EJ().Grid<object>("FlatGrid")

    .Datasource((IEnumerable<object>)ViewBag.datasource)
    
    .AllowPaging()

    .Columns(col =>

    {

        col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Width(75).Add();

        col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();

        col.Field("ShipName").HeaderText("Ship Name").Width(100).Add();

         col.Field("ShipCity").HeaderText("Ship City").Width(100).Add();      col.Field("Freight").Format("{0:c3}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();
    })
    )

{% endhighlight  %}

{% highlight c# %} 
        
          namespace MVCSampleBrowser.Controllers
           {
            public class GridController : Controller
              { 
               public ActionResult Paging()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.datasource = DataSource;
                   return View();
                 }
              }   
            } 

{% endhighlight  %}

    N> _Pager settings can be customized by using the 'PageSize' and 'PageCount' properties. When it is not given the default values for `PageSize` and `PageCount` are 12 and 8 respectively._

![](Getting-Started_images/Getting-Started_img4.png)

## Enable filtering

The [`Filtering`](http://help.syncfusion.com/aspnetmvc/grid/filtering) feature in the grid is used to facilitate the extraction of a subset of records that meets certain criteria. You can apply Filter to one or more columns. Filtering feature can be enabled by the AllowFiltering property. By default, the filter bar row is displayed to perform filtering, you can change the filter type by using the `FilterType` property of FilterSettings.


{% highlight razor %}


    @(Html.EJ().Grid<object>("FlatGrid")
    
    .Datasource((IEnumerable<object>)ViewBag.datasource)

    .AllowPaging()

    .AllowFiltering()

    .FilterSettings(d => d.FilterType(FilterType.FilterBar))

    .Columns(col =>

    {	

        col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Width(75).Add();

        col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();

        col.Field("ShipName").HeaderText("Ship Name").Width(100).Add();

        col.Field("ShipCity").HeaderText("Ship City").Width(100).Add();      

        col.Field("Freight").Format("{0:c3}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();

    })

    )

{% endhighlight  %}

{% highlight c# %} 
        
          namespace MVCSampleBrowser.Controllers
           {
            public class GridController : Controller
              { 
               public ActionResult Paging()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.datasource = DataSource;
                   return View();
                 }
              }   
            } 

{% endhighlight  %}

![](Getting-Started_images/Getting-Started_img7.png)


## Enable grouping

The ['Grouping'](http://help.syncfusion.com/aspnetmvc/grid/grouping) feature in the grid is used to consolidate grid data into groups. Grouping allows the categorization of records based on specified columns. You can enable grouping feature by the `AllowGrouping` property. Columns can be grouped dynamically by drag and drop of the grid column header to the group drop area. The initial grouping can be done by adding required column names in the `GroupedColumns` property of `GroupSettings` property.

{% highlight razor %}

    @(Html.EJ().Grid<object>("FlatGrid")

    .Datasource((IEnumerable<object>)ViewBag.datasource)
    
    .AllowPaging()

    .AllowGrouping()

    .GroupSettings(group => group.GroupedColumns(col=>col.Add("ShipName") ))

    .AllowFiltering()

    .FilterSettings(d => d.FilterType(FilterType.FilterBar))

    .Columns(col =>

    {

        col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Width(75).Add();

        col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();

        col.Field("ShipName").HeaderText("Ship Name").Width(100).Add();

        col.Field("ShipCity").HeaderText("Ship City").Width(100).Add();    col.Field("Freight").Format("{0:c3}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();

    })

    )

{% endhighlight  %}

{% highlight c# %} 
        
          namespace MVCSampleBrowser.Controllers
           {
            public class GridController : Controller
              { 
               public ActionResult Paging()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.datasource = DataSource;
                   return View();
                 }
              }   
            } 

{% endhighlight  %}


![](Getting-Started_images/Getting-Started_img8.png)


## Add summaries

The [`Summaries`](http://help.syncfusion.com/aspnetmvc/grid/summary) can be enabled by setting the `ShowSummary` to true and adding required summary rows and columns in the `SummaryRows` property. 

The following code example shows the option to enable group summary.

{% highlight razor %}


    @(Html.EJ().Grid<object>("FlatGrid")

    .Datasource((IEnumerable<object>)ViewBag.datasource)

    .AllowPaging()

    .AllowGrouping()

    .ShowSummary()

    .GroupSettings(group => group.GroupedColumns(col=>col.Add("ShipName") ))

    .AllowFiltering()

    .FilterSettings(d => d.FilterType(FilterType.FilterBar))

    .SummaryRow(row =>

    {

        row.ShowTotalSummary(false)

           .SummaryColumns(col =>

           {

                col.SummaryType(SummaryType.Sum)

                .DisplayColumn("Freight")

                .DataMember("Freight")

                .Prefix("Sum = ")

                .Format("{0:c3}")

                .Add();

           }).Add();

    })

    .Columns(col =>

    {

         col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Width(75).Add();

         col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();

         col.Field("ShipName").HeaderText("Ship Name").Width(100).Add();

         col.Field("ShipCity").HeaderText("Ship City").Width(100).Add();
                        
         col.Field("Freight").Format("{0:c3}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();

    })

    )

{% endhighlight  %}

{% highlight c# %} 
        
          namespace MVCSampleBrowser.Controllers
           {
            public class GridController : Controller
              { 
               public ActionResult Paging()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.datasource = DataSource;
                   return View();
                 }
              }   
            } 

{% endhighlight  %}

![](Getting-Started_images/Getting-Started_img9.png)

