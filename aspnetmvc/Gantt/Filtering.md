---
layout: post
title: Filtering | Gantt | ASP.NET MVC | Syncfusion
description: filtering
platform: ejmvc
control: Gantt
documentation: ug
---

# Filtering

Filtering helps to view specific or related records from data source which meets a given filtering criteria. The `FilterSettings` property in Gantt is used to set the filtering criteria at load time.

## Filter columns at initial load
It is possible to filter one or more columns at initial load by providing the `Field`, `Value`,`Predicate` and `Operator` to the `FilteredColumns` property. The following code example explains how to filter a column on initial load.

{% highlight CSHTML %}

@(Html.EJ().Gantt("GanttContainer")
.FilterSettings(filter =>
{
	filter.FilteredColumns(filtered =>
		{
			filtered.Value("plan").Field("taskName").Predicate("and").Operator(FilterOperatorType.StartsWith).Add();
		});
})
)@(Html.EJ().ScriptManager())

{% endhighlight %}

The output of the filtering applied for a specific column is as follows.

![](Filtering_images/Filtering_img1.png)

## Filtering a specific column by public method

It is possible to filter columns dynamically by using the [`filterColumn`](/api/js/ejgantt#methods:filtercolumn "filterColumn(fieldName, filterOperator, filterValue, [predicate], [matchCase])") public method. 
The below code snippet explains the above behavior.

{% highlight js %}

<button id="filterColumn">Filter Column</button>
@(Html.EJ().Gantt("GanttContainer")
   //..
)@(Html.EJ().ScriptManager())
<script type="text/javascript">

$("#filterColumn").click(function (args) {
       var obj = $("#GanttContainer").ejGantt("instance");
       obj.filterColumn("taskName", "startswith", "plan");
})
</script>

{% endhighlight %}


## Clearing the filter applied to Gantt

You can clear all the filtering condition done in the Gantt by using the [`clearFilter`](/api/js/ejgantt#methods:clearfilter "clearFilter()") public method. 
The below code snippet explains the above behavior.

{% highlight js %}

<button id="clearFilter">Clear Filter</button>

@(Html.EJ().Gantt("GanttContainer")
   //..
)@(Html.EJ().ScriptManager())

<script type="text/javascript">

$("#clearFilter").click(function (args) {
       var obj = $("#GanttContainer").ejGantt("instance");
       obj.clearFilter();
})
</script>

{% endhighlight %}