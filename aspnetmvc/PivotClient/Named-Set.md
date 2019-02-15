---
layout: post
title: Named Set | PivotClient | ASP.NET MVC | Syncfusion
description: named set
platform: ejmvc
control: PivotClient
documentation: ug
---

# Named set

Named set is a multidimensional expression (MDX) that returns a set of dimension members, which can be created by combining the cube data, arithmetic operators, numbers, and functions. You can set the named set option in the pivot client by setting the `isNamedSets` property to true for client mode.

## Client mode

You can bind the named sets in the pivot client by setting it's unique name in the `FieldName` property either in row or column axis and `isNamedSets` Boolean property to true.

{% highlight html %}

@Html.EJ().Pivot().PivotClient("PivotClient1").DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("[Date].[Fiscal]").Add(); }).Columns(columns => { columns.FieldName("[Core Product Group]").IsNamedSets(true).Add(); }).Values(values => { values.Measures(measures => { measures.FieldName("[Measures].[Internet Sales Amount]").Add(); }).Axis(AxisName.Column).Add(); }).Data("https://bi.syncfusion.com/olap/msmdpump.dll").Catalog("Adventure Works DW 2008 SE").Cube("Adventure Works"))

{% endhighlight %}

## Server mode

You can add the named sets in the pivot client by using the NamedSetElement Class in the OLAP report.

{% highlight C# %}

OlapReport olapReport = new OlapReport();
olapReport.Name = "Customer Report";
olapReport.CurrentCubeName = "Adventure Works";

DimensionElement dimensionElementRow = new DimensionElement();
dimensionElementRow.Name = "Date";
dimensionElementRow.AddLevel("Fiscal", "Fiscal Year");

MeasureElements measureElementColumn = new MeasureElements();
measureElementColumn.Elements.Add(new MeasureElement {
Name = "Internet Sales Amount"
});

NamedSetElement dimensionElementColumn = new NamedSetElement();
dimensionElementColumn.Name = "Core Product Group";

olapReport.CategoricalElements.Add(dimensionElementColumn);
olapReport.CategoricalElements.Add(measureElementColumn);
olapReport.SeriesElements.Add(dimensionElementRow);

{% endhighlight %}

![Named set in ASP NET MVC pivot client OLAP mode](KPI_images/namedset.png)
