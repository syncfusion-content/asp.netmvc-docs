---
layout: post
title: Advanced Functionalities | DataManager  | ASP.NET MVC | Syncfusion
description: Advanced Functionalities
platform:  ejmvc
control: DataManager
documentation: ug
keywords: Offline Support, Load on Demand, Customer Request Headers, HTML Table, Cross domain & JSONP

---
# Advanced Functionalities

## Offline Support

Offline support allows data-bound Syncfusion UI widgets to function without active server connection. Users can continue working with the data.

With offline as true, the DataManager requests the server only once and further data manipulation operation can be done at client side itself.

In the following code example, the offline property of the DataManager is set as true.

{% highlight CSHTML %}

    @Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/").Offline(true))

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

![](Data-Binding_images/Data-Binding_img8.png)

Figure offline mode 
{:.caption}   

## Load on demand

Load on demand is powerful technique to reduce band width size of consuming data. It allow you to retrieve the required range of data alone from the server and this feature helps you when the server contains large amount of data.

You can use the following code example for implementing load on demand using DataManager.

{% highlight CSHTML %}

    @Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/").CrossDomain(true))

    @(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")
            .DataManagerID("FlatData")
            .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).page(1,3)")
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
                col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
                col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
            })
    )

    pageIndex: <input id="pageIndex" type="text" placeholder="pageindex" />

    pageSize:  <input id="pageSize" type="text" placeholder="pageSize" />

    @Html.EJ().Button("submit").Text("LoadOnDemand").ClientSideEvents(e => { e.Click("onClick"); })


    <script type="text/javascript" class="jsScript">

        function onClick(e) {

            var from = parseInt($("#pageIndex").val());
            var to = parseInt($("#pageSize").val());
            var obj = $("#FlatGrid").ejGrid("instance")
            tempQuery = new ej.Query();
            tempQuery.page(from, to);
            var dataObj = window.FlatData.executeQuery(tempQuery).done(function (e1) {
                obj.dataSource(e1.result);

            })
        }

    </script>

{% endhighlight  %}

The result of the above code example is illustrated as follows.

![](Data-Binding_images/Data-Binding_img9.png)

Load on demand
{:.caption}

The request and the response for the above code are sent as follows.

![](Data-Binding_images/Data-Binding_img10.png)

Demanded data     
{:.caption}

## Custom Request Headers

You can add custom request headers using **DataManager** and the headers can be added to the request headers in three ways that is illustrated in the following code example.

### Adding Custom Request Headers to every Request using headers

You can add custom request headers to every request made by the **DataManager** using the `headers` property. Refer to the following code example for setting the custom request headers using the `headers` property.

