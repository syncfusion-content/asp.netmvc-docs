---
layout: post
title: Custom Binding for Grid CRUD operation | Grid | ASP.NET MVC | Syncfusion
description: custom binding for grid crud operation
platform: ejmvc
control: Grid
documentation: ug
---

# Custom Binding for Grid CRUD operation

In Grid control DataManager is used for data processing. The adaptors of dataManager are customizable that can be extended for custom Binding with server-side for Grid CRUD operation.

For instance bind the data to Grid by using “remoteSaveAdaptor” and extend it to modify its update method to bind edited record values of Grid as “FormCollection” in server-side.

{% tabs %}

{% highlight CSHTML %}

@(Html.EJ().Grid<EJGrid.Models.Order>("Grid")

        .Datasource(ds => ds.Json((IEnumerable<object>)ViewBag.datasource).UpdateURL("Home/Update")

            .InsertURL("Home/Insert").RemoveURL("Home/Remove").Adaptor("remoteSaveAdaptor"))

        .AllowSorting()

        .AllowPaging()

        .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing(); })

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

        .Columns(col =>

        {

            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(90).ValidationRules(v => v.AddRule("required", true).AddRule("number", true)).Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(90).ValidationRules(v => v.AddRule("required", true)).Add();

            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(80).Add();

            col.Field("ShipName").HeaderText("ShipName").Width(150).Add();

        })

        .ClientSideEvents(eve => eve.Load("load"))

)


    var adaptor = new ej.remoteSaveAdaptor().extend({

        insert: function (dm, data, tableName) {

            return {

                url: dm.dataSource.insertUrl,

                dataType: 'json',

                contentType: "application/x-www-form-urlencoded; charset=utf-8",

                data: $("#GridEditForm").serialize()

            };

        },

        update: function (dm, keyField, value, tableName) {

            return {

                type: "POST",

                url: dm.dataSource.updateUrl+"?id="+value.OrderID,

                dataType: 'json',

                contentType: "application/x-www-form-urlencoded; charset=utf-8",

                data: $("#GridEditForm").serialize()

            };

        },

    })



    function load(args) {

        this.model.dataSource.adaptor = new adaptor();

    }

{% endhighlight %}



{% highlight C# %}

namespace EJGrid.Controllers

{

    public class HomeController : Controller

    {

        public ActionResult Index()

        {

            ViewBag.datasource = OrderRepository.GetAllRecords();

            return View();

        }



        public ActionResult Update(int id, FormCollection value)

        {

            var ord = new EditableOrder();

            ord.OrderID = id;

            if (value["EmployeeID"] != "")

            ord.EmployeeID = Convert.ToInt32(value["EmployeeID"]);

            if (value["Freight"] != "")

            ord.Freight = Convert.ToDecimal(value["Freight"]);

            if (value["ShipCity"] != null)

            ord.ShipCity = value["ShipCity"];

            OrderRepository.Update(ord);

            var data = OrderRepository.GetAllRecords();

            return Json(data, JsonRequestBehavior.AllowGet);

        }

        public ActionResult Insert(FormCollection value)

        {

            var ord = new EditableOrder();

            ord.OrderID = Convert.ToInt32(value["OrderID"]);

            if (value["EmployeeID"] != "")

                ord.EmployeeID = Convert.ToInt32(value["EmployeeID"]);

            if (value["Freight"] != "")

                ord.Freight = Convert.ToDecimal(value["Freight"]);

            if (value["ShipCity"] != null)

                ord.ShipCity = value["ShipCity"];

            OrderRepository.Add(ord);

            var data = OrderRepository.GetAllRecords();

            return Json(data, JsonRequestBehavior.AllowGet);

        }

    }

}

{% endhighlight %}
{% endtabs %}  

The output is as follows.
{% include image.html url="/aspnetmvc/Grid/How-to/DCustom-Binding-for-Grid-CRUD-operation_images/Custom-Binding-for-Grid-CRUD-operation_img1.png"%}

































