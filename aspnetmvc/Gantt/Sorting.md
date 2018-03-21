---
layout: post
title: Sorting | Gantt | ASP.NET MVC | Syncfusion
description: sorting
platform: ejmvc
control: Gantt
documentation: ug
---

# Sorting

The Gantt control for JavaScript has built-in support for sorting one or more columns.

##Sorting Columns

Gantt allows the tasks to be sorted in ascending or descending order based on the selected column by enabling the `AllowSorting` option in Gantt control. The following code example shows you how to enable sorting in Gantt control.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
//..
.AllowSorting(true)
.Datasource(ViewBag.datasource)
)@(Html.EJ().ScriptManager())

{% endhighlight %}

## Multicolumn sorting

Gantt allows you to sort multiple columns by clicking the desired column headers while holding the `CTRL` key with `AllowMultiSorting` as `true` . The following code example shows you how to enable multicolumn sorting in Gantt control.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
//...
.AllowSorting(true)
.AllowMultiSorting(true)
.Datasource(ViewBag.datasource)
)@(Html.EJ().ScriptManager())
{% endhighlight %}

The following screenshot shows the output of multicolumn sorting in Gantt control.
![](Sorting_images/Sorting_img1.png)

Multicolumn Sorting
{:.caption}

## Sorting column on Gantt initialization

Gantt control can be rendered with sorted columns initially, this can be achieved by using `SortSettings` property. We can add columns which are sorted initially in `SortedColumns` collection. `SortedColumns` collection was defined with `Field` and `Direction` properties. The following code example shows how to add sorted column on Gantt initialization.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
//...
.AllowSorting(true)
.SortSettings(sort=>
	{
	 sort.SortedColumns(sc =>
		 sc.Field("taskName").Direction(SortOrder.Descending).Add());
	})
.Datasource(ViewBag.datasource)
)@(Html.EJ().ScriptManager())
{% endhighlight %}

The following screenshot shows the output of above code example.

![](Sorting_images/Sorting_img2.png)

## Sorting column dynamically

Columns in Gantt control can be sorted dynamically by using [`sortColumn`](/api/js/ejgantt#methods:sortcolumn "sortColumn(mappingName, columnSortDirection)") method. The following code example shows how to invoke the [`sortColumn`](/api/js/ejgantt#methods:sortcolumn "sortColumn(mappingName, columnSortDirection)") method on button click action.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
//...
.AllowSorting(true)
)@(Html.EJ().ScriptManager())

 <script type="text/javascript">
$("#sort_column").click(function(){ 
        $("#Gantt").ejGantt("sortColumn", "taskID", ej.sortOrder.Descending);
    });
 </script>
{% endhighlight %}

The following screenshot shows the output of above code example.

![](Sorting_images/Sorting_img3.png)

Before Sorting
{:.caption}

![](Sorting_images/Sorting_img4.png)

After Sorting
{:.caption}

N> when sorting a column using this method, previously sorted columns are cleared.

## Sorting multiple columns dynamically

Multiple columns in Gantt can be sorted dynamically by using `setModel` method with `sortSettings`property. The following code example shows how to use this method.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
//...
.AllowSorting(true)
.AllowMultiSorting(true)
.Datasource(ViewBag.datasource)
)@(Html.EJ().ScriptManager())

<script type="text/javascript">
$("#sort_column").click(function() {
        var sortedColumns = [
             { field: "taskID", direction: ej.sortOrder.Descending },
             { field: "taskName", direction: ej.sortOrder.Descending }
            ];
        var sortSettings = {
                sortedColumns: sortedColumns
            };
        var ganttObj = $("#Gantt").ejGantt("instance");
            ganttObj.setModel({ "sortSettings": sortSettings });
    });
 </script>
{% endhighlight %}

The following screenshot shows the output of the above code example.

![](Sorting_images/Sorting_img3.png)

Before Sorting
{:.caption}

![](Sorting_images/Sorting_img5.png)

After Sorting
{:.caption}