{% highlight C# %}

    public ActionResult GridFeatures()
    {
        var DataSource = new NorthwindDataContext().OrdersViews.ToList();
        ViewBag.data = DataSource;
        return View();
    }

{% endhighlight %}

{% highlight CSHTML %}

    @(Html.EJ().DataManager("FlatData").Json((IEnumerable<object>)ViewBag.data).Headers(new { myData = 3232323 }))

    @(Html.EJ().Grid<object>("FlatGrid")
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

The above method generates the request header with custom header as follows.

![](Data-Binding_images/headers1.png) 

### Adding Custom Request Headers to every Request using pre-request callback **beforeSend**

You can set the custom headers using pre-request callback **beforeSend** as follows. The **setRequestHeader** method can be used to modify the **XMLHTTPRequest**.

{% highlight C# %}

    public static List<OrderDetails> order = new List<OrderDetails>();
    public ActionResult DataSource()
    {
        int code = 10000;
        for (int i = 1; i < 10; i++)
        {
            order.Add(new OrderDetails(code + 1, "ALFKI", i + 0, 2.3 * i, "Berlin"));
            order.Add(new OrderDetails(code + 2, "ANATR", i + 2, 3.3 * i, "Madrid"));
            order.Add(new OrderDetails(code + 3, "ANTON", i + 1, 4.3 * i, "Cholchester"));
            order.Add(new OrderDetails(code + 4, "BLONP", i + 3, 5.3 * i, "Marseille"));
            order.Add(new OrderDetails(code + 5, "BOLID", i + 4, 6.3 * i, "Tsawassen"));
            code += 5;
        }
        var list = order.ToList();
        DataResult result = new DataResult();
        result.result = list;
        result.count = list.Count;
        return Json(result, JsonRequestBehavior.AllowGet);
    }
    public class DataResult
    {

        public IEnumerable<OrderDetails> result { get; set; }

        public int count { get; set; }

    }
    public class OrderDetails
    {
        public OrderDetails()
        {

        }
        public OrderDetails(int OrderID, string CustomerId, int EmployeeId, double Freight, string ShipCity)
        {
            this.OrderID = OrderID;
            this.CustomerID = CustomerId;
            this.EmployeeID = EmployeeId;
            this.Freight = Freight;
            this.ShipCity = ShipCity;
        }

        public int? OrderID { get; set; }
        public string CustomerID { get; set; }
        public int? EmployeeID { get; set; }
        public double? Freight { get; set; }
        public string ShipCity { get; set; }
    }

{% endhighlight %}

{% highlight CSHTML %}

    @(Html.EJ().DataManager("FlatData").URL("DataSource"))

    @(Html.EJ().Grid<object>("FlatGrid")

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


{% highlight javascript %}

    <script type="text/javascript">
        setTimeout(function () {
            var customAdaptor = new ej.UrlAdaptor().extend({
                beforeSend: function (request, settings) {
                    settings.setRequestHeader("myData1", "Syncfusion");
                    settings.setRequestHeader("myData2", 23243);
                }
            });
            window.FlatData.adaptor = new customAdaptor();
            var gridObj = $("#FlatGrid").ejGrid("instance");
            gridObj.dataSource(window.FlatData.executeQuery(new ej.Query().take(7)));

        }, 3000);
        
    </script>
  
{% endhighlight %}

The above method generates the request header with custom header as follows.

![](Data-Binding_images/headers3.png)

### Adding Custom Request Headers using **addParams** method

You can use the addParams method of ej.Query class, to add custom parameter to the data request.

{% highlight CSHTML %}

   @Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/").Adaptor(AdaptorType.ODataAdaptor).CrossDomain(true)


    @(Html.EJ().Grid<object>("FlatGrid")
            .DataManagerID("FlatData")
            .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).take(5).addParams('Syncfusion', true)")
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

The custom parameter will be passed along with the data request of the grid as follows.

![](Data-Binding_images/headers2.png) 

## Cross domain & JSONP

The **DataManager** contains support for creating cross domain request, you can achieve this by using `crossDomain` and `jsonp` property of the **DataManager**. The following code example illustrate on how to create cross domain request. 

{% highlight CSHTML %}

    @(Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/").CrossDomain(true))

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

Result of above code example is illustrated as follows.

![](Data-Binding_images/Data-Binding_img12.png)

Cross domain          
{:.caption}

## HTML Table

Other than **JSON** and **Remote** datasource, the **DataManager** can also fetch and use data from **HTML** element. You can achieve this by using the **table** property of the **DataManager**. The **DataManager** can fetch data from the **HTML** table element.

Refer to the following code example for the **HTML** element binding using **DataManager**.

{% highlight CSHTML %}

    <script id="_table1" type="text/template">
    <table id="datasource" style="display:none">
        <thead>
            <tr>
                <th>OrderID</th>
                <th>EmployeeID</th>
                <th>CustomerID</th>
            </tr>
        </thead>
        <tbody>
            <tr><td>10248</td><td>VINET</td><td>5</td></tr>
            <tr><td>10249</td><td>TOMSP</td><td>6</td></tr>
            <tr><td>10250</td><td>HANAR</td><td>4</td></tr>
            <tr><td>10251</td><td>VICTE</td><td>3</td></tr>
            <tr><td>10252</td><td>SUPRD</td><td>4</td></tr>
        </tbody>
    </table>
</script>

@(Html.EJ().DataManager("FlatData").Table("#_table1"))


@(Html.EJ().Grid<object>("FlatGrid")
        .DataManagerID("FlatData")
        .Columns(col =>
        {
            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
        })

)
{% endhighlight %}

The result of the above code example is illustrated as follows.

![](Data-Binding_images/Data-Binding_img13.png)

HTML Table element binding
{:.caption}