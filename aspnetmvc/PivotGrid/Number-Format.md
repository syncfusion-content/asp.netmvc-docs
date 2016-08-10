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

Allow us to specify the required number format that PivotGrid should use in its values by setting the `format` option. Following number formats that are supported:

* number
* decimal
* currency
* percentage
* date
* time
* scientific
* accounting
* fraction


{% highlight CSHTML %}

 @Html.EJ().Pivot().PivotGrid("PivotGrid1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); rows.FieldName("State").FieldCaption("State").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); values.FieldName("Quantity").Format("decimal").Add(); }))
 
 {% endhighlight %}

![](Number-Format_images/Numberformat.png)

