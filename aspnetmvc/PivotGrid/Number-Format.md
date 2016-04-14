---
layout: post
title: Number format  | PivotGrid | ASP.NET MVC | Syncfusion
description: number format 
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Number format 

I> This feature is applicable only for Relational datasource only at Client Mode.

The PivotGrid widget values could be formatted to number, decimal, currency, percentage, date and time etc… by setting an appropriate`Format` option.

{% highlight CSHTML %}

 @Html.EJ().Pivot().PivotGrid("PivotGrid1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); rows.FieldName("State").FieldCaption("State").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); values.FieldName("Quantity").Format("decimal").Add(); }))
 
 {% endhighlight %}

![](Number-Format_images/Numberformat.png)

