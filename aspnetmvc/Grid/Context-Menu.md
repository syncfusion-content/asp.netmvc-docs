---
layout: post
title: Context Menu with Grid widget for Syncfusion Essential ASP.NET MVC
description: How to enable contextMenu and its functionalities
platform: ejmvc
control: Grid
documentation: ug
---

# Context Menu

Context menu is used to improve user action with Grid using popup menu. It can be shown by defining `EnableContextMenu` property of `ContextMenuSettings` as true. Context menu has option to add default items in `ContextMenuItems` property of `ContextMenuSettings` and customized items in `CustomContextMenuItems` property of `ContextMenuSettings`.

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
                Sort column in Ascending order
            </td>
        </tr>
        <tr>
            <td>
                Sort in Descending Order
            </td>
            <td>
                Sort column in Descending order
            </td>
        </tr>
        <tr>
            <td>
                Group
            </td>
            <td>
                Group the current column
            </td>
        </tr>
        <tr>
            <td>
                Ungroup
            </td>
            <td>
                Ungroup the current column if already grouped
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
                Start Add new record
            </td>
        </tr>
        <tr>
            <td>
                Edit Record
            </td>
            <td>
                Start Edit in current record
            </td>
        </tr>
        <tr>
            <td>
                Delete Record
            </td>
            <td>
                Delete the current record
            </td>
        </tr>
        <tr>
            <td>
                Save
            </td>
            <td>
                Save the record if Add/Edit record is started
            </td>
        </tr>
        <tr>
            <td>
                Cancel
            </td>
            <td>
                Cancel Added/Edited state
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
                Go to Next Page
            </td>
        </tr>
        <tr>            
            <td>
                Last Page
            </td>
            <td>
                Go to Last page
            </td>
        </tr>
        <tr>
            <td>
                Previous page
            </td>
            <td>
                Go to previous page
            </td>
        </tr>
        <tr>
            <td>
                First page
            </td>
            <td>
                Go to first page
            </td>
        </tr>
 </table>
 
{% tabs %}
{% highlight cshtml %}

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

        col.Field("Freight").Format("{0:c3}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();

        col.Field("ShipName").HeaderText("Ship Name").Width(150).Add();

    })
)
{% endhighlight  %}

{% highlight c# %}

namespace MvcApplication66.Controllers
{
    public class HomeController : Controller
    {
        public static List<Orders> order = new List<Orders>();
        public ActionResult Index(){
            GetData();
            ViewBag.datasource = order;
            return View();
        }
        public void GetData() {
            int orderId = 10643;
            int empId = 0;
            for (int i = 1; i < 10; i++)
            {
                order.Add(new Orders(orderId + 1, "ALFKI", empId + 1, 32.38, "Alfreds Futterkiste "));
                order.Add(new Orders(orderId + 2, "ANATR", empId + 2, 11.61, "Ana Trujillo Emparedados y helados"));
                order.Add(new Orders(orderId + 3, "ANTON", empId + 3, 45.34, "Antonio Moreno Taquería"));
                order.Add(new Orders(orderId + 4, "AROUT", empId + 4, 37.28, "Around the Horn"));
                order.Add(new Orders(orderId + 5, "BERGS", empId + 5, 67.00, "Berglunds snabbköp"));
                order.Add(new Orders(orderId + 6, "BLONP", empId + 6, 23.32, "Blondel père et fils"));
                orderId += 6;
                empId += 6;
            }
        }
        public class Orders
        {
            public Orders()
            {

            }
            public Orders(long OrderId, string CustomerId, int EmployeeId, double Freight, string ShipName)
            {
                this.OrderID = OrderId;
                this.CustomerID = CustomerId;
                this.EmployeeID = EmployeeId;
                this.Freight = Freight;
                this.ShipName = ShipName;
                
            }
            public long OrderID { get; set; }
            public string CustomerID { get; set; }
            public int EmployeeID { get; set; }
            public double Freight { get; set; }
            public string ShipName { get; set; }
        }
    }
}

{% endhighlight  %}
    
{% endtabs %} 

![](Context-Menu_images/ContextMenu_img1.png)
{:caption}

Contextmenu at header

![](Context-Menu_images/ContextMenu_img2.png)
{:caption}

Contextmenu at body

![](Context-Menu_images/ContextMenu_img3.png)
{:caption}

Contextmenu at pager

N> `AllowGrouping`, `AllowSorting` should be enabled to perform default context menu actions in Grid header. `AllowEditing`, `AllowDeleting` and `AllowAdding` should be enabled to perform default actions in body.

## Custom Context Menu

Custom context menu is used to create your own menu item and its action. To add customized context menu items, you need to use [`contextMenuSettings.customContextMenuItems`](http://help.syncfusion.com/js/api/ejgrid#members:contextmenusettings-customcontextmenuitems "contextMenuSettings.customContextMenuItems") property and to bind required actions for this, use [`contextClick`](http://help.syncfusion.com/js/api/ejgrid#events:contextclick "contextClick") event.


{% tabs %}
{% highlight cshtml %}

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
        contextMenu.ContextMenuItems(new List<string>(){
            "Clear Selection"
        });
    })
    .AllowPaging()
    .AllowSorting()
    .AllowGrouping()
    .ClientSideEvents(eve => {eve.ContextClick("contextclick");})
    .Columns(col =>
    {
        col.Field("OrderID").IsPrimaryKey(true).HeaderText("Order ID").TextAlign(TextAlign.Right).Width(90).Add();

        col.Field("CustomerID").HeaderText("Customer ID").Width(90).Add();

        col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(90).Add();

        col.Field("Freight").Format("{0:c3}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();

        col.Field("ShipName").HeaderText("Ship Name").Width(150).Add();

    })
)
<script type="text/javascript">
    function contextclick(args) {
        if (args.text == "Clear Selection")
            this.clearSelection();
    }
