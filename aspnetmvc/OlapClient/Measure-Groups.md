---
layout: post
title: Measure Groups | OLAPClient | ASP.NET MVC | Syncfusion
description: measure groups 
platform: ejmvc
control: OLAPClient
documentation: ug
---

# Measure Groups

In Cube Dimension Browser, treeview can be viewed in a filtered manner through the Measure Groups option. This feature allows you to view the list of measure groups and dimensions associated with the selected measure group from the cube. For enabling this, the `EnableMeasureGroups` property is set to true. By default, its value is set to false.

{% highlight C# %}

@Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("/OlapClient")).Title("OLAP Browser").EnableMeasureGroups(true)

{% endhighlight %}

On selecting a measure group from the drop-down list, the Cube Dimension Browser treeview displays the related dimensions as follows.

![](Measure-Groups_images/measure.png)

![](Measure-Groups_images/measure1.png)