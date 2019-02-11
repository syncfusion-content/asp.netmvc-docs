---
layout: post
title: Named Set | PivotGrid | ASP.NET MVC | Syncfusion
description: named set
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Named Set

Named set is a multidimensional expression (MDX) that returns a set of dimension members, which can be created by combining cube data, arithmetic operators, numbers and functions.

## Client Mode

You can bind the Named Sets in PivotGrid by setting it's unique name in the `FieldName` property either in row or column axis and `IsNamedSets` Boolean property to "true".

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("[Date].[Fiscal]").Add(); }).Columns(columns => { columns.FieldName("[Core Product Group]").IsNamedSets(true).Add(); }).Values(values => { values.Measures(measures => { measures.FieldName("[Measures].[Internet Sales Amount]").Add(); }).Axis(AxisName.Column).Add(); }).Data("http://bi.syncfusion.com/olap/msmdpump.dll").Catalog("Adventure Works DW 2008 SE").Cube("Adventure Works"))

{% endhighlight %}

![Named sets in ASP NET MVC pivot grid OLAP client mode](KPI_images/namedset.png)


## Server Mode

You can add Named Sets in the PivotGrid by using "NamedSetElement" Class in the OlapReport.

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

![Named sets in ASP NET MVC pivot grid OLAP server mode](KPI_images/servernamedset.png)

