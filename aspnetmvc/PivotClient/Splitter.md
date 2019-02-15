---
layout: post
title: Splitter | PivotClient | ASP.NET MVC | Syncfusion
description: splitter
platform: ejmvc
control: PivotClient
documentation: ug
---

# Splitter

I> This feature is not applicable for OLAP datasource  bound from server-side.

You can resize Cube Dimension Browser and Axis Element Builder by setting `EnableSplitter` property to true.This property is disabled by default.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).EnableSplitter(true)

{% endhighlight %}

![Left move of splitter in ASP NET MVC pivot client control](Splitter_images/Splitter1.png)

![Resizing axis element builder in ASP NET MVC pivot client control](Splitter_images/Splitter2.png)

![Right move of splitter in ASP NET MVC pivot client control](Splitter_images/Splitter3.png)

![Resizing cube dimension browser in ASP NET MVC pivot client control](Splitter_images/Splitter4.png)