</script>

{% endhighlight  %}

{% highlight c# %}

namespace MvcApplication66.Controllers
{
    public class HomeController : Controller
    {
        public static List<Orders> order = new List<Orders>();
        public ActionResult Index(){
            GetData();
            ViewBag.datasource = order;
            return View();
        }
        public void GetData() {
            int orderId = 10643;
            int empId = 0;
            for (int i = 1; i < 10; i++)
            {
                order.Add(new Orders(orderId + 1, "ALFKI", empId + 1, 32.38, "Alfreds Futterkiste "));
                order.Add(new Orders(orderId + 2, "ANATR", empId + 2, 11.61, "Ana Trujillo Emparedados y helados"));
                order.Add(new Orders(orderId + 3, "ANTON", empId + 3, 45.34, "Antonio Moreno Taquería"));
                order.Add(new Orders(orderId + 4, "AROUT", empId + 4, 37.28, "Around the Horn"));
                order.Add(new Orders(orderId + 5, "BERGS", empId + 5, 67.00, "Berglunds snabbköp"));
                order.Add(new Orders(orderId + 6, "BLONP", empId + 6, 23.32, "Blondel père et fils"));
                orderId += 6;
                empId += 6;
            }
        }
        public class Orders
        {
            public Orders()
            {

            }
            public Orders(long OrderId, string CustomerId, int EmployeeId, double Freight, string ShipName)
            {
                this.OrderID = OrderId;
                this.CustomerID = CustomerId;
                this.EmployeeID = EmployeeId;
                this.Freight = Freight;
                this.ShipName = ShipName;
                
            }
            public long OrderID { get; set; }
            public string CustomerID { get; set; }
            public int EmployeeID { get; set; }
            public double Freight { get; set; }
            public string ShipName { get; set; }
        }
    }
}

{% endhighlight  %}
    
{% endtabs %}

![](Context-Menu_images/ContextMenu_img4.png)


## Sub Context Menu

Sub context menu is used to add customized sub menu to the custom context menu item. To add a sub context menu, you need to use [`contextMenuSettings.subContextMenu`](http://help.syncfusion.com/js/api/ejgrid#members:contextmenusettings-subcontextmenu "contextMenuSettings.subContextMenu") property and to bind required actions for this, use [`contextClick`](http://help.syncfusion.com/js/api/ejgrid#events:contextclick "contextClick") event.

{% tabs %}
{% highlight cshtml %}

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
        contextMenu.ContextMenuItems(new List<string>(){
            "Clear Selection",
            "Hide Column"
        });
        contextMenu.SubContextMenu(submenu =>
        {
            submenu.ContextMenuItem("Hide Column").SubMenu(new List<string>() { "Order ID", "Customer ID", "Employee ID" }).Add();
        });
     })
    .AllowPaging()
    .AllowSorting()
    .AllowGrouping()
    .ClientSideEvents(eve => {eve.ContextClick("contextclick");})
    .Columns(col =>
    {
        col.Field("OrderID").IsPrimaryKey(true).HeaderText("Order ID").TextAlign(TextAlign.Right).Width(90).Add();

        col.Field("CustomerID").HeaderText("Customer ID").Width(90).Add();

        col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(90).Add();

        col.Field("Freight").Format("{0:c3}").HeaderText("Freight").Width(80).TextAlign(TextAlign.Right).Add();

        col.Field("ShipName").HeaderText("Ship Name").Width(150).Add();

    })
)

<script type="text/javascript">
    function contextclick(args) {
        if (args.text == "Clear Selection")
            this.clearSelection();
        else if (args.text != "Hide Column")
            this.hideColumns(args.text);
    }
</script>

{% endhighlight  %}

{% highlight c# %}

namespace MvcApplication66.Controllers
{
    public class HomeController : Controller
    {
        public static List<Orders> order = new List<Orders>();
        public ActionResult Index(){
            GetData();
            ViewBag.datasource = order;
            return View();
        }
        public void GetData() {
            int orderId = 10643;
            int empId = 0;
            for (int i = 1; i < 10; i++)
            {
                order.Add(new Orders(orderId + 1, "ALFKI", empId + 1, 32.38, "Alfreds Futterkiste "));
                order.Add(new Orders(orderId + 2, "ANATR", empId + 2, 11.61, "Ana Trujillo Emparedados y helados"));
                order.Add(new Orders(orderId + 3, "ANTON", empId + 3, 45.34, "Antonio Moreno Taquería"));
                order.Add(new Orders(orderId + 4, "AROUT", empId + 4, 37.28, "Around the Horn"));
                order.Add(new Orders(orderId + 5, "BERGS", empId + 5, 67.00, "Berglunds snabbköp"));
                order.Add(new Orders(orderId + 6, "BLONP", empId + 6, 23.32, "Blondel père et fils"));
                orderId += 6;
                empId += 6;
            }
        }
        public class Orders
        {
            public Orders()
            {

            }
            public Orders(long OrderId, string CustomerId, int EmployeeId, double Freight, string ShipName)
            {
                this.OrderID = OrderId;
                this.CustomerID = CustomerId;
                this.EmployeeID = EmployeeId;
                this.Freight = Freight;
                this.ShipName = ShipName;
                
            }
            public long OrderID { get; set; }
            public string CustomerID { get; set; }
            public int EmployeeID { get; set; }
            public double Freight { get; set; }
            public string ShipName { get; set; }
        }
    }
}

{% endhighlight  %}
    
{% endtabs %}

![](Context-Menu_images/ContextMenu_img5.png)
