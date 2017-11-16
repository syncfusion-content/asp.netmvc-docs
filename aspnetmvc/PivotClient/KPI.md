---
layout: post
title: Key-Performance-Indicator-KPI | PivotClient | ASP.NET MVC | Syncfusion
description: key performance indicator (KPI)
platform: ejmvc
control: PivotClient
documentation: ug
---

# KPI

Key Performance Indicators (KPIs) are business metric that help to figure out the progress of an enterprise in meeting its business goals.

The different indicators available in KPI are:

* KPI Value: A physical measure or a calculated measure.
* KPI Goal: Defines the target for the measure.
* KPI Status: Evaluates the current status of the value compared to the goal.
* KPI Trend: Evaluate the current trend of the value compared to the goal.

The **“KpiElements”** class in OLAP Base library holds the KPI name and when its object is added to an OlapReport, you can view the resultant information in PivotClient.

To enable KPI option set the property `EnableKPI` to `true`.

## Client Mode

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotClient("PivotClient1").DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("[Date].[Fiscal]").Add(); }).Columns(columns => { columns.FieldName("[Product].[Product Categories]").Add(); }).Values(values => { values.Measures(measures => { measures.FieldName("[Measures].[Internet Sales Amount]").Add(); measures.FieldName("[Measures].[Growth in Customer Base Trend]").Add(); measures.FieldName("[Measures].[Growth in Customer Base Status]").Add(); }).Axis(AxisName.Column).Add(); }).Data("http://bi.syncfusion.com/olap/msmdpump.dll").Catalog("Adventure Works DW 2008 SE").Cube("Adventure Works")).EnableKPI(true)

{% endhighlight %}

![](KPI_images/clientmode-kpi.png)

## Server Mode

### Client side property declaration

{% highlight cshtml %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").Url(Url.Content("/OlapClient")).Title("OLAP Browser").EnableKPI(true)

{% endhighlight %}

### Framing OlapReport with KPI Elements

{% highlight c# %}

OlapReport olapReport = new OlapReport();
olapReport.Name = "KPI Report";
olapReport.CurrentCubeName = "Adventure Works";

MeasureElements measureElementColumn = new MeasureElements();
measureElementColumn.Elements.Add(new MeasureElement {
    Name = "Gross Profit"
});

DimensionElement dimensionElementRow = new DimensionElement();
dimensionElementRow.Name = "Date";
dimensionElementRow.AddLevel("Fiscal", "Fiscal Year");

KpiElements kpiElement = new KpiElements();
kpiElement.Elements.Add(new KpiElement {
    Name = "Revenue", ShowKPIStatus = true, ShowKPIGoal = false, ShowKPITrend = true, ShowKPIValue = true
});

olapReport.CategoricalElements.Add(kpiElement);
olapReport.CategoricalElements.Add(measureElementColumn);
olapReport.SeriesElements.Add(dimensionElementRow);

{% endhighlight %}

![](KPI_images/KPI.png)

