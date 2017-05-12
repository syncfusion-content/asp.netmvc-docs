---
layout: post
title: Row with Grid widget for Syncfusion Essential MVC
description: How to use and customize the grid row
platform: ejmvc
control: Grid
documentation: ug
---
# Row
It represents the record details that are fetched from the datasource.

## Row Hover
You can see the mouse hovering effect on the corresponding grid rows using `EnableRowHover` property. By default its value is `true`.
The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}

     @(Html.EJ().Grid<OrdersView>("FlatGrid")
         .Datasource((IEnumerable<object>)ViewBag.datasource)
         .AllowPaging()   
         .EnableRowHover(true)        
         .Columns(col =>
          {
             col.Field("OrderID").Add();
             col.Field("EmployeeID").Add();
             col.Field("ShipCity").Add();
             col.Field("ShipCountry").Add();
             col.Field("Freight").Add();
        }))
{% endhighlight %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
      {
       public class GridController : Controller
        {
         public ActionResult Default()
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

![](Row_images/Row_img1.png)

## Details Template

It provides a detailed view /additional information about each row of the grid. You can render any type of JsRender template and assign the script template id in the `DetailsTemplate` property. And also you can change HTML elements in detail template row into JavaScript controls using `DetailsDataBound ` event.

On enabling details template, new column will be added in grid with an expander button in it and that can be expanded or collapsed to show or hide the underlying details row respectively.

N> It's a standard way to enclose the template within the `script` tag with `type` as "text/x-jsrender".

The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}

   @(Html.EJ().Grid<EmployeeView>("DetailTemplate")
          .Datasource((IEnumerable<object>)ViewBag.datasource)
          .DetailsTemplate("#tabGridContents")
          .ClientSideEvents(eve => { eve.DetailsDataBound("detailGridData"); })
          .Columns(col =>
               {
                     col.Field("EmployeeID").Add();
                     col.Field("FirstName").Add();
                     col.Field("Title").Add();
                     col.Field("City").Add();
                     col.Field("Country").Add();
                })
               )
{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
       {
         public class GridController : Controller
           { 
             public ActionResult DetailTemplate()
               {
                   var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
                   ViewBag.datasource = DataSource;
                   return View();
                }
           }
      }
{% endhighlight  %}
{% highlight js %}

   <script id="tabGridContents" type="text/x-jsrender">
        <div class="tabcontrol" id="Test">
                  <ul>
                      <li><a href="#gridTab{{"{{"}}:EmployeeID {{}}}}">Stock Grid</a></li>
                  </ul>
             <div id="gridTab{{"{{"}}:EmployeeID {{}}}}">
                  <div id="detailGrid">
                    </div>
             </div>
       </div>
</script>
<script src="~/Scripts/jsondata.min.js"></script>
<script type="text/javascript">
      function detailGridData(e) {
          var filteredData = e.data["EmployeeID"];
          // the datasource "window.ordersView" is referred from jsondata.min.js
          var data = ej.DataManager(window.ordersView).executeLocal(ej.Query().where("EmployeeID", "equal", parseInt(filteredData), true).take(5));
          e.detailsElement.find("#detailGrid").ejGrid({
          dataSource: data,
          columns: [
                        {field: "OrderID"},
                        {field: "EmployeeID"},
                        {field: "ShipCity"},
                        {field: "ShipCountry"},
	                    {field: "Freight"}
	               ]
	     });
       e.detailsElement.find(".tabcontrol").ejTab();
}
</script>
{% endhighlight  %}
{% endtabs %}
The following output is displayed as a result of the above code example.

![](Row_images/Row_img2.png)

## Row Template

Row template enables you to set the customized look and behavior to grid all rows. `RowTemplate` property can be used bind the `id` of HTML template.
The following code example describes the above behavior.

{% tabs %}
{% highlight  js %}
<script id="templateData" type="text/x-jsrender">
    <tr>
             <td class="photo">
                 <img style="width:130px;height: 160px" src="/13.2.0.29/themes/web/images/employees/{{"{{"}}:EmployeeID {{}}}}.png" alt="{{"{{"}}:EmployeeID {{}}}}" />
             </td>
             <td class="details">
                 <table class="CardTable" cellpadding="3" cellspacing="2">
                      <colgroup>
                              <col width="50%">
                              <col width="50%">
                      </colgroup>
                      <tbody>
                          <tr>
                              <td class="CardHeader">First Name</td>
                              <td>{{"{{"}}:FirstName {{}}}} </td>
                          </tr>
                          <tr>
                              <td class="CardHeader">Last Name</td>
                              <td>{{"{{"}}:LastName {{}}}}</td>
                          </tr>
                          <tr>
                              <td class="CardHeader">Title</td>
                              <td>{{"{{"}}:Title {{}}}}</td>
                          </tr>
                      </tbody>
                 </table>
            </td>
      </tr>
</script>
{% endhighlight  %}
{% highlight  css %}
<style>
    .photo img {
        width: 130px;
    }
    .photo, .details {
        border-color: #c4c4c4;
        border-style: solid;
    }
    .photo {
        border-width: 1px 0px 0px 0px;
    }
    .details {
        border-width: 1px 0px 0px 1px;
    }
    .details > table {
            width: 100%;
        }
    .CardHeader {
        font-weight: bolder;
    }
</style>
{% endhighlight  %}
{% highlight  razor %}
@(Html.EJ().Grid<EmployeeView>("RowTemplate")
        .Datasource((IEnumerable<object>)ViewBag.datasource)
        .Query("new ej.Query().take(2)")
        .Columns(col =>
            {
                col.HeaderText("Photo").Width(30).Add();
                col.HeaderText("Employee Details").Width(70).Add();
            })
       .RowTemplate("#templateData")    // row template
)
{% endhighlight  %}
{% highlight c# %}
namespace MVCSampleBrowser.Controllers
  {
	   public class GridController : Controller
         {
               public ActionResult RowTemplate()
                {
                     var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
                      ViewBag.datasource = DataSource;
                      return View();
                }
         }
  }
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example.

![](Row_images/Row_img3.png)

## Alternate row styling

Alternate row styling enhances the readability of grid rows by setting different background color for every alternate row. You can enable the alternative row styling in grid by using `EnableAltRow` property. 

By default its value is `true`, so the following code example describes the how to turn off alternate row behavior.

{% tabs %}
{% highlight  razor %}

   @(Html.EJ().Grid<OrdersView>("Grid")
         .Datasource((IEnumerable<object>)ViewBag.datasource)
         .AllowPaging()
         .EnableAltRow(false)
         .Columns(col =>
            {
               col.Field("OrderID").Add();
               col.Field("EmployeeID").Add();
               col.Field("ShipCity").Add();
               col.Field("ShipCountry").Add();
               col.Field("Freight").Add();
            })
)
{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
      {
        public class GridController : Controller
         {
           public ActionResult Default()
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

![](Row_images/Row_img4.png)


## Drag-and-Drop

Grid rows can be reordered, dropped to another Grid or custom control by enabling `AllowRowDragAndDrop` Grid property.

N> To enable selection of multiple rows by mouse dragging on Grid rows, `SelectionType` property of Grid must be set to “multiple”.

### Reorder

By simply enabling the property `AllowRowDragAndDrop`, Grid rows can be reordered within the same Grid.

The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}

@(Html.EJ().Grid<OrdersView>("Grid")
        .Datasource(ds => ds.Json((IEnumerable<object>)ViewBag.datasource).Adaptor(AdaptorType.RemoteSaveAdaptor))
        .AllowSorting()
        .AllowPaging()
        .SelectionType(SelectionType.Multiple)
        .AllowRowDragAndDrop()
        .RowDropSettings(drop => drop.RowDropMapper("RowDropHandler"))
        .Columns(col =>
        {
            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
        })
)
{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
      {
        public class GridController : Controller
         {
           public ActionResult Default()
            {
               ViewBag.datasource =OrderRepository.GetAllRecords();
               return View();
            }
            public ActionResult RowDropHandler(List<EditableOrder> changed)
            {
                JavaScriptSerializer ser = new JavaScriptSerializer();
                RowDropModel dropDetails = (RowDropModel)ser.Deserialize(Request.Headers["rowDropDetails"], typeof(RowDropModel));
                var count = 0;
                foreach (var item in changed)
                {
                    EditableOrder result = OrderRepository.GetAllRecords().Where(o => o.OrderID == item.OrderID).FirstOrDefault();
                    OrderRepository.GetAllRecords().Remove(result);
                    OrderRepository.GetAllRecords().Insert(dropDetails.DestinationRowIndex + count, item);
                    count++;
                }
                return Json(changed, JsonRequestBehavior.AllowGet);
           }

        }
     }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed before reordering rows. 

![](Row_images/Row_img5.png)
{:Before Drop}

The following output is displayed after reordering rows.

![](Row_images/Row_img6.png)
{:After Drop}

### Grid-to-Grid

To drag and drop rows between two Grid, enable the Grid property `AllowRowDragAndDrop` and specify the target Grid ID in `DropTargetID` property of Grid `RowDropSettings`.

Dragged and Dropped rows can be mapped to server-side using `RowDragMapper` and `RowDropMapper` property of Grid `RowDropSettings`.

The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}
<div style="float:left;width:49%">
    @(Html.EJ().Grid<OrdersView>("Grid")
        .Datasource(ds => ds.Json((IEnumerable<object>)ViewBag.datasource).Adaptor(AdaptorType.RemoteSaveAdaptor))
        .AllowSorting()
        .AllowPaging()
        .SelectionType(SelectionType.Multiple)
        .AllowRowDragAndDrop()
        .RowDropSettings(drop => drop.RowDragMapper("RowDragHandler").RowDropMapper("RowDropHandler").DropTargetID("#DestGrid"))
        .Columns(col =>
        {
            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
        }))
    </div>

<div style="float:right;width:49%">
    @(Html.EJ().Grid<OrdersView>("DestGrid")
        .Datasource(ds => ds.Json((IEnumerable<object>)ViewBag.datasource2).Adaptor(AdaptorType.RemoteSaveAdaptor))
        .AllowSorting()
        .AllowPaging()
        .SelectionType(SelectionType.Multiple)
        .AllowRowDragAndDrop()
        .RowDropSettings(drop => drop.RowDragMapper("RowDragHandler2").RowDropMapper("RowDropHandler2").DropTargetID("#Grid"))
        .Columns(col =>
        {
            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
        }))
    </div>

{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
{
    public partial class GridController : Controller
    {

        JavaScriptSerializer ser = new JavaScriptSerializer();
        public ActionResult DragAndDrop()
        {
           
            ViewBag.datasource2 = OrderRepository.GetAllRecords2();  
            ViewBag.datasource = OrderRepository.GetAllRecords();
            return View();
        }

        public ActionResult RowDragHandler(List<EditableOrder> deleted)
        {
            OrderRepository.Delete(deleted);
            return Json(deleted, JsonRequestBehavior.AllowGet);
        }
        public ActionResult RowDragHandler2(List<EditableOrder> deleted)
        {
            OrderRepository.Delete2(deleted);
            return Json(deleted, JsonRequestBehavior.AllowGet);
        }

        public ActionResult RowDropHandler(List<EditableOrder> added)
        {
            RowDropModel dropDetails = (RowDropModel)ser.Deserialize(Request.Headers["rowDropDetails"], typeof(RowDropModel));
            var count = 0;
            var data = OrderRepository.GetAllRecords();
            if (added != null)
            {
                foreach (var item in added)
                {
                    data.Insert(dropDetails.DestinationRowIndex + count, item);
                    count++;
                }
            }
            return Json(added, JsonRequestBehavior.AllowGet);
        }
        public ActionResult RowDropHandler2(List<EditableOrder> added)
        {
            RowDropModel dropDetails = (RowDropModel)ser.Deserialize(Request.Headers["rowDropDetails"], typeof(RowDropModel));
            var count = 0;
            var data = OrderRepository.GetAllRecords2();
            foreach (var item in added)
            {
                data.Insert(dropDetails.DestinationRowIndex + count, item);
                count++;
            }
            return Json(added, JsonRequestBehavior.AllowGet);
        }

    }
}

{% endhighlight  %}
{% endtabs %} 

The following output is displayed before dropping Grid rows.

![](Row_images/Row_img7.png)
{:Before Drop}

The following output is displayed after dropping Grid rows.

![](Row_images/Row_img8.png)
{:After Drop}

### Grid-to-Custom control

You can also drag and drop grid rows to any custom control. For instance, let it be a form.

Enable the Grid property `AllowRowDragAndDrop` and specify the target form element ID in `DropTargetID` property of Grid `RowDropSettings`.

On dropping the Grid records on Form element, Grid event “RowDrop” would be triggered by which we can populate input elements in Form.

The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}
<div style="float:left;width:49%">
    @(Html.EJ().Grid<OrdersView>("Grid")
        .Datasource(ds => ds.Json((IEnumerable<object>)ViewBag.datasource).Adaptor(AdaptorType.RemoteSaveAdaptor))
        .AllowSorting()
        .AllowPaging()
        .AllowRowDragAndDrop()
        .RowDropSettings(drop => drop.DropTargetID("#DropForm"))
        .ClientSideEvents(eve => eve.RowDrop("rowDropHandler"))
        .Columns(col =>
        {
            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
        }))
    </div>

<div style="float:right;width:38%">
    <form role="form" id="dropForm" style="width:98%">
        <fieldset style="text-align:center; font-weight:700"><legend>Record Details</legend></fieldset>
        <div class="form-group row">
            <label for="OrderID">Order ID:</label>
            <input class="form-control" name="OrderID">
        </div>
        <div class="form-group row">
            <label for="CustomerID">Customer ID:</label>
            <input name="CustomerID" class="form-control">
        </div>
        <div class="form-group row">
            <label for="EmployeeID">Employee ID:</label>
            <input name="EmployeeID" class="form-control">
        </div>
        <div class="form-group row">
            <label for="Freight">Freight:</label>
            <input name="Freight" class="form-control">
        </div>
        <div class="form-group row">
            <label for="ShipCity">Ship City:</label>
            <input name="ShipCity" class="form-control">
        </div>
        <br />
    </form>
</div>

{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
      {
        public class GridController : Controller
         {
           public ActionResult Default()
            {
               ViewBag.datasource =OrderRepository.GetAllRecords();
               return View();
            }
        }
     }
{% endhighlight  %}
{% highlight js %}
<script type="text/javascript">
function rowDropHandler(args) {
        for (var key in args.data[0]) {
            $('#dropForm input[name=' + key + ']').val(args.data[0][key]);
        }
    }

</script>

{% endhighlight  %}
{% endtabs %} 

The following output is displayed before dropping the rows on Form.

![](Row_images/Row_img9.png)
{:Before Drop}

The following output is displayed after dropping the rows on Form.

![](Row_images/Row_img10.png)
{:After Drop}

N>   The default behavior of drag and drop between Grid or any other controls is as cut and paste. For copy and paste behavior specify the drag behavior in [`dragBehavior`] property of Grid as copy.