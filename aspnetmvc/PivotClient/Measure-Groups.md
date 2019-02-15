---
layout: post
title: Measure Groups | PivotClient | ASP.NET MVC | Syncfusion
description: measure groups
platform: ejmvc
control: PivotClient
documentation: ug
---

# Measure Groups

I> This feature is applicable only for OLAP data source bound from server-side.

In Cube Dimension Browser, treeview can be viewed in a filtered manner through the Measures option. This feature allows you to view the list of measure groups and dimensions associated with the selected measure group from the cube. For enabling this, the `EnableMeasureGroups` property is set to true. By default, its value is set to false.

{% highlight cshtml %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").Url(Url.Content("/OlapClient")).Title("OLAP Browser").EnableMeasureGroups(true)

{% endhighlight %}

On selecting a measure group from the drop-down list, the Cube Dimension Browser treeview displays the related measures and dimensions as follows.

![Measure group in ASP NET MVC pivot client control](Measure-Groups_images/measure.png)

![Internet Sales Measure Group in ASP NET MVC pivot client control](Measure-Groups_images/measure1.png)