---
layout: post
title: Calculated Field | PivotGrid | ASP.NET MVC | Syncfusion
description: This document illustrates that how to define calculated field through code-behind/UI in ASP.NET MVC PivotGrid control 
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Calculated Field

N> This feature is applicable only for Relational data source.

PivotGrid provides support to insert a new calculated field based on the existing Pivot Fields either through Calculated Field dialog or code behind.

### Through UI
To insert a new calculated Field, open the Calculated Field dialog using the Grouping Bar context menu. We can define "Name" for the new Calculated Field and "Formula" can be entered by inserting required fields through Fields section. For inserting numbers and operators, you can use formula pop-up as shown in the below screen-shot.

![Calculated field dialog in ASP NET MVC pivot grid control](Calculated-Field_images/Calculated-Field-Popup.png)

Click **Add** for adding the respective Calculated Field and **OK** to populate the PivotGrid control.

### Through Code-behind

For client mode, Calculated Field can be created at code-behind by defining formula based on the existing Pivot Fields in the PivotGrid. To indicate a field as a calculated field we need to set `IsCalculatedField` property to true and `Formula` property to set the expression.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableGroupingBar(true).DataSource(dataSource => dataSource.Values(values => { values.FieldName("Amount").Add(); values.FieldName("Price").FieldCaption("Price").IsCalculatedField(true).Formula("Amount * 15").Add(); }))

{% endhighlight %}

For server mode, we need to set **CalculationType** property to **CalculationType.Formula** and **Formula** property to set the expression for the PivotComputation item in the PivotReport.

{% highlight c# %}

    private PivotReport BindDefaultData()
    {
        PivotReport pivotSetting = new PivotReport();
        pivotSetting.PivotRows.Add(new PivotItem { FieldMappingName = "Country", FieldHeader = "Country", TotalHeader = "Total" });
        pivotSetting.PivotColumns.Add(new PivotItem { FieldMappingName = "Product", FieldHeader = "Product", TotalHeader = "Total" });
        pivotSetting.PivotCalculations.Add(new PivotComputationInfo { CalculationName = "Amount", Description = "Amount", FieldHeader = "Amount", FieldName = "Amount", SummaryType = Syncfusion.PivotAnalysis.Base.SummaryType.DoubleTotalSum });
        pivotSetting.PivotCalculations.Add(new PivotComputationInfo  {
            CalculationName = "Price",
            FieldHeader = "Price",
            FieldName = "Price",
            CalculationType = CalculationType.Formula,
            Formula = "Amount * 10 + 12"
        });
        return pivotSetting;
    }

{% endhighlight %}


![ASP NET MVC pivot grid control with user-defined field, aka calculated field](Calculated-Field_images/Calculated-Field1.png)