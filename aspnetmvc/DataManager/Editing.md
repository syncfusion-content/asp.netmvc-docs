---
layout: post
title: Editing
description: editing
platform: ejmvc
control: DataManager
documentation: ug
---

# Editing

Editing is a key feature in the DataManager and it provides support to add a new record, edit an existing record and remove a record from the table. Here, you can learn in detail how these operations are performed by using the DataManager.

## Batch Edit

Batch Editing is a unique feature, where requests to add, remove and change are handled altogether at a time rather than passing the request separately for each operation.
{% highlight js %}
@(Html.EJ().DataManager("FlatData").Adaptor(AdaptorType.JsonAdaptor))



@(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")

        .DataManagerID("FlatData")

        .Query("ej.Query().take(5)")

        .Columns(col =>

        {

            col.Field("EmployeeID").HeaderText("EmployeeID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("FirstName").HeaderText("FirstName").Width(80).Add();

            col.Field("LastName").HeaderText("LastName").TextAlign(TextAlign.Right).Width(75).Add();



        })

)
{% endhighlight  %}

## Employee ID
{% highlight js %}
<input id="EmployeeID" class="e-ejinputtext" type="text" value="" />

First Name

<input id="FirstName" class="e-ejinputtext" type="text" value="" />

Last Name 

<input id="LastName" class="e-ejinputtext" type="text" value="" />

@Html.EJ().Button("submit").Text("Add").ClientSideEvents(e => { e.Click("onClick"); })

@Html.EJ().Button("submit").Text("Change").ClientSideEvents(e => { e.Click("onClick"); })

@Html.EJ().Button("submit").Text("Delete").ClientSideEvents(e => { e.Click("onClick"); })

@Html.EJ().Button("submit").Text("Save All").ClientSideEvents(e => { e.Click("onClick"); })

    <script type="text/javascript" class="jsScript">

        window.changes = { changed: [], added: [], deleted: [] };



        function Click(args) {

            if (document.activeElement.value == "Change") {

                data = window.FlatData.executeLocal(ej.Query().where("EmployeeID", ej.FilterOperators.equal, parseInt($("#EmployeeID").val(), 10)));

                if (data.length) {

                    data[0].FirstName = $("#FirstName").val();

                    window.changes.changed.push(data);

                }

            }

            else if (document.activeElement.value == "Add") {

                window.changes.added.push({

                    EmployeeID: parseInt($("#EmployeeID").val(), 10),

                    FirstName: $("#FirstName").val(),

                    LastName: $("#LastName").val(),

                });

            }

            else if (document.activeElement.value == "Delete") {

                data = window.FlatData.executeLocal(ej.Query().where("EmployeeID", ej.FilterOperators.equal, parseInt($("#EmployeeID").val(), 10)));

                if (data.length)

                    window.changes.deleted.push(data[0]);

            }

            else {

                var obj = $("#MainContent_OrdersGrid").ejGrid("instance");

                window.FlatData.saveChanges(window.changes, "EmployeeID");

                (window.FlatData.dataSource.json);

            }

        }

    </script>

</asp:Content>

{% endhighlight %}

Result of the above code example is illustrated as follows.

![](Editing_images/Editing_img1.png)



## Insert

The insert method of the DataManager is used to add a new record to the table. The JSON data is passed as a parameter to the insert method that is inserted to the data source of the DataManager.

{% highlight js %}
@(Html.EJ().DataManager("FlatData").Adaptor(AdaptorType.JsonAdaptor))

@Html.EJ().Button("submit").Text("Insert").ClientSideEvents(e => { e.Click("onClick"); })

@(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")

        .DataManagerID("FlatData")

        .Query("ej.Query().take(5)")

        .Columns(col =>

        {

            col.Field("EmployeeID").HeaderText("EmployeeID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("FirstName").HeaderText("FirstName").Width(80).Add();

            col.Field("LastName").HeaderText("LastName").TextAlign(TextAlign.Right).Width(75).Add();



        })

)
{% endhighlight  %}
{% highlight js %}
    <script type="text/javascript" class="jsScript">

        function onClick(e) {

            var record = { OrderID: 10253, CustomerID: "STRPQ", EmployeeID: 4, ShipCity: "Reims", Freight:23.1 };

            window.FlatData.insert(record)

            var obj = $("#MainContent_OrdersGrid").ejGrid("instance");

            obj.dataSource(window.FlatData.executeLocal(ej.Query().sortByDesc("OrderID")));



        }

    </script>

{% endhighlight  %}

Result of the above code example is illustrated as follows.

![](Editing_images/Editing_img2.png)



## Update

The update method is used to update the modified changes made to a record in the data source of the DataManager.
{% highlight js %}
@(Html.EJ().DataManager("FlatData").Adaptor(AdaptorType.JsonAdaptor))

@Html.EJ().Button("submit").Text("Update").ClientSideEvents(e => { e.Click("onClick"); })

@(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")

        .DataManagerID("FlatData")

        .Query("ej.Query().take(5)")

        .Columns(col =>

        {

            col.Field("EmployeeID").HeaderText("EmployeeID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("FirstName").HeaderText("FirstName").Width(80).Add();

            col.Field("LastName").HeaderText("LastName").TextAlign(TextAlign.Right).Width(75).Add();



        })

)

{% endhighlight %}
{% highlight js %}
    <script type="text/javascript" class="jsScript">

        function onClick(e) {

            var record = { OrderID: 10045, CustomerID: "STRQP", EmployeeID: 4, ShipCity: "Reims", Freight: 23.1 };

            window.FlatData.update("OrderID", record, window.FlatData.dataSource.json)

            var obj = $("#MainContent_OrdersGrid").ejGrid("instance");

          obj.dataSource(window.FlatData.executeLocal(ej.Query().sortByDesc("OrderID")));



        }

    </script>


{% endhighlight  %}
Result of the above code example is illustrated as follows.

![](Editing_images/Editing_img3.png)



## Remove

The remove method is used to delete a record from the data source of the DataManager.
{% highlight js %}
@(Html.EJ().DataManager("FlatData").Adaptor(AdaptorType.JsonAdaptor))

@Html.EJ().Button("submit").Text("Update").ClientSideEvents(e => { e.Click("onClick"); })

@(Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")

        .DataManagerID("FlatData")

        .Query("ej.Query().take(5)")

        .Columns(col =>

        {

            col.Field("EmployeeID").HeaderText("EmployeeID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();

            col.Field("FirstName").HeaderText("FirstName").Width(80).Add();

            col.Field("LastName").HeaderText("LastName").TextAlign(TextAlign.Right).Width(75).Add();



        })

)
{% endhighlight %}

{% highlight js %}
<script type="text/javascript" class="jsScript">

        function onClick(e) {

            var record = { OrderID: 10046, CustomerID: "STRQP", EmployeeID: 4, ShipCity: "Reims", Freight: 23.1 };

            window.FlatData.remove("OrderID", record, window.FlatData.dataSource.json)

            var obj = $("#MainContent_OrdersGrid").ejGrid("instance");

          obj.dataSource(window.FlatData.executeLocal(ej.Query().sortByDesc("OrderID")));



        }

    </script>

{% endhighlight  %}

Result of the above code example is illustrated as follows.

![](Editing_images/Editing_img4.png)



