---
layout: post
title: Named Set | PivotTreeMap | ASP.NET MVC | Syncfusion
description: named set
platform: ejmvc
control: PivotTreeMap
documentation: ug
---

# Named Sets

Named Sets is a multidimensional expression (MDX) that returns a set of dimension members, which can be created by combining cube data, arithmetic operators, numbers and functions.

## Client Mode

You can bind the Named Sets in PivotTreeMap by setting it's unique name in the `fieldName` property either in row or column axis and `isNamedSets` boolean property to "true".

{% highlight js %}

<!--Create a tag which acts as a container for PivotTreeMap--> 
@Html.EJ().Pivot().PivotTreeMap("PivotTreeMap1").DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("[Core Product Group]").IsNamedSets(true).Add(); }).Columns(columns => { columns.FieldName("[Customer].[Customer Geography]").Add(); }).Values(values => { values.Measures(measures => { measures.FieldName("[Measures].[Internet Sales Amount]").Add(); }).Axis(AxisName.Column).Add(); })
.Data("http://bi.syncfusion.com/olap/msmdpump.dll").Catalog("Adventure Works DW 2008 SE").Cube("Adventure Works"))

<! --Tooltip labels can be localized here-->
<script id="tooltipTemplate" type="application/jsrender">
    <div style="background:White; color:black; font-size:12px; font-weight:normal; border: 1px solid #4D4D4D; white-space: nowrap;border-radius: 2px; margin-right: 25px; min-width: 110px;padding-right: 5px; padding-left: 5px; padding-bottom: 2px ;width: auto; height: auto;">
        <div>Measure(s) : {{:~Measures(#data)}}</div><div>Row : {{:~Row(#data)}}</div><div>Column : {{:~Column(#data)}}</div><div>Value : {{:~Value(#data)}}</div>
    </div>
</script>  

{% endhighlight %}

![](NamedSets_images/namedset.png)


## Server Mode

You can add Named Sets in the PivotTreeMap by using `NamedSetElement` class in the OlapReport.

{% highlight C# %}

OlapReport olapReport = new OlapReport(); 
olapReport.Name = "Customer Report"; 
olapReport.CurrentCubeName = "Adventure Works"; 

DimensionElement dimensionElementColumn = new DimensionElement(); 
dimensionElementColumn.Name = "Customer"; 
dimensionElementColumn.AddLevel("Customer Geography", "Country ");
 
MeasureElements measureElementColumn = new MeasureElements(); 
measureElementColumn.Elements.Add(new MeasureElement { 
Name = "Internet Sales Amount" 
}); 

NamedSetElement dimensionElementRow = new NamedSetElement(); 
dimensionElementRow.Name = "Core Product Group"; 

olapReport.CategoricalElements.Add(dimensionElementColumn); 
olapReport.CategoricalElements.Add(measureElementColumn); 
olapReport.SeriesElements.Add(dimensionElementRow);

{% endhighlight %}

![](NamedSets_images/servernamedset.png)


