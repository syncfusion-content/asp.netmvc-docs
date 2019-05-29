---
layout: post
title: Grouping Bar | PivotGrid | ASP.NET MVC | Syncfusion
description: This document illustrates that how to enable grouping bar feature and its functionalities in ASP.NET MVC PivotGrid control with relational mode
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Grouping Bar

## Initialization

Grouping Bar allows user to dynamically alter the report by filter, sort and  remove operations in the PivotGrid control. Based on the Relational datasource and report bound to the PivotGrid control, Grouping Bar will be automatically populated. You can enable Grouping Bar option in PivotGrid by setting the `EnableGroupingBar` property to true.

### Client Mode

{% highlight CSHTML %}

 @Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableGroupingBar(true).ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); rows.FieldName("State").FieldCaption("State").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Add(); values.FieldName("Quantity").Add(); }).Filters(filters => { filters.FieldName("Date").FieldCaption("Date").Add(); }))

 <script type="text/javascript">
        function onLoad(args) {
            args.model.dataSource.data = pivot_dataset;//Array of data
        }
</script>

{% endhighlight %}

![Grouping bar support in ASP NET MVC pivot grid control with relational client mode](Grouping-Bar_images/realtionalclientGB.png)


### Server Mode

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("/RelationalService")).EnableGroupingBar(true)

{% endhighlight %}

![Grouping bar support in ASP NET MVC pivot grid control with relational server mode](Grouping-Bar_images/groupingbar.png)

## Drag and Drop

You can alter the report on fly through drag-and-drop operation.

![Drag and drop in ASP NET MVC pivot grid control](Grouping-Bar_images/GBar_Rel.png)

## Context Menu

You can alter the report by using context menu.

![Context menu in ASP NET MVC pivot grid control](Grouping-Bar_images/CMenu_Rel.png)

## Searching Values

Search option available in Grouping Bar allows you to search a specific value that needs to be filtered from the list of values inside the filter pop-up window.

![Member editor dialog in ASP NET MVC pivot grid control](Grouping-Bar_images/filter.png)

![Searching in ASP NET MVC pivot grid control](Grouping-Bar_images/groupingbar-search.png)

## Filtering Values

Filtering option available in Grouping Bar allows you to select a specific set of values that needs to be displayed in the PivotGrid control. At least one value needed to be in checked state while filtering otherwise “Ok” button will be disabled.

![Member editor in ASP NET MVC pivot grid control](Grouping-Bar_images/FILTER.png)

![Filtering in ASP NET MVC pivot grid control](Grouping-Bar_images/FILTER1.png)

## Sorting Values

Sorting option available in Grouping Bar allows you to arrange headers either in ascending or descending order. Sorting option is applicable for fields available only in Row and Column region. By default, headers are sorted in ascending order. Regarding sorting indicator, up arrow denotes ascending order and down arrow denotes descending order.

![Sorting icon in ASP NET MVC pivot grid control](Grouping-Bar_images/sort.png)

![Sorted results in ASP NET MVC pivot grid control](Grouping-Bar_images/sort-grid.png)

## Removing Field

Remove option available in the Grouping Bar allows you to completely remove a specific field from the PivotGrid control. Remove operation can be either achieved by clicking remove icon available inside each field or by dragging and dropping field out of Grouping Bar region.

![Remove icon in ASP NET MVC pivot grid control](Grouping-Bar_images/remove.png)

![Removed items in ASP NET MVC pivot grid control](Grouping-Bar_images/remove-grid.png)

