---
layout: post
title: Summary with Grid widget for EJMVC
description: How to enable summary and its functionalities
platform: ejmvc
control: Grid
documentation: ug
---

# Summary 

Summary rows visibility can be controlled by the `ShowSummary` property and it can be added to grid by using the `SummaryRow` array property. The following code sample describes this.


{% tabs %}

{% highlight razor %}

@(Html.EJ().Grid<OrdersView>("Summary")
	.Datasource((IEnumerable<object>)ViewBag.datasource)
	.ShowSummary()
	.SummaryRow(row =>
	{
		row.Title("Sum").SummaryColumns(col => { col.SummaryType(SummaryType.Sum).Format("{0:C}").DisplayColumn("Freight").DataMember("Freight").Add(); }).Add();
	})
	.AllowPaging()
	.Columns(col =>
	{
		col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(80).Add();
		col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(80).Add();
		col.Field("ShipCity").HeaderText("Ship City").Width(90).Add();
		col.Field("ShipCountry").HeaderText("Ship Country").Width(100).Add();
		col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(80).Format("{0:C}").Add();

	})
)

{% endhighlight %}
{% highlight C# %}

namespace SyncfusionMvcApplication3.Controllers

{
    public class HomeController : Controller
    {
        public ActionResult Index()
        {
            var DataSource = new NorthwindDataContext().OrdersViews.ToList();
            ViewBag.datasource = DataSource;
            return View();

        }
    }
}


{% endhighlight  %}
{% endtabs %} 

![](Summary_images/summaryGrid_img1.png)

## Supported aggregates 

Following are the supported list of aggregates: 

* Sum
* Average
* Maximum
* Minimum
* False Count
* True Count

### Sum, average, maximum and minimum


Summaries with `Sum`,`average`,`maximum` and `minimum` aggregate can be defined by using the `SummaryType` in `SummaryColumns` collections. These aggregate are used in the `Number` column.

{% tabs %}

{% highlight razor %}

@(Html.EJ().Grid<OrdersView>("Summary")
	.Datasource((IEnumerable<object>)ViewBag.datasource)
	.ShowSummary()
	.SummaryRow(row =>
	{
		row.Title("Sum").SummaryColumns(col => { col.SummaryType(SummaryType.Sum).Format("{0:C}").DisplayColumn("Freight").DataMember("Freight").Add(); }).Add();
		row.Title("Average").SummaryColumns(col => { col.SummaryType(SummaryType.Average).Format("{0:C}").DisplayColumn("Freight").DataMember("Freight").Add(); }).Add();
		row.Title("Maximum").SummaryColumns(col => { col.SummaryType(SummaryType.Maximum).Format("{0:C}").DisplayColumn("Freight").DataMember("Freight").Add(); }).Add();
		row.Title("Minimum").SummaryColumns(col => { col.SummaryType(SummaryType.Minimum).Format("{0:C}").DisplayColumn("Freight").DataMember("Freight").Add(); }).Add();
	  })
	.AllowPaging()
	.Columns(col =>
	{
		col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(80).Add();
		col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(80).Add();
		col.Field("ShipCity").HeaderText("Ship City").Width(90).Add();
		col.Field("ShipCountry").HeaderText("Ship Country").Width(100).Add();
		col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(80).Format("{0:C}").Add();

	})
)

{% endhighlight %}
{% highlight C# %}

namespace SyncfusionMvcApplication3.Controllers

{
    public class HomeController : Controller
    {
        public ActionResult Index()
        {
            var DataSource = new NorthwindDataContext().OrdersViews.ToList();
            ViewBag.datasource = DataSource;
            return View();

        }
    }
}

{% endhighlight  %}
{% endtabs %} 

![](Summary_images/summaryGrid_img2.png)

### True and False count 

Summaries with `True` and `False` count aggregate can be defined by using the `SummaryType`,`SummaryColumns` collections. The `True` and `False` count aggregates are used for boolean columns.

{% tabs %}

{% highlight razor %}

@(Html.EJ().Grid<OrdersView>("Summary")
	.Datasource((IEnumerable<object>)ViewBag.datasource)
	.ShowSummary()
	.SummaryRow(row =>
	{
		row.Title("False Count").SummaryColumns(col => { col.SummaryType(SummaryType.FalseCount).DisplayColumn("Verified").DataMember("Verified").Add(); }).Add();
		row.Title("True Count").SummaryColumns(col => { col.SummaryType(SummaryType.TrueCount).DisplayColumn("Verified").DataMember("Verified").Add(); }).Add();
		
	})  
	.AllowPaging()
	.Columns(col =>
	{
		col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(80).Add();
		col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(80).Add();
		col.Field("ShipCity").HeaderText("Ship City").Width(90).Add();
		col.Field("ShipCountry").HeaderText("Ship Country").Width(100).Add();
		col.Field("Verified").HeaderText("Verified").Width(80).Add();

	})
)

{% endhighlight %}
{% highlight C# %}

namespace SyncfusionMvcApplication3.Controllers

{
    public class HomeController : Controller
    {
        public ActionResult Index()
        {
            var DataSource = new NorthwindDataContext().OrdersViews.ToList();
            ViewBag.datasource = DataSource;
            return View();

        }
    }
}

{% endhighlight  %}
{% endtabs %} 


![](Summary_images/summaryGrid_img3.png)


## Custom summary

Custom summary can be used to create summary values based on your required custom logic and calculations. To enable custom summary, the `SummaryType` should be `Custom` and `CustomSummaryValue` property need to defined as function. In the `CustomSummaryValue` function, you need to use the grid instance to access `model.dataSource` and `model.currentViewData`. After the custom calculation, the returned value will be displayed in corresponding summary cell.
{% tabs %}

{% highlight razor %}

@(Html.EJ().Grid<OrdersView>("Summary")
	.Datasource((IEnumerable<object>)ViewBag.datasource)
	.ShowSummary()
	.SummaryRow(row =>
	{
		 row.Title("Currency").SummaryColumns(col => { col.SummaryType(SummaryType.Custom).CustomSummaryValue("currency").DisplayColumn("Freight").Format("{0:C2}").Add(); }).Add(););
		
		
	})  
	.AllowPaging()
	.Columns(col =>
	{
		col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(70).Add();
		col.Field("CustomerID").HeaderText("CustomerID").TextAlign(TextAlign.Right).Width(70).Add();
		col.Field("ShipCity").HeaderText("Ship City").Width(70).Add();
		col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(70).Add();
		col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(70).Format("{0:C}").Add();

	})
)

{% endhighlight %}
{% highlight C# %}

namespace SyncfusionMvcApplication3.Controllers

{
    public class HomeController : Controller
    {
        public ActionResult Index()
        {
            var DataSource = new NorthwindDataContext().OrdersViews.ToList();
            ViewBag.datasource = DataSource;
            return View();

        }
    }
}

{% endhighlight  %}

{% highlight js %}

<script type="text/javascript">
  function currency() {
      //to get grid instance
      var gridObj = $("#Grid").ejGrid("instance");
      //ej.sum is aggregate to add data's of freight from datasource
      return ej.sum(gridObj.model.dataSource, "Freight");
  }
  </script>

{% endhighlight %}

{% endtabs %} 

![](Summary_images/summaryGrid_img4.png)

## Group summary

Group summary is used to summarize values of a particular column based on group and it shows at bottom of each group. To enable group Summary for particular group, you need to define the `ShowTotalSummary` as false.

{% tabs %}

{% highlight razor %}

@(Html.EJ().Grid<OrdersView>("Summary")
	.Datasource((IEnumerable<object>)ViewBag.datasource)
	.ShowSummary()
	.SummaryRow(row =>
	{
		row.ShowTotalSummary(false).SummaryColumns(col => 
		{ 
			col.SummaryType(SummaryType.Sum)
			.Format("{0:C2}")
			.DisplayColumn("Freight")
			.DataMember("Freight")
			.Prefix("Sum = ")
			.Add(); 
		}).Add();
	})
	.AllowPaging()
	.AllowSorting()
	.AllowGrouping()
	.GroupSettings(group => { group.GroupedColumns(col => { col.Add("CustomerID"); }); })
	.Columns(col =>
	{
		col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).Width(80).Add();
		col.Field("CustomerID").HeaderText("CustomerID").TextAlign(TextAlign.Right).Width(75).Add();
		col.Field("ShipCity").HeaderText("Ship City").Width(150).Add();	
		col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();		
		col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();

	})
)

{% endhighlight %}
{% highlight C# %}

namespace SyncfusionMvcApplication3.Controllers

{
    public class HomeController : Controller
    {
        public ActionResult Index()
        {
            var DataSource = new NorthwindDataContext().OrdersViews.ToList();
            ViewBag.datasource = DataSource;
            return View();

        }
    }
}

{% endhighlight %}

{% endtabs %}

![](Summary_images/summaryGrid_img5.png)


W> Minimum one column should be grouped to show the summary details.

## Group caption summary

To show summaries in each group's caption row, particular summary row should have the `ShowTotalSummary` as `false` and the `ShowCaptionSummary` as `true`.
{% tabs %}

{% highlight razor %}

@(Html.EJ().Grid<OrdersView>("Summary")
	.Datasource((IEnumerable<object>)ViewBag.datasource)
	.ShowSummary()
	.SummaryRow(row =>
	{
		row.ShowTotalSummary(false).SummaryColumns(col => 
		{ 
			col.SummaryType(SummaryType.Average)
			.Format("{0:C2}")
			.DisplayColumn("Freight")
			.DataMember("Freight")
			.Prefix("Average = ")
			.Add(); 
		}).Add();
	})
	.AllowPaging()
	.AllowSorting()
	.AllowGrouping()
	.GroupSettings(group => { group.GroupedColumns(col => { col.Add("EmployeeID"); }); })
	.Columns(col =>
	{
		col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).Width(80).Add();
		col.Field("CustomerID").HeaderText("CustomerID").TextAlign(TextAlign.Right).Width(75).Add();
		col.Field("ShipCity").HeaderText("Ship City").Width(150).Add();	
		col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();		
		col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();

	})
)

{% endhighlight %}
{% highlight C# %}

namespace SyncfusionMvcApplication3.Controllers

{
    public class HomeController : Controller
    {
        public ActionResult Index()
        {
            var DataSource = new NorthwindDataContext().OrdersViews.ToList();
            ViewBag.datasource = DataSource;
            return View();

        }
    }
}

{% endhighlight %}

{% endtabs %}

![](Summary_images/summaryGrid_img6.png)


W> Minimum one column should be grouped to the show summary details.

## Summary template

Using the `Template` property of `SummaryColumns` you can render any type of JsRender templates or customizing the summary value.

The following code example describes the previous behavior.

{% tabs %}

{% highlight razor %}

@(Html.EJ().Grid<OrdersView>("Summary")
	.Datasource((IEnumerable<object>)ViewBag.datasource)
	.ShowSummary()
	.SummaryRow(row =>
	{
		row.ShowTotalSummary(false).SummaryColumns(col => 
		{ 
			col.SummaryType(SummaryType.Average)
			.Format("{0:C2}")
			.DisplayColumn("Freight")
			.DataMember("Freight")
			.Template("#templateData")
			.Add(); 
		}).Add();
	})
	
	.Columns(col =>
	{
		col.Field("OrderID").Add();
		col.Field("EmployeeID").Add();		
		col.Field("Freight").Format("{0:C}").Add();
	})
)

{% endhighlight %}
{% highlight C# %}

namespace SyncfusionMvcApplication3.Controllers

{
    public class HomeController : Controller
    {
        public ActionResult Index()
        {
            var DataSource = new NorthwindDataContext().OrdersViews.Take(5).ToList();
            ViewBag.datasource = DataSource;
            return View();

        }
    }
}

{% endhighlight %}
{% highlight js %}

<script id="templateData" type="text/x-jsrender">
     Freight has Average of {{"{{"}}:summaryValue{{"}}"}} in  dollars
</script>

{% endhighlight %}

{% endtabs %}

The following output is displayed as a result of the previous code example.

![](Summary_images/summaryGrid_img9.png)

## Format

To format summary values, the `Format` property needs to be assigned in `SummaryColumns` collection object.  To know more about formatting options. Please refer to the [**globalize.js**](https://github.com/jquery/globalize/tree/v0.1.1#)

{% tabs %}

{% highlight razor %}

@(Html.EJ().Grid<OrdersView>("Summary")
	.Datasource((IEnumerable<object>)ViewBag.datasource)
	.ShowSummary()
	.SummaryRow(row =>
	{
		row.Title("Sum").SummaryColumns(col => { col.SummaryType(SummaryType.Sum).Format("{0:C}").DisplayColumn("Freight").DataMember("Freight").Add(); }).Add();
	})
	.AllowPaging()
	.Columns(col =>
	{
		col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(80).Add();
		col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(80).Add();
		col.Field("ShipCity").HeaderText("Ship City").Width(90).Add();
		col.Field("ShipCountry").HeaderText("Ship Country").Width(100).Add();
		col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(80).Format("{0:C}").Add();

	})
)

{% endhighlight %}
{% highlight C# %}

namespace SyncfusionMvcApplication3.Controllers

{
    public class HomeController : Controller
    {
        public ActionResult Index()
        {
            var DataSource = new NorthwindDataContext().OrdersViews.ToList();
            ViewBag.datasource = DataSource;
            return View();

        }
    }
}


{% endhighlight  %}
{% endtabs %} 

![](Summary_images/summaryGrid_img7.png)

## Handling aggregation in server-side

The Aggregation at server-side is handled by using the `aggregate` key. While using remote data, summary row must be handled by returning summary column datasource into the `aggregate` property of `result` object.

The following code example describes the previous behavior.

{% tabs %}

{% highlight razor %}

@(Html.EJ().Grid<OrdersView>("Summary")

  .Datasource(datasource => datasource.URL("/Grid/DataSource").Adaptor("UrlAdaptor"))
  .ShowSummary()
  .AllowPaging()
  .SummaryRow(row =>
   {
       row.ShowTotalSummary(true)
       row.Title("Sum").SummaryColumns(col ={
       col.SummaryType(SummaryType.Sum)
       .DisplayColumn("Freight")
       .DataMember("Freight")
       .Format("{0:C}")
       .Add();
    }).Add();
})

.Columns(col =>
{
   col.Field("OrderID").HeaderText("Order ID").Width(100).Add();
   col.Field("EmployeeID").HeaderText("Employee ID").Width(100).Add();
   col.Field("Freight").HeaderText("Freight").Width(100).Format("{0:C}").Add();
   col.Field("ShipCity").HeaderText("Ship City").Width(100).Add();
})
)
}

{% endhighlight %}

{% highlight c# %}

namespace MvcApplication4.Controllers
{
    public partial class GridController: Controller
       {
        public ActionResult GridFeatures()
           {

             ViewBag.dataSource = OrderRepository.GetAllRecords().ToList();
			 return View();
           }

     public ActionResult DataSource(DataManager dataManager)
       {
            IEnumerable DataSource = OrderRepository.GetAllRecords();
		    DataOperations dataOperations = new DataOperations();
            List<string> aggregateFields = new List<string>();
            if (dataManager.Aggregates != null)
             {
               for (var i = 0; i < dataManager.Aggregates.Count; i++)
               string.Add(dataManager.Aggregates[i].Field);
               result.aggregate = datasource.PerformSelect(DataSource, aggregateFields);
             }

       DataSource = datasource.PerformSkip(DataSource, dataManager.Skip);
       result.result = datasource.PerformTake(DataSource, dataManager.Take);
       result.count = DataSource.AsQueryable().Count();
       return Json(result, JsonRequestBehavior.AllowGet);

       }

    public class DataResult
       {
         public IEnumerable result { get; set; }
         public int count { get; set; }
         public IEnumerable aggregate { get; set; }
         public IEnumerable groupDs { get; set; }
       }

   }

}

{% endhighlight %}
{% endtabs %} 

The following output is displayed as a result of the previous code example.

![](Summary_images/summaryGrid_img8.png)





