---
layout: post
title: Scrolling | Grid | ASP.NET MVC | Syncfusion
description: scrolling
platform: ejmvc
control: Grid
documentation: ug
---
# Scrolling

Scrolling can be enabled by setting [`allowScrolling`](http://help.syncfusion.com/js/api/ejgrid#members:allowscrolling "allowScrolling") as `true`. The height and width can be set to grid by using the properties [`scrollSettings.height`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-height "scrollSettings.height") and [`scrollSettings.width`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-width "scrollSettings.width") respectively. 

   N> If [`width`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-width "width") and [`height`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-height "height") is not defined in the [`scrollSettings`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings "scrollSettings") property then the horizontal and vertical scrollbar is enabled, only when the grid width exceeds the browser width.

The height and width can be set in percentage and pixel. The default value for [`height`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-height "height") and [`width`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-width "width") in [`scrollSettings`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings "scrollSettings") is 0 and `auto` respectively.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight CSHTML %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(400).Height(300); })             
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
			    col.Field("ShipCity").HeaderText("Ship City").Add();
		        col.Field("ShipCountry").HeaderText("Ship Country").Add()
                col.Field("ShipAddress").HeaderText("Ship Country").Add();
		        col.Field("ShipPostalCode").HeaderText("ShipPostalCode").Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();    
            })
		)

{% endhighlight  %}
{% highlight C# %}
		
		 namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public ActionResult Scrolling()
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

![](Scrolling_images/Scrolling_img1.png)

## Set width and height in pixel 

To specify the [`scrollSettings.width`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-width "scrollSettings.width") and [`scrollSettings.height`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-height "scrollSettings.height") in pixel, by set the pixel value as integer. 

The following code example describes the above behavior.

{% tabs %}
 
{% highlight CSHTML %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(500).Height(300); })             
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
			    col.Field("ShipCity").HeaderText("Ship City").Add();
		        col.Field("ShipCountry").HeaderText("Ship Country").Add();
			    col.Field("ShipAddress").HeaderText("Ship Country").Add();
			    col.Field("ShipPostalCode").HeaderText("ShipPostalCode").Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();    
            })
		)

{% endhighlight  %}
{% highlight C# %}
		
		 namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public ActionResult Scrolling()
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

![](scrolling_images/scrolling_img2.png)

## Set width and height in percentage

To specify the [`scrollSettings.width`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-width "scrollSettings.width") and [`scrollSettings.height`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-height "scrollSettings.height") in percentage, by set the percentage value as string.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight CSHTML %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width("70%").Height("5%"); })             
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
			    col.Field("ShipCity").HeaderText("Ship City").Add();
			    col.Field("ShipCountry").HeaderText("Ship Country").Add();
			    col.Field("ShipAddress").HeaderText("Ship Country").Add();
			    col.Field("ShipPostalCode").HeaderText("ShipPostalCode").Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();    
            })
		)

{% endhighlight  %}
{% highlight C# %}
		
		 namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public ActionResult Scrolling()
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

![](scrolling_images/scrolling_img3.png)

## Set width as auto

Specify [`width`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-width "width") property of [`scrollSettings`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings "scrollSettings") as auto, then the scrollbar is rendered only when the grid width exceeds the browser window width.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight CSHTML %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width("auto").Height(300); })            
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
			    col.Field("ShipCity").HeaderText("Ship City").Add();
			    col.Field("ShipCountry").HeaderText("Ship Country").Add();
			    col.Field("ShipAddress").HeaderText("Ship Country").Add();
		        col.Field("ShipPostalCode").HeaderText("ShipPostalCode").Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();    
            })
		)

