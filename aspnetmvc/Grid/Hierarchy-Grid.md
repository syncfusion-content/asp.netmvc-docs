---
layout: post
title: Hierarchical binding | Grid | ASP.NET MVC | Syncfusion
description: How to bind the hierarchical data
platform: ejmvc
control: Grid
documentation: ug
---

# Hierarchical Bindings

Hierarchical binding can be used to create the Grid with parent and child relation, this facilitate you to view the child records for a particular row by clicking on the Expander button present in first column of each grid row. This can be enabled by defining `ChildGrid` and `QueryString`.

The `ChildGrid` property is used to define the model properties that has to be applied on the child grid. The `ChildGrid` is the extended class of the base class grid such that it holds all the properties of the grid. The `QueryString` is a property that has to be specified within the ChildGrid, which defines the relation between the parent and child grid. The `QueryString` property is used to denote the primaryKey field of the parent grid which is to be mapped with the foreignKey field of the child grid. Based on the mapping, the child grid records are filtered from the table and is bound as datasource for the child grid.

If the foreign key column name differs for parent and child grid then use `ForeignKeyField` property of child grid. Refer [here](https://help.syncfusion.com/aspnetmvc/grid/how-to#hierarchy-grid-with-different-foreignkeyfield-in-parent-and-child-table "here") for more information.

N> The responsive and exporting support is not applicable for Hierarchical binding. 

{% tabs %}

{% highlight razor %}

@(Html.EJ().Grid<EmployeeView>("HierarchyGrid")
        .Datasource((IEnumerable<object>)ViewBag.datasource)
        .Columns(col =>
        {
            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(85).Add();
            col.Field("FirstName").HeaderText("First Name").Width(100).Add();
            col.Field("Title").Width(120).Add();
            col.Field("City").Width(100).Add();
            col.Field("Country").Width(100).Add();
        })
                 .ChildGrid(child =>
                 {
                     child.Datasource("http://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders")
                        .QueryString("EmployeeID")
                        .AllowPaging()
                        .PageSettings(page => page.PageSize(5))
                        .Columns(col =>
                        {
                            col.Field("OrderID").HeaderText("OrderID").TextAlign(TextAlign.Right).Width(75).Add();
                            col.Field("ShipCity").HeaderText("ShipCity").Width(100).Add();
                            col.Field("Freight").Width(120).Add();
                            col.Field("ShipName").Width(100).Add();
                        });
                 })

)

{% endhighlight  %}
{% highlight c# %}

public partial class GridController : Controller

{

	//

	// GET: /HierarchyGrid/

	 public ActionResult HierarchyGrid()

        {

            var DataSource = new NorthwindDataContext().EmployeeViews.ToList();

            ViewBag.datasource = DataSource;

            return View();

        }

}


{% endhighlight  %}

{% endtabs %} 

![](Hierarchy-Grid_images/HierarchyGrid_img1.png)


## Expand or collapse all child's

The grid can able to expand and collapse all the `ChildGrid` through programmatically using the [`expandAll`](http://help.syncfusion.com/js/api/ejgrid#methods:expandall "expandAll") and [`collapseAll`](http://help.syncfusion.com/js/api/ejgrid#methods:collapseall "collapseAll") method.

{% tabs %}

{% highlight razor %}

<button id="expand">expandAll</button>
<button id="collapse">collapseAll</button>

 @(Html.EJ().Grid<EmployeeView>("HierarchyGrid")
        .Datasource((IEnumerable<object>)ViewBag.datasource)
        .ChildGrid(child =>
        {
            child.Datasource((IEnumerable<object>)ViewBag.datasource2)
               .QueryString("EmployeeID")
               .AllowPaging()
               .PageSettings(page => page.PageSize(5))
               .Columns(col =>
               {
                   col.Field("OrderID").HeaderText("OrderID").TextAlign(TextAlign.Right).Width(75).Add();
                   col.Field("ShipCity").HeaderText("ShipCity").Width(100).Add();
                   col.Field("Freight").Width(120).Add();
                   col.Field("ShipName").Width(100).Add();
               });
        })

)

<script type="text/javascript">
   
    $("#expand,#collapse").ejButton({
        showRoundedCorner: true,
        size: "mini",
        width: 150,
        click: function (args) {
            $("#HierarchyGrid").ejGrid(args.model.text); //invokes expandAll & collapseAll method based on button name
        }
    });
</script>

{% endhighlight  %}
{% highlight c# %}

public partial class GridController : Controller

{

	//

	// GET: /HierarchyGrid/

	 public ActionResult HierarchyGrid()

        {

            var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
            
            var DataSource2 = new NorthwindDataContext().OrdersViews.ToList();

            ViewBag.datasource = DataSource;
            
            ViewBag.datasource2 = DataSource2;

            return View();

        }

}


{% endhighlight  %}

{% endtabs %} 

