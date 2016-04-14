---
layout: post
title: Summary Type | PivotGrid | ASP.NET MVC | Syncfusion
description: summary type
platform: ejmvc
control: PivotGrid
documentation: ug
---


# Summary Type

I> This feature is applicable only for Relational datasource only at Client Mode.

Allow us to specify the required summary type that PivotGrid should use in its summary cells. “Sum” is the default summary type. Following are the summary types that are supported:

* sum
* average
* count
* minimum
* maximum

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").SummaryType(PivotAnalysisSummaryType.Average).Add(); values.FieldName("Quantity").FieldCaption("Quantity").SummaryType(PivotAnalysisSummaryType.TotalSum).Add(); }))  

 <script type="text/javascript">
        function onLoad(args) {
            args.model.dataSource.data = pivot_dataset;
        }
    </script>

{% endhighlight %}

![](Getting-Started_images/purejssummarytype.png) 

