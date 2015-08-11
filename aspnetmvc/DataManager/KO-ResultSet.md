---
layout: post
title: KO-ResultSet
description: ko resultset
platform: ejmvc
control: DataManager
documentation: ug
---

# KO ResultSet

The DataManager contains a default method to subscribe the viewmodel properties as KO observable. This is done at the success of the executeQuery by using the getKnockoutModel. You can also provide computed properties to the viewmodel by using the getKnockoutModel.

The following code example illustrates how the model is made observable and updated.
{% highlight html %}
    @(Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc"))

    <div>

        <div id="Grid" data-bind="ejGrid: { dataSource: dataSource, allowPaging: true, pageSettings: { currentPage: currentPage, pageSize: 4 }}"></div>

    </div>



    <script src="~/Scripts/knockout-min.js"></script>

    <script src="~/Scripts/ej/ej.widget.ko.min.js"></script>

    <script type="text/javascript" class="jsScript">

        function onClick(arg) {

            var data = window.FlatData;

            window.employeeView = {

                dataSource: ko.observableArray(data),

            };

            ko.applyBindings(employeeView);

            var proxy = $("#MainContent_OrdersGrid").ejGrid("instance");

            proxy.refreshContent();

        }



    </script>

 </asp:Content>

{% endhighlight %}

The result of the above code example is illustrated as follows.

Before changing the model, EmployeeID 1 has FullName value as Nancy Davolio. After changing, the result is as follows.



![](KO-ResultSet_images/KO-ResultSet_img1.png)