{% endhighlight  %}
{% highlight C# %}
		
		 namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public ActionResult Scrolling()
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

![](scrolling_images/scrolling_img4.png)

## Frozen columns

Specify [`frozenColumns`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-frozencolumns "frozenColumns") property of [`scrollSettings`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings "scrollSettings") to freeze the columns(upto the specified frozenColumns value) at the time of scrolling. Horizontal scrollbar must be enabling while specifying [`frozenColumns`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-frozencolumns "frozenColumns") then only you can scroll and see the remaining columns with freeze pane.

N> [`allowScrolling`](http://help.syncfusion.com/js/api/ejgrid#members:allowscrolling "allowScrolling") must be `true` while specifying [`frozenColumns`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-frozencolumns "frozenColumns").

The following code example describes the above behavior.

{% tabs %}
 
{% highlight CSHTML %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(300).FrozenColumns(2); })             
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
				col.Field("ShipCity").HeaderText("Ship City").Add();
				col.Field("ShipCountry").HeaderText("Ship Country").Add();
			    col.Field("ShipAddress").HeaderText("Ship Country").Add();
			    col.Field("ShipPostalCode").HeaderText("ShipPostalCode").Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();    
            })
		)

{% endhighlight  %}
{% highlight C# %}
		
		 namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public ActionResult Scrolling()
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

![](scrolling_images/scrolling_img5.png)


### Freeze particular columns:

To freeze selected columns in grid at the time of scrolling, by set [`isFrozen`](http://help.syncfusion.com/js/api/ejgrid#members:columns-isfrozen "isFrozen") property of columns as `true`. [`isFrozen`](http://help.syncfusion.com/js/api/ejgrid#members:columns-isfrozen "isFrozen") columns are rendered first in the grid even the columns index is different while declaring the [`columns`](http://help.syncfusion.com/js/api/ejgrid#members:columns "columns").

The following code example describes the above behavior.

{% tabs %}
 
{% highlight CSHTML %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(400); })              
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
				col.Field("Freight").HeaderText("Freight").Format("{0:C}").IsFrozen(true).Add(); 
				col.Field("OrderDate").HeaderText("Order Date").Format("{0:dd/MM/yyyy}").Add();
				col.Field("ShipCity").HeaderText("Ship City").Add();
			    col.Field("ShipCountry").HeaderText("Ship Country").Width(100).IsFrozen(true).Add();
			    col.Field("ShipAddress").HeaderText("Ship Country").Add();
			    col.Field("ShipPostalCode").HeaderText("ShipPostalCode").Add();         
            })
		)

{% endhighlight  %}
{% highlight C# %}
		
		 namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public ActionResult Scrolling()
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

![](scrolling_images/scrolling_img6.png)


### Frozen Columns alert Messages:

1. If [`allowScrolling`](http://help.syncfusion.com/js/api/ejgrid#members:allowscrolling "allowScrolling") is false while using [`frozenColumns`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-frozencolumns "frozenColumns") then "Enable [`allowScrolling`](http://help.syncfusion.com/js/api/ejgrid#members:allowscrolling "allowScrolling") while using frozen Columns" alert message is thrown.
2. If [`frozenColumns`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-frozencolumns "frozenColumns") is specified out of the grid column view then "Frozen columns should be in grid view area" alert message is thrown.
3. Frozen Rows and Columns are not supported the following features
 Grouping
 Row Template
 Detail Template
 Hierarchy Grid 
 Batch Editing

If any one of the above feature is enabled along with Frozen Rows and Columns, then "Frozen Columns and Rows are not supported for Grouping, Row Template, Detail Template, Hierarchy Grid and Batch Editing" alert message is thrown.

## Frozen Rows

Specify [`frozenRows`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-frozenrows "frozenRows") property of [`scrollSettings`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings "scrollSettings") to freeze rows(upto the specified frozenRows value) at the time of scrolling. Vertical scrollbar must be enabling while specifying [`frozenRows`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-frozenrows "frozenRows") then only you can scroll and see the remaining rows with freeze pane.

N> [`allowScrolling`](http://help.syncfusion.com/js/api/ejgrid#members:allowscrolling "allowScrolling") must be `true` while specifying [`frozenRows`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-frozenrows "frozenRows").

The following code example describes the above behavior.

{% tabs %}
 
{% highlight CSHTML %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(300).FrozenRows(4); })             
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
				col.Field("ShipCity").HeaderText("Ship City").Add();
				col.Field("ShipCountry").HeaderText("Ship Country").Add();
				col.Field("ShipAddress").HeaderText("Ship Country").Add();
			    col.Field("ShipPostalCode").HeaderText("ShipPostalCode").Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();    
            })
		)

