---
layout: post
title: Number format  | PivotGrid | ASP.NET MVC | Syncfusion
description: number format 
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Number format 

I> This feature is applicable only for all modes.

Allows us to specify the required number format that PivotGrid should use in its values by setting the `format` option. Following number formats that are supported:

* number
* decimal
* currency
* percentage
* date
* time
* scientific
* accounting
* fraction

## Relational

### Client Mode

{% highlight CSHTML %}

 @Html.EJ().Pivot().PivotGrid("PivotGrid1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); rows.FieldName("State").FieldCaption("State").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); values.FieldName("Quantity").Format("decimal").Add(); }))
 
 {% endhighlight %}

![](Number-Format_images/RelationalClient.png)

### Server Mode

You can set Number Format through the property `Format`. You should specify the format to the property as per the MS standard notation.
 
private PivotReport BindDefaultData()
    {        
        PivotReport pivotSetting = new PivotReport();
        pivotSetting.PivotRows.Add(new PivotItem { FieldMappingName = "Product", FieldHeader = "Product", TotalHeader = "Total" });
        pivotSetting.PivotColumns.Add(new PivotItem { FieldMappingName = "Country", FieldHeader = "Country", TotalHeader = "Total" });
        //specify the format here
        pivotSetting.PivotCalculations.Add(new PivotComputationInfo { CalculationName = "Amount", Description = "Amount", FieldHeader = "Amount", FieldName = "Amount", Format = "E", SummaryType = Syncfusion.PivotAnalysis.Base.SummaryType.DoubleTotalSum });
        return pivotSetting;
    }

![](Number-Format_images/RelationalServer.png)

## OLAP

### Client Mode

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableGroupingBar(true).DataSource(dataSource => dataSource.Rows(rows=>{rows.FieldName("[Date].[Fiscal]").Add();}).Columns(columns=>{columns.FieldName("[Customer].[Customer Geography]").Add();}).Values(values => { values.Measures(measures => { measures.FieldName("[Measures].[Internet Sales Amount]").Format("percent").Add(); }).Axis(AxisName.Column).Add();}).Data("http://bi.syncfusion.com/olap/msmdpump.dll").Catalog("Adventure Works DW 2008 SE").Cube("Adventure Works"))

{% endhighlight %}

![](Number-Format_images/OlapClient.png)

### Server Mode

 OLAP server mode supports the following Number Formats in addition to the above mentioned formats. 
* General
* RoundTrip
* FixedPoint
* HexaDecimal

N> You can set the number format through the property `Format`

private OlapReport CreateOlapReport()
{
     OlapReport olapReport = new OlapReport();
     olapReport.CurrentCubeName = "Adventure Works";

     MeasureElements measureElement = new MeasureElements();
     measureElement.Elements.Add(new MeasureElement { UniqueName = "[Measures].[Internet Sales Amount]", Format = NumberFormat.FixedPoint }); //Specify the format here

     DimensionElement dimensionElementRow = new DimensionElement();
     dimensionElementRow.Name = "Date";
     dimensionElementRow.AddLevel("Fiscal", "Fiscal Year");

     DimensionElement dimensionElementColumn = new DimensionElement();
     dimensionElementColumn.Name = "Customer";
     dimensionElementColumn.AddLevel("Customer Geography", "Country");

     olapReport.SeriesElements.Add(dimensionElementRow);
     olapReport.CategoricalElements.Add(dimensionElementColumn);
     olapReport.CategoricalElements.Add(measureElement);

     return olapReport;
}

![](Number-Format_images/OlapServer.png)