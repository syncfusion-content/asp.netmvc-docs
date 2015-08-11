---
layout: post
title: Set-Dynamic-DataSource-to-Grid
description: set dynamic datasource to grid
platform: wpf
control: Grid
documentation: ug
---

## Set Dynamic DataSource to Grid

Grid control is capable of updating its dataSource as and when required. Grid method “DataSource” helps in achieving this and in this method parameter, you have to pass the new dataSource as List Collection.

For instance, consider a textbox above Grid and depending on its value, you can update a new datasource to Grid dynamically.

{% highlight html %}

[MVC]



[razor]

Enter EmployeeID Field Value:

<input type="text" id="colValue" />

<input type="button" id="customButton" value="Change DataSource">



 @(Html.EJ().Grid<EJGrid.Models.Order>("Grid")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

                             .AllowPaging()

                                           .Columns(col =>

                                         {

                                             col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Width(75).Add();

                                             col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(90).Add();

                                             col.Field("Freight").HeaderText("Freight").Format("{0:c}").TextAlign(TextAlign.Right).Width(90).Add();

                                             col.Field("ShipCity").HeaderText("Ship City").Width(90).Add();

                                             col.Field("Child.Test").HeaderText("TEst").Format("{0:c}").Width(90).Add();

                                             col.Field("ShipCountry").HeaderText("Ship Country").Width(90).Add();

                                         })

)
{% endhighlight  %}
{% highlight js %}
<script>

    $("#customButton").ejButton({

        size: "Normal", click: function (args) {

            var obj = $("#Grid").ejGrid("instance");

            var value = $("#colValue").val();

            //Add custom paramter to the server

            var query = new ej.Query().addParams("EmployeeID", value);



            //Creating ejDataManager with UrlAdaptor



            var dm = ej.DataManager({ url: "/Home/GetData", adaptor: new ej.UrlAdaptor() });



            var promise = dm.executeQuery(query);



            promise.done(function (e) {

                //Assign the result to the grid dataSource using "dataSource" method.

                obj.dataSource(e.result);

            });



        }})

</script>

{% endhighlight  %}
{% highlight c# %}
[Controller]

namespace EJGrid.Controllers

{

    public class HomeController : Controller

    {

        public ActionResult Index()

        {

            ViewBag.datasource = null;

            return View();

        }



        public JsonResult GetData(int EmployeeID)

        {

            var data = new DataClasses1DataContext().Orders.Where(ds => ds.EmployeeID ==        EmployeeID).ToList();

            return Json(data, JsonRequestBehavior.AllowGet);

        }

    }

}


{% endhighlight %}


The following screenshot illustrates the output.

![C:/Users/ApoorvahR/Desktop/1.png](Set-Dynamic-DataSource-to-Grid_images/Set-Dynamic-DataSource-to-Grid_img1.png)



