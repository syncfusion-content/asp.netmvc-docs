---
layout: post
title: Layout | PivotGauge | ASP.NET MVC | Syncfusion
description: This document illustrates that how to define layouts and its functionalities in ASP.NET MVC PivotGauge control
platform: ejmvc
control: PivotGauge
documentation: ug
---

# Layout 

## Row-wise Layout

Gauges can be arranged in specified number of rows by using the `RowsCount` property.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").RowsCount(2)

{% endhighlight %}

![Row wise layout in ASP NET MVC pivot gauge control](Layout_images/Row-wiseLayout.png) 

## Column-wise Layout

Gauges can be arranged in specified number of columns by using the `ColumnsCount` property.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").ColumnsCount(2)

{% endhighlight  %}

![Row wise layout in ASP NET MVC pivot gauge control](Layout_images/Column-wiseLayout.png)