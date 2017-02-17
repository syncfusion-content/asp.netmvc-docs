---
layout: post
title: Value-Soritng | PivotGrid | ASP.NET MVC | Syncfusion
description: value sorting
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Value Sorting

I> This feature is applicable for Relational datasource only at Client Mode.

Value Sorting allows to sort columns and rows based on value fields.

The headers of the column to be sorted is given in the 'HeaderText' property under 'ValueSortSettings' in field wise order separated by a string.  The string which is used to separate the headers is given in the property 'HeaderDelimiters'.

{% highlight js %}
  
@Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Add(); values.FieldName("Quantity").Add(); })).ValueSortSettings(valuesortsettings=>valuesortsettings.HeaderText("Bike##Quantity").HeaderDelimiters("##").SortOrder(SortOrder.Descending))

{% endhighlight %}

![](Value-Sorting_images/Before.png) 

![](Value-Sorting_images/After.png) 



