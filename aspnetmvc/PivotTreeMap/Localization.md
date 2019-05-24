---
layout: post
title: Localization | PivotTreeMap | ASP.NET MVC | Syncfusion
description: This document illustrates that how to define localization with respective to the modes in ASP.NET MVC PivotTreeMap control 
platform: ejmvc
control: PivotTreeMap
documentation: ug
---

# Localization

## Localization and Globalization of Cube Info (Client Mode)

Content displayed within the PivotTreeMap control are obtained from the OLAP Cube. So following are the steps that needs to be done to get the localized and globalized Cube content.

* To get localized data from OLAP Cube, we need to set **"Locale Identifier"** in the connection string to a specific culture in the **"data"** property present inside **"DataSource"**. 

{% highlight CSHTML %}

//1036 refers to “fr-FR” culture.
<!--Create a tag which acts as a container for PivotTreeMap--> 
@Html.EJ().Pivot().PivotTreeMap("PivotTreeMap1").DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("[Customer].[Customer Geography]").Add(); }).Columns(columns => { columns.FieldName("[Date].[Fiscal]").Add(); }).Values(values => { values.Measures(measures => { measures.FieldName("[Measures].[Customer Count]").Add(); }).Axis(AxisName.Column).Add(); })
.Data("http://bi.syncfusion.com/olap/msmdpump.dll;Locale Identifier=1036;").Catalog("Adventure Works DW 2008 SE").Cube("Adventure Works")).IsResponsive(true)

<! --Tooltip labels can be localized here-->
<script id="tooltipTemplate" type="application/jsrender">
    <div style="background:White; color:black; font-size:12px; font-weight:normal; border: 1px solid #4D4D4D; white-space: nowrap;border-radius: 2px; margin-right: 25px; min-width: 110px;padding-right: 5px; padding-left: 5px; padding-bottom: 2px ;width: auto; height: auto;">
        <div>Measure(s) : {{:~Measures(#data)}}</div><div>Row : {{:~Row(#data)}}</div><div>Column : {{:~Column(#data)}}</div><div>Value : {{:~Value(#data)}}</div>
    </div>
</script>  

{% endhighlight %}

## Localization and Globalization of Cube Info (Server Mode)

Content displayed within the PivotTreeMap control are obtained from the OLAP Cube. So following are the steps that needs to be done to get the localized and globalized Cube content.

* To get the localized string based on different cultures, from OLAP Cube, we need to set **"Locale Identifier"** in the connection string to a specific culture. 
* To bind the globalized content in PivotTreeMap control, we need to set **"Culture"** and **"OverrideDefaultFormatStrings"** properties in "OlapDataManager" class to a specific culture. 
 
{% highlight c# %}

//1036 refers to “fr-FR” culture.
string connectionString = "Data Source=localhost; Initial Catalog=Adventure Works DW; Locale Identifier=1036;";
DataManager = new OlapDataManager(connectionString);
DataManager.Culture = new System.Globalization.CultureInfo(1036);
DataManager.OverrideDefaultFormatStrings = true;

{% endhighlight %}

![](Localization_images/localization.png) 

