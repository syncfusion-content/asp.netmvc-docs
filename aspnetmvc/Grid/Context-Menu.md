---
layout: post
title: Context Menu with Grid widget for Syncfusion Essential ASP.NET MVC
description: How to enable contextMenu and its functionalities
platform: ejmvc
control: Grid
documentation: ug
---

# Context Menu

Context menu is used to improve the user action with Grid using popup menu. It can be shown by defining the `EnableContextMenu` property of `ContextMenuSettings` as true. Context menu has option to add default items in the `ContextMenuItems` property of `ContextMenuSettings` and customized items in the `CustomContextMenuItems` property of `ContextMenuSettings`.

## Default Context Menu items

Please find the below table for default context menu items and its actions.

 <table>
        <tr>
            <th>
                Section
            </th>
            <th>
                Context menu items
            </th>
            <th>
                Action
            </th>
        </tr>
        <tr>
            <td rowspan="4">
                Header
            </td>
            <td>
                Sort in Ascending Order
            </td>
            <td>
                Sort column in Ascending order.
            </td>
        </tr>
        <tr>
            <td>
                Sort in Descending Order
            </td>
            <td>
                Sort column in Descending order.
            </td>
        </tr>
        <tr>
            <td>
                Group
            </td>
            <td>
                Group the current column.
            </td>
        </tr>
        <tr>
            <td>
                Ungroup
            </td>
            <td>
                Ungroup the current column if already grouped.
            </td>
        </tr>
        <tr>
            <td rowspan="5">
                Body
            </td>
            <td>
                Add Record
            </td>
            <td>
                Start Add new record.
            </td>
        </tr>
        <tr>
            <td>
                Edit Record
            </td>
            <td>
                Start Edit in current record.
            </td>
        </tr>
        <tr>
            <td>
                Delete Record
            </td>
            <td>
                Delete the current record.
            </td>
        </tr>
        <tr>
            <td>
                Save
            </td>
            <td>
                Save the record if Add/Edit record is started.
            </td>
        </tr>
        <tr>
            <td>
                Cancel
            </td>
            <td>
                Cancel Added/Edited state.
            </td>
        </tr>
        <tr>
            <td rowspan="4">
                Pager
            </td>
            <td>
                Next Page
            </td>
            <td>
                Go to Next Page.
            </td>
        </tr>
        <tr>            
            <td>
                Last Page
            </td>
            <td>
                Go to Last page.
            </td>
        </tr>
        <tr>
            <td>
                Previous page
            </td>
            <td>
                Go to previous page.
            </td>
        </tr>
        <tr>
            <td>
                First page
            </td>
            <td>
                Go to first page.
            </td>
        </tr>
 </table>
 