{% endhighlight  %}
{% highlight C# %}
		
		 namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public ActionResult Scrolling()
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

![](scrolling_images/scrolling_img7.png)


## Touch scroll

In [touch](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-enabletouchscroll "touch") supported devices you can scroll and show the content by swipe left, right, top and bottom. Disable touch scroll by setting [`enableTouchScroll`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-enabletouchscroll "enableTouchScroll") property of [`scrollSettings`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings "scrollSettings") as `false`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight CSHTML %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(300).EnableTouchScroll(false); })             
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
			    col.Field("ShipCity").HeaderText("Ship City").Add();
		        col.Field("ShipCountry").HeaderText("Ship Country").Add();
			    col.Field("ShipAddress").HeaderText("Ship Country").Add();
			    col.Field("ShipPostalCode").HeaderText("ShipPostalCode").Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();    
            })
		)

{% endhighlight  %}
{% highlight C# %}
		
		 namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public ActionResult Scrolling()
             {
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
              }
          }
       }

{% endhighlight  %}
{% endtabs %} 

## Virtual Scrolling

The virtual scrolling support allows you to load data that you require (load data based on page size) without buffering the entire huge database. To enable virtual scrolling by setting [`allowVirtulScrolling`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-allowvirtualscrolling "allowVirtulScrolling") property of [`scrollSettings`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings "scrollSettings") as `true`. It supports two mode of virtualization. They are,

1. Normal Mode
2. Continuous Mode
    
N> The following features are not supported by virtual scrolling 
N> 1. Grouping
N> 2. Frozen Rows 
N> 3. Cell merging 
N> 4. Detail template 
N> 5. Row template 
N> 6. Hierarchy

### Normal Mode:

It allows you to load the grid with data while scrolling. This can be achieved by setting [`virtualScrollMode`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-virtualscrollmode "virtualScrollMode") as `normal`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight CSHTML %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(300).AllowVirtualScrolling(true).VirtualScrollMode(VirtualScrollMode.Normal); })             
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
			    col.Field("ShipCity").HeaderText("Ship City").Add();
		        col.Field("ShipCountry").HeaderText("Ship Country").Add();
			    col.Field("ShipAddress").HeaderText("Ship Country").Add();
			    col.Field("ShipPostalCode").HeaderText("ShipPostalCode").Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();    
            })
		)

{% endhighlight  %}
{% highlight C# %}
		
		 namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public ActionResult Scrolling()
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

![](scrolling_images/scrolling_img8.png)


### Continuous Mode:

In Continuous mode, the data is loaded in grid when the scrollbar reaches the end.  You can enable the continuous mode by setting the [`virtualScrollMode`](http://help.syncfusion.com/js/api/ejgrid#members:scrollsettings-virtualscrollmode "virtualScrollMode") property as `continuous`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight CSHTML %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(300).AllowVirtualScrolling(true).VirtualScrollMode(VirtualScrollMode.Continuous); })             
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
			    col.Field("ShipCity").HeaderText("Ship City").Add();
		        col.Field("ShipCountry").HeaderText("Ship Country").Add();
			    col.Field("ShipAddress").HeaderText("Ship Country").Add();
			    col.Field("ShipPostalCode").HeaderText("ShipPostalCode").Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();    
            })
		)

{% endhighlight  %}
{% highlight C# %}
		
		 namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public ActionResult Scrolling()
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

 ![](images/scrolling_img9.PNG)





 