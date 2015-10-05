---
layout: post
title: 3D | OLAPChart | ASP.NET MVC | Syncfusion
description: 3d
platform: ejmvc
control: OLAPChart
documentation: ug
---

# 3D

The OlapChart control provides three dimensional view for Bar, Column, StackingBar, StackingColumn and Pie Charts. The representation of data in 3D Chart is very clear and easy to understand when compared to 2D Chart. You can see all the three dimensions of the series by rotating them. To enable this functionality, you need to set `enable3D` property to "true".

The following code example explains on how to enable 3D in the OlapChart control.

{% highlight CSHTML %}

@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).Rotation(24).CommonSeriesOptions(comm => { comm.Type(SeriesType.Column); }).Size(size => size.Height("320px").Width("100%")).Enable3D(true)
       
{% endhighlight  %}


![](3DChart_images/3DChart_images1.png)