{% tabs %}
{% highlight RAZOR %}

    @(Html.EJ().Grid<object>("FlatGrid")
        .Datasource((IEnumerable<object>)ViewBag.datasource)
        .EditSettings(edit =>
        {
            edit.AllowAdding().AllowDeleting().AllowEditing();
        })
        .ToolbarSettings(toolbar =>
        {
            toolbar.ShowToolbar().ToolbarItems(items =>
            {
                items.AddTool(ToolBarItems.Add);
                items.AddTool(ToolBarItems.Edit);
                items.AddTool(ToolBarItems.Delete);
                items.AddTool(ToolBarItems.Update);
                items.AddTool(ToolBarItems.Cancel);
            });
        })
        .ContextMenuSettings(contextMenu =>
        {
            contextMenu.EnableContextMenu();
        })
        .AllowPaging()
        .AllowSorting()
        .AllowGrouping()
        .Columns(col =>
        {
            col.Field("OrderID").IsPrimaryKey(true).HeaderText("Order ID").TextAlign(TextAlign.Right).Width(90).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Width(90).Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(90).Add();

            col.Field("Freight").Format("{0:c2}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();

            col.Field("ShipName").HeaderText("Ship Name").Width(150).Add();

        })
    )
{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
    {
        public class GridController : Controller
        {
            public ActionResult Index(){
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }

{% endhighlight  %}
    
{% endtabs %} 

![](Context-Menu_images/ContextMenu_img1.png)
{:caption}

Context menu at header

![](Context-Menu_images/ContextMenu_img2.png)
{:caption}

Context menu at body

![](Context-Menu_images/ContextMenu_img3.png)
{:caption}

Context menu at pager

N> `AllowGrouping`, `AllowSorting` should be enabled to perform default context menu actions in Grid header. `AllowEditing`, `AllowDeleting` and `AllowAdding` should be enabled to perform default actions in body.

## Custom Context Menu

Custom context menu is used to create your own menu item and its action. To add customized context menu items, you need to use the `ContextMenuSettings.CustomContextMenuItems` property and to bind required actions for this, use the `ContextClick` event.


{% tabs %}
{% highlight RAZOR %}

    @(Html.EJ().Grid<object>("FlatGrid")
        .Datasource((IEnumerable<object>)ViewBag.datasource)
        .ContextMenuSettings(contextMenu =>
        {
            contextMenu.EnableContextMenu();
            contextMenu.DisableDefaultItems();
            contextMenu.CustomContextMenuItems(new List<CustomContextMenuItems> { new CustomContextMenuItems() { Id = "clear", Text = "Clear Selection" }});
        })
        .AllowPaging()        
        .ClientSideEvents(eve => {eve.ContextClick("context_click");})
        .Columns(col =>
        {
            col.Field("OrderID").IsPrimaryKey(true).HeaderText("Order ID").TextAlign(TextAlign.Right).Width(90).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Width(90).Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(90).Add();

            col.Field("Freight").Format("{0:c2}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();

            col.Field("ShipCountry").HeaderText("Ship Country").Width(150).Add();

        })
    )
    <script type="text/javascript">
        function context_click(args) {
            if (args.text == "Clear Selection")
                this.clearSelection();
        }
    </script>

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
    {
        public class GridController : Controller
        {
            public ActionResult Index(){
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }

{% endhighlight  %}
    
{% endtabs %}

![](Context-Menu_images/ContextMenu_img4.png)


## Sub Context Menu

Sub context menu is used to add customized sub menu to the custom context menu item. To add a sub context menu, you need to use the `ContextMenuSettings.SubContextMenu` property and to bind required actions for this, use the `ContextClick` event.

{% tabs %}
{% highlight RAZOR %}

    @(Html.EJ().Grid<object>("FlatGrid")
        .Datasource((IEnumerable<object>)ViewBag.datasource)
         .ContextMenuSettings(contextMenu =>
                        {
                            contextMenu.EnableContextMenu();
                            contextMenu.DisableDefaultItems();
                            contextMenu.CustomContextMenuItems(new List<CustomContextMenuItems> { new CustomContextMenuItems() { Id = "clear", Text = "Clear Selection" }, new CustomContextMenuItems() { Id = "hide", Text = "Hide Column" } });
                            contextMenu.SubContextMenu(submenu =>
                            {
                                submenu.ContextMenuItem("hide").SubMenu(new List<string>() { "Order ID", "Customer ID", "Employee ID" }).Add();
                            });
                        })
        .AllowPaging()        
        .ClientSideEvents(eve => {eve.ContextClick("context_click");})
        .Columns(col =>
        {
            col.Field("OrderID").IsPrimaryKey(true).HeaderText("Order ID").TextAlign(TextAlign.Right).Width(90).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Width(90).Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(90).Add();

            col.Field("Freight").Format("{0:c2}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();

            col.Field("ShipCountry").HeaderText("Ship Country").Width(150).Add();

        })
    )

    <script type="text/javascript">
        function context_click(args) {
            if (args.text == "Clear Selection")
                this.clearSelection();
            else if (args.text == "Hide Column")
                this.hideColumns(args.text);
        }
    </script>

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
    {
        public class GridController : Controller
        {
            public ActionResult Index(){
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }

{% endhighlight  %}
    
{% endtabs %}

![](Context-Menu_images/ContextMenu_img5.png)

## Sub Context Menu with Template

On rendering the Sub context menu items, the customized sub menu items is created by using the `ContextMenuSettings.SubContextMenu.Template` property.

{% tabs %}
{% highlight RAZOR %}

    @(Html.EJ().Grid<object>("FlatGrid")
        .Datasource((IEnumerable<object>)ViewBag.datasource)
         .ContextMenuSettings(contextMenu =>
                        {
                            contextMenu.EnableContextMenu();
                            contextMenu.DisableDefaultItems();
                            contextMenu.CustomContextMenuItems(new List<CustomContextMenuItems> { new CustomContextMenuItems() { Id = "clear", Text = "Clear Selection" }, new CustomContextMenuItems() { Id = "hide", Text = "Hide Column" } });
                            contextMenu.SubContextMenu(submenu =>
                            {
                                submenu.ContextMenuItem("hide").Template("#template").Add();
                            });
                        })
        .AllowPaging()        
        .ClientSideEvents(eve => {eve.ContextClick("context_click");})
        .Columns(col =>
        {
            col.Field("OrderID").IsPrimaryKey(true).HeaderText("Order ID").TextAlign(TextAlign.Right).Width(90).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Width(90).Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(90).Add();

            col.Field("Freight").Format("{0:c2}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();

            col.Field("ShipCountry").HeaderText("Ship Country").Width(150).Add();

        })
    )
{% endhighlight  %}
{% highlight js %}
    <script type="text/javascript">
        function context_click(args) {
            if (args.text == "Clear Selection")
                this.clearSelection();
            else if (args.text != "Hide Column")
                this.hideColumns(args.text);
        }
    </script>
    <script type= "text/x-jsrender" id=template>
        <ul>
            <li><a>OrderID</a></li>
            <li><a>CustomerID</a></li>
            <li><a>EmployeeID</a></li>
        </ul>
    </script>
{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
    {
        public class GridController : Controller
        {
            public ActionResult Index(){
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }

{% endhighlight  %}
    
{% endtabs %}

![](Context-Menu_images/ContextMenu_img5.png)

