---
layout: post
title: IEnumerable-IQueryable | DataManager | ASP.NET MVC | Syncfusion
description: IEnumerable-IQueryable
platform: ejmvc
control: DataManager
documentation: ug
keywords : IEnumerable-IQueryable, IQueryable, IEnumerable

---

# IEnumerable

IEnumerable will execute **select** query on server side, load data in-memory on client side and then filter data.IEnumerable can be used for querying data from in-memory collections like List, Array etc.

## Data Binding

The **DataManager** contains a default support to bind data from a IEnumerable list to a control.  

Refer the below given code to bind data from IEnumerable list through datamanager to Grid

{% highlight C# %}

 public ActionResult DataSource(Syncfusion.JavaScript.DataManager dataManagerObj)
        {
            IEnumerable data = OrderRepository.GetAllRecords();
            var count = data.AsQueryable().Count();
            DataOperations ds = new DataOperations();
            data = ds.Execute(data, dataManagerObj);
            
            return Json(new { result=data , count = count }, JsonRequestBehavior.AllowGet);
        }

{% endhighlight %}

{% highlight CSHTML %}

    @(Html.EJ().DataManager("FlatData").URL("Home/DataSource").Adaptor(AdaptorType.UrlAdaptor))
    @(Html.EJ().Grid<object>("FlatGrid")
            .DataManagerID("FlatData") // pass the datamanager Id 
            .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).take(10)") // query to be executed
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
                col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
                col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
            })

    )
    )

{% endhighlight %}

The result of above code example is illustrated as follows.

![](IEnumerable-IQueryable_images/Databinding.png)

## Filtering Sorting and Searching with IEnumerable

We can perform filtering ,sorting and searching by passing the corresponding query through datamanager.

Refer the below given code to perform these actions

{% highlight CSHTML %}

    @(Html.EJ().DataManager("FlatData").URL("/Home/DataSource").Adaptor(AdaptorType.UrlAdaptor))
    @(Html.EJ().Grid<object>("FlatGrid")
            .DataManagerID("FlatData") // pass the datamanager Id 
            .Query("new ej.Query().sortByDesc('OrderID').sortBy('EmployeeID', 'ascending').search(4, 'EmployeeID').where('OrderID', 'lessThan', 10435, false).take(10)") // query to be executed
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
                col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
                col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
            })

)
    )

{% endhighlight %}

The result of above code example is illustrated as follows.

![](IEnumerable-IQueryable_images/Query.png)

## IQueryable

IQueryable is derived from IEnumerable and this executes select query on server side with all filters.IQueryable can be used for querying data from out-memory like remote database, service collections. 

## IQueryable support in DataManager

The DataManager now allows to execute a query against a specific data source by using the QueryableDataOperations. It can perform the IQueryable server side operation such as filtering, paging and sorting.

Refer the below code for performing these actions using IQueryable in Grid

{% highlight C# %}

     public ActionResult DataSource(Syncfusion.JavaScript.DataManager data)
        {
            IQueryable<OrdersView> datasource = new NorthwindDataContext().OrdersViews;
            if (data.Where != null) // for filtering
                datasource = QueryableDataOperations.PerformWhereFilter(datasource, data.Where, data.Where[0].Condition);
           if (data.Sorted != null)//for sorting
                datasource = QueryableDataOperations.PerformSorting(datasource, data.Sorted);
            if (data.Search != null)
                datasource = QueryableDataOperations.PerformSearching(datasource, data.Search);
            if (data.Skip >= 0)//for paging
               datasource = QueryableDataOperations.PerformSkip(datasource, data.Skip);
            if (data.Take > 0)//for paging
                datasource = QueryableDataOperations.PerformTake(datasource, data.Take);
            int count = datasource.Count();
            return Json(new { result = datasource.ToList(), count = count }, JsonRequestBehavior.AllowGet);      
        }

{% endhighlight %}

{% highlight CSHTML %}

   @(Html.EJ().Grid<OrdersView>("QueryableGrid")
        .Datasource(ds =>
        {
            ds.URL("/Home/DataSource").Adaptor(AdaptorType.UrlAdaptor);
        })
        .AllowScrolling()
        .AllowSorting()
        .AllowMultiSorting()
        .AllowFiltering()
        .AllowSearching()
                    .ToolbarSettings(set1 => set1.ShowToolbar(true).ToolbarItems(new List<ToolBarItems>() { ToolBarItems.Search }))

       .AllowPaging()
                    .SortSettings(sort => sort.SortedColumns(col => col.Field("ShipCity").Direction(SortOrder.Descending).Add()))

           .FilterSettings(filter => { filter.FilterType(FilterType.Menu); })
        .Columns(col =>
        {

            col.Field("OrderID").HeaderText("Order ID").Add();
            col.Field("CustomerID").HeaderText("Customer ID").AllowSorting().Add();
            col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();
            col.Field("ShipCity").HeaderText("Ship City").Add();
            col.Field("ShipName").HeaderText("Ship Name").Add();
        })
)

{% endhighlight %}

The result of above code example is illustrated as follows.

![](IEnumerable-IQueryable_images/IQueryable.png)