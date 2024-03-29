---
layout: post
title: scrolling with Grid widget for Syncfusion Essential MVC
description: This section explains about the scrolling and its functionalities like Frozen Rows and Columns, Touch Scroll, Virtual Scroll and the types of Virtual Scroll.
platform: ejmvc
control: Grid
documentation: ug
---
# Enable Scrolling in ASP.NET MVC Grid

Scrolling can be enabled by setting the `AllowScrolling` as `true`. The height and width can be set to grid by using the properties  `Height` and `Width` property of the `ScrollSettings`. 

 N> If `Width`  and `Height`  is not defined in the `ScrollSettings`  property then the horizontal and vertical scrollbar is enabled, only when the grid width exceeds the browser width.

The height and width can be set in percentage and pixel. The default value for `Height`  and `Width`  in `ScrollSettings`  is 0 and `auto` respectively.

The following code example describes the previous behavior.

{% tabs %} 
{% highlight razor %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(400).Height(300); })             
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add()
                col.Field("ShipAddress").Add();
                col.Field("ShipPostalCode").Add();
                col.Field("Freight").Format("{0:C}").Add();    
            })
      	)
{% endhighlight  %}
{% highlight c# %}
		
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

The following output is displayed as a result of the previous code example.

![Scrolling](Scrolling_images/Scrolling_img1.png)

## Set width and height in pixel 

To specify the `Width` and `Height` property of  `ScrollSettings` in pixel, by set the pixel value as integer. 

The following code example describes the previous behavior.

{% tabs %} 
{% highlight razor %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(500).Height(300); })             
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add();
                col.Field("ShipAddress").Add();
                col.Field("ShipPostalCode").Add();
                col.Field("Freight").Format("{0:C}").Add();    
            })
      	)
{% endhighlight  %}
{% highlight c# %}
		
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

The following output is displayed as a result of the previous code example.

![In pixel](scrolling_images/scrolling_img2.png)

## Set width and height in percentage

To specify the `Width` and `Height` property of  `ScrollSettings`  in percentage, by set the percentage value as string.

The following code example describes the previous behavior.

{% tabs %} 
{% highlight razor %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width("70%").Height("5%"); })             
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add();
                col.Field("ShipAddress").Add();
                col.Field("ShipPostalCode").Add();
                col.Field("Freight").Format("{0:C}").Add();    
            })
      	)
{% endhighlight  %}
{% highlight c# %}
		
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

The following output is displayed as a result of the previous code example.

![In percentage](scrolling_images/scrolling_img3.png)

## Set width as auto

Specify the `Width`  property of `ScrollSettings`  as auto, then the scrollbar is rendered only when the grid width exceeds the browser window width.

The following code example describes the previous behavior.

{% tabs %} 
{% highlight razor %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width("auto").Height(300); })            
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add();
                col.Field("ShipAddress").Add();
                col.Field("ShipPostalCode").Add();
                col.Field("Freight").Format("{0:C}").Add();    
            })
       	)
{% endhighlight  %}
{% highlight c# %}
		
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

The following output is displayed as a result of the previous code example.

![Auto Width](scrolling_images/scrolling_img4.png)

## Frozen columns

Specify the `FrozenColumns`  property of `ScrollSettings`  to freeze the columns(upto the specified frozenColumns value) at the time of scrolling. Horizontal scrollbar must be enabling while specifying the `FrozenColumns`  then only you can scroll and see the remaining columns with freeze pane.

N> The `AllowScrolling`  must be `true` while specifying `FrozenColumns` .

The following code example describes the previous behavior.

{% tabs %} 
{% highlight razor %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(300).FrozenColumns(2); })             
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add();
                col.Field("ShipAddress").Add();
                col.Field("ShipPostalCode").Add();
                col.Field("Freight").Format("{0:C}").Add();    
            })
        )
{% endhighlight  %}
{% highlight c# %}
		
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

The following output is displayed as a result of the previous code example.

![Frozen Columns](scrolling_images/scrolling_img5.png)


### Freeze particular columns:

To freeze selected columns in grid at the time of scrolling, by setting the `IsFrozen`  property of columns as `true`. The `IsFrozen`  columns are rendered first in the grid even the columns index is different while declaring the `Columns` .

The following code example describes the previous behavior.

{% tabs %} 
{% highlight razor %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(400); })              
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("Freight").Format("{0:C}").IsFrozen(true).Add(); 
                col.Field("OrderDate").Format("{0:dd/MM/yyyy}").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Width(100).IsFrozen(true).Add();
                col.Field("ShipAddress").Add();
                col.Field("ShipPostalCode").Add();         
            })
       	)
{% endhighlight  %}
{% highlight c# %}
		
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

The following output is displayed as a result of the previous code example.

![Frozen Column](scrolling_images/scrolling_img6.png)


### Frozen columns alert messages:

1. If the `AllowScrolling`  is false while using `FrozenColumns`  then "Enable `AllowScrolling`  while using frozen Columns" alert message is thrown.
2. If the `FrozenColumns`  is specified out of the grid column view then "Frozen columns should be in grid view area" alert message is thrown.
3. Frozen Rows and Columns are not supported in the following features.
 Grouping
 Row Template
 Detail Template
 Hierarchy Grid 
 Batch Editing
 Virtual Scrolling

If any one of the previous feature is enabled along with Frozen rows and columns, then the "Frozen Columns and Rows are not supported for Grouping, Row Template, Detail Template, Hierarchy Grid and Batch Editing" alert message is thrown.

## Frozen rows

Specify the `FrozenRows`  property of `ScrollSettings`  to freeze rows(upto the specified FrozenRows value) at the time of scrolling. Vertical scrollbar must be enabling while specifying the `FrozenRows` then only you can scroll and see the remaining rows with freeze pane.

N> The `AllowScrolling`  must be `true` while specifying `FrozenRows` .

The following code example describes the previous behavior.

{% tabs %} 
{% highlight razor %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(300).FrozenRows(4); })             
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();   
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add();
                col.Field("ShipAddress").Add();
                col.Field("ShipPostalCode").Add();
                col.Field("Freight").Format("{0:C}").Add();    
            })
       	)
{% endhighlight  %}
{% highlight c# %}
		
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

The following output is displayed as a result of the previous code example.

![Frozen Rows](scrolling_images/scrolling_img7.png)


## Touch scroll

In touch  supported devices you can scroll and show the content by swipe left, right, top and bottom. Disable touch scroll by setting the `EnableTouchScroll`  property of `ScrollSettings`  as `false`.

The following code example describes the previous behavior.

{% tabs %} 
{% highlight razor %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(300).EnableTouchScroll(false); })             
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add();
                col.Field("ShipAddress").Add();
                col.Field("ShipPostalCode").Add();
                col.Field("Freight").Format("{0:C}").Add();    
            })
       	)
{% endhighlight  %}
{% highlight c# %}
		
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

## Virtual scrolling

The virtual scrolling support allows you to load data that you require (load data based on page size) without buffering the entire huge database. To enable virtual scrolling by setting the `AllowVirtualScrolling` property of `ScrollSettings` as `true`. 

We also have an enhanced virtual scrolling feature with an improvised virtual scrolling performance. To enable improvised virtual scrolling feature by setting `EnableVirtualization` property of `ScrollSettings` as true and it doesn't requires `AllowVirtualScrolling` to enabled. It allows you to load the grid with data while scrolling. In order to enable this, you need to enable `EnableVirtualization` property of the `ScrollSettings`. Some of the relevant functionalities of this are,

1.	White space will not be appeared in the grid. 
2.	Improved page rendering performance. 
3.  It can render nearly 500 thousand records.

It supports two mode of virtualization. They are:

1. Normal Mode
2. Infinite or Continuous Mode

N> Enhanced Virtual Scrolling supports only normal mode
N> The following features are not supported by virtual scrolling 
N> 1. Grouping
N> 2. Frozen Rows 
N> 3. Cell merging 
N> 4. Detail template 
N> 5. Hierarchy
N> 6. Editing

### Normal mode:

It allows you to load the grid with data while scrolling. This can be achieved by setting the `VirtualScrollMode`  as `Normal`.

The following code example describes the previous behavior.

{% tabs %} 
{% highlight razor %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(300).AllowVirtualScrolling(true).VirtualScrollMode(VirtualScrollMode.Normal); })             
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add();
                col.Field("ShipAddress").Add();
                col.Field("ShipPostalCode").Add();
                col.Field("Freight").Format("{0:C}").Add();    
            })
       	)
{% endhighlight  %}
{% highlight c# %}
		
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

The following output is displayed as a result of the previous code example.

![Normal Mode](scrolling_images/scrolling_img8.png)

#### Enhanced virtual scrolling:

In order to enable this, you need to set the `EnableVirtualization` property of the `ScrollSettings` as true. 

The following code example describes the previous behavior.

{% tabs %} 
{% highlight razor %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(300).EnableVirtualization(true); })             
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add();
                col.Field("ShipAddress").Add();
                col.Field("ShipPostalCode").Add();
                col.Field("Freight").Format("{0:C}").Add();    
            })
       	)
{% endhighlight  %}
{% highlight c# %}
		
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

The following output is displayed as a result of the previous code example.

![Virtual Scroll](scrolling_images/scrolling_img10.png)

### Infinite or Continuous mode:

In Infinite or Continuous mode, the data is loaded in grid when the scrollbar reaches the end.  You can enable the continuous mode by setting the `VirtualScrollMode`  property as `Continuous`.

The following code example describes the previous behavior.

{% tabs %} 
{% highlight razor %}

	  @(Html.EJ().Grid<OrdersView>("Scrolling")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowScrolling()
            .ScrollSettings(col => { col.Width(550).Height(300).AllowVirtualScrolling(true).VirtualScrollMode(VirtualScrollMode.Continuous); })             
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add();
                col.Field("ShipAddress").Add();
                col.Field("ShipPostalCode").Add();
                col.Field("Freight").Format("{0:C}").Add();    
            })
       	)
{% endhighlight  %}
{% highlight c# %}
		
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

The following output is displayed as a result of the previous code example.

 ![Infinite Mode](scrolling_images/scrolling_img9.png)
