---
layout: post
title: Data-Adaptors
description: data adaptors
platform: ejmvc
control: DataManager
documentation: ug
---

# Data Adaptors

DataManger uses adaptors to process data. There are three types of adaptors in the DataManger. They are

* JSON Adaptor
* Url Adaptor
* OData Adaptor

Here, you can learn when and how each adaptor is used.

## JSON Adaptor

JSONAdaptor is used to process JSON data. It contains methods to process the given JSON data based on the queries. The following code example illustrates on how to use the JSONAdaptor.

{% highlight js %}

@(Html.EJ().DataManager("FlatData").Json((IEnumerable<object>)ViewBag.dataSource))



@(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")

        .DataManagerID("FlatData")

        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).take(5)")



        .Columns(col =>

        {

            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();

            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();



        })

)
{% endhighlight %}


The result of above code example is illustrated as follows.



![](Data-Adaptors_images/Data-Adaptors_img1.png)



## URL Adaptor

Url Adaptor of the DataManager can be used when you are required to use remote service to retrieve data. It interacts with server-side for all DataManager Queries and CRUD operations. Now, in the following code example, the data is retrived from the MVCController. 

{% highlight js %}

@(Html.EJ().DataManager("FlatData").URL("Home/DataSource").Adaptor(AdaptorType.UrlAdaptor))



@(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")

        .DataManagerID("FlatData")

        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).take(5)")



        .Columns(col =>

        {

            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();

            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();



        })

)

{% endhighlight %}
{% highlight c# %}


		public class HomeController : Controller

        {

            public ActionResult Index()

            {

                return View();

            }

            public ActionResult DataSource(Syncfusion.JavaScript.DataManager dm)

            {

                var DataSource = OrderRepository.GetAllRecords();

                DataResult result = new DataResult();

                result.result = DataSource.Skip(dm.Skip).Take(dm.Take).ToList();

                result.count = DataSource.Count();

                return Json(result, JsonRequestBehavior.AllowGet);

            }

            public class DataResult

            {

                public IEnumerable<EditableOrder> result { get; set; }

                public int count { get; set; }

            }

        }

{% endhighlight %}

The result of the above code example is illustrated as follows.



![](Data-Adaptors_images/Data-Adaptors_img2.png)



## OData Adaptor

Odata Adaptor that is extended from Url Adaptor is used for consuming data through oData Service. You can use the following code example to use oData adaptor.

{% highlight js %}

@(Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/").Offline(true).CrossDomain(true))



@(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")

        .DataManagerID("FlatData")

        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).take(5)")



        .Columns(col =>

        {

            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();

            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();



        })

)


{% endhighlight %}


The result of the above code example is illustrated as follows.

![](Data-Adaptors_images/Data-Adaptors_img3.png)



## WebAPI Adaptor

WebAPIAdaptor extended from the UrlAdaptor of the DataManager is used for retrieving data from WebAPI service. Refer to the following code example.
{% highlight js %}
@(Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/UGService/api/Orders").Adaptor(AdaptorType.WebApiAdaptor))



@(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")

        .DataManagerID("FlatData")

        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).take(5)")



        .Columns(col =>

        {

            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();

            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();



        })

)


{% endhighlight %}


Result of the above code example is illustrated as follows.



![](Data-Adaptors_images/Data-Adaptors_img4.png)





_Web API Adaptor_

## RemoteSave Adaptor

RemoteSaveAdaptor extended from the JsonAdaptor of theDataManager is used for binding local data and performs all DataManager queries in client-side. It interacts with server-side only for CRUD operations to pass the modified records. Refer to the following code example.

{% highlight js %}





@(Html.EJ().DataManager("FlatData").Json((IEnumerable<object>)ViewBag.dataSource).Adaptor(AdaptorType.RemoteSaveAdaptor))



@(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")

        .DataManagerID("FlatData")

        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).take(5)")



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





		public class HomeController : Controller

        {

            public ActionResult Index()

            {

                return View();

            }

            public ActionResult DataSource(Syncfusion.JavaScript.DataManager dm)

            {

                var DataSource = OrderRepository.GetAllRecords();

                DataResult result = new DataResult();

                result.result = DataSource.Skip(dm.Skip).Take(dm.Take).ToList();

                result.count = DataSource.Count();

                return Json(result, JsonRequestBehavior.AllowGet);

            }

            public class DataResult

            {

                public IEnumerable<EditableOrder> result { get; set; }

                public int count { get; set; }

            }

        }

{% endhighlight  %}

Result of the above code example is illustrated as follows.

![](Data-Adaptors_images/Data-Adaptors_img5.png)



## Custom Adaptor

Custom Adaptor is a key technique to customize adaptors in the DataManager. It is useful to write own adaptor. Normally ej.Adaptor is base class for all adaptors. Therefore, first inherit the ej.Adaptor to develop the customized one and then override functionality in Custom Adaptor with base class. The following code example illustrates you how to create the Custom Adaptor.

{% highlight html %}

@(Html.EJ().DataManager("FlatData”))



@(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")

        .DataManagerID("FlatData")

        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).take(5)")



        .Columns(col =>

        {

            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();

            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();



        })

)

{% endhighlight %}
{% highlight js %}

<script type="text/javascript">

        $(function () {// Document is ready.

            //new custom adaptor implementation

            //able to implement more option in custom adaptor other than insert

            var customAdaptor = new ej.Adaptor().extend({

                insert: function (dm, data) {

                    return dm.dataSource.json.push(data);

                },

                processQuery: ej.JsonAdaptor.prototype.processQuery // reused process query from json adaptor

            });

            window.FlatData.Adaptor = new customAdaptor()

            window.FlatData.insert({ OrderID: 10240, CustomerID: "HANAR", EmployeeID: 3, ShipCity: "Reims", Freight: "23.4" });

            window.FlatData.insert({ OrderID: 10241, CustomerID: "HANAR", EmployeeID: 2, ShipCity: "Reimse", Freight: "21.4" });

            window.FlatData.insert({ OrderID: 10242, CustomerID: "VINET", EmployeeID: 5, ShipCity: "Lyon", Freight: "13.4" });

            var obj = $("#MainContent_OrdersGrid").ejGrid("instance");

            obj.dataSource(window.FlatData.executeLocal(new ej.Query().take(7)));

        })



</script>
{% endhighlight %}


Result of above code example is as follows.

![](Data-Adaptors_images/Data-Adaptors_img6.png)



