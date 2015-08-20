---
layout: post
title: Context-Menu
description: context menu
platform: ejmvc
control: Grid
documentation: ug
---

# Context Menu

Context Menu is one of the user interaction controls related with Grid. It is handy to use the Context Menu to trigger more actions. The default Context Menu items created for Grid are:

1. Header
1. Sort In Ascending Order
2. Sort In Descending Order
3. Grouping
4. UnGrouping
2. Content
1. Add Record
2. Edit Record
3. Delete Record                  
3. Footer 
1. Next Page     
2. Last Page
3. Previous Page
4. First Page

## Context Menu action


To enable Context Menu in Grid use EnableContextMenu property in ContextMenuSettings at Grid initialize. The following code example illustrates you on how to set Context Menu.


{% highlight js %}


  @(Html.EJ().Grid<object>("Grid")

      .Datasource((IEnumerable<object>)ViewBag.datasource)

      .AllowSorting()

      .AllowPaging()

      .AllowGrouping()

      .EditSettings(edit => {

       edit.AllowAdding().AllowEditing().AllowDeleting()

        })

      .ContextMenuSettings(contextMenu =>

         {

contextMenu.EnableContextMenu();    

         })

       .Columns(col =>

        	{

            	col.Field("OrderID").HeaderText("Order ID") TextAlign(TextAlign.Right).Add();

            	col.Field("CustomerID").HeaderText("Employee ID").Add();

            	col.Field("EmployeeID").HeaderText("Freight"). TextAlign(TextAlign.Right).Add();

            	col.Field("ShipCity").HeaderText("Ship City").Add();

        	}))



{% endhighlight  %}
{% highlight c# %}

namespace SyncfusionMvcApplication3.Controllers

{

    public class HomeController : Controller

    {

        public ActionResult ContextMenu()

        {

            ViewBag.datasource = new NorthwindDataContext.Orders.ToList();

            return View();

        }         

    }	

}


{% endhighlight  %}


The following output is displayed as a result of the above code example.

Content

![](Context-Menu_images/Context-Menu_img1.png)

_Figure131: Context Menu in content_

Header

![](Context-Menu_images/Context-Menu_img2.png)

_Figure112: Context Menu in Header_

Footer

![](Context-Menu_images/Context-Menu_img3.png)

_Figure113: Context Menu in Footer_

