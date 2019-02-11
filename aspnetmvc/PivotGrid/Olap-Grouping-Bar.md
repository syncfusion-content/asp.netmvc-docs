---
layout: post
title: Grouping Bar | PivotGrid | ASP.NET MVC | Syncfusion
description: grouping bar
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Grouping Bar

## Initialization

Grouping Bar allows user to dynamically alter the report by filter and remove operations in the PivotGrid control. Based on the OLAP datasource and report bound to the PivotGrid control, Grouping Bar will be automatically populated. You can enable Grouping Bar option in PivotGrid by setting the `EnableGroupingBar` property to true.

### Client Mode

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableGroupingBar(true).DataSource(dataSource => dataSource.Rows(rows=>{rows.FieldName("[Date].[Fiscal]").Add();}).Columns(columns=>{columns.FieldName("[Customer].[Customer Geography]").Add();}).Values(values => { values.Measures(measures => { measures.FieldName("[Measures].[Internet Sales Amount]").Add(); }).Axis(AxisName.Column).Add();}).Data("http://bi.syncfusion.com/olap/msmdpump.dll").Catalog("Adventure Works DW 2008 SE").Cube("Adventure Works"))

{% endhighlight %}

![Grouping bar in ASP NET MVC pivot grid OLAP client mode](Grouping-Bar_images/OlapGroupingbar.png)

### Server Mode

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("/OLAPService")).EnableGroupingBar(true)

{% endhighlight %}

![Grouping bar in ASP NET MVC pivot grid OLAP server mode](Grouping-Bar_images/OlapServerModeGB.png)

## Drag and Drop

You can alter the report on fly through drag-and-drop operation.

![Drag and drop in ASP NET MVC pivot grid control](Grouping-Bar_images/GBar_Olap.png)

## Context Menu

You can also alter the report by using context menu.

![Context menu in ASP NET MVC pivot grid control](Grouping-Bar_images/CMenu_Olap.png)

## Searching Values

Search option available in Grouping Bar allows you to search a specific value that needs to be filtered from the list of values inside the filter pop-up window.

![Filtering icon in grouping bar of ASP NET MVC pivot grid control](Grouping-Bar_images/OlapFilterIcon.png)

![Searching in member editor dialog of ASP NET MVC pivot grid control](Grouping-Bar_images/olapclientsearching.png)

## Filtering Values

Filtering option available in Grouping Bar allows you to select a specific set of values that needs to be displayed in the PivotGrid control. At least one value needed to be in checked state while filtering otherwise “Ok” button will be disabled.

![Filtering icon in grouping bar of ASP NET MVC pivot grid control](Grouping-Bar_images/OlapFiltericon.png)

![Filtering in member editor dialog of ASP NET MVC pivot grid control](Grouping-Bar_images/OlapFiltering.png)

## Removing Field

Remove option available in the Grouping Bar allows you to completely remove a specific field from the PivotGrid control. Remove operation can be either achieved by clicking remove icon available inside each field or by dragging and dropping field out of Grouping Bar region.

![Remove icon in grouping bar of ASP NET MVC pivot grid control](Grouping-Bar_images/OlapRemoveicon.png)

![Removed items in ASP NET MVC pivot grid control](Grouping-Bar_images/OlapRemove.png)

