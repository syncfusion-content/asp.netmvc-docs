---
layout: post
title: Group by date | PivotGrid | ASP.NET MVC | Syncfusion
description: group by date
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Group by date

I> This feature is applicable for Relational datasource alone (in Client Mode).

Allows the user to categorize the date type field and showcase them based on year, quarter, month and day formats. 

{% highlight CSHTML %}

 @Html.EJ().Pivot().PivotGrid("PivotGrid1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); rows.FieldName("State").FieldCaption("State").Add(); }).Columns(columns => { columns.FieldName("Date").FieldCaption("Date").Format("date").FormatString("yyyy-MMM-ddd").Delimiter("-").GroupByDate(groupByDate => { groupByDate.Interval(groupinterval => { groupinterval.Add("yyyy"); groupinterval.Add("MMM-dd"); }); }).Add(); }).Values(values => { values.FieldName("Product").Add(); values.FieldName("Quantity").Add(); }))

{% endhighlight %}

The properties associated with group by date option is,

* Format - To set the data type format. 
* FotmatString - Specifies the structure of the date format.
* Delimiter - Specifies the separator of the date values.
* GroupByDate.Interval - Specifies the pattern in which date type to be displayed.

![](GroupByDate_images/group_by_date.png)
