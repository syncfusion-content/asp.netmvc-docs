---
layout: post
title: Layout | PivotGauge | ASP.NET MVC | Syncfusion
description: layout 
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

![](Layout/Row-wiseLayout.png) 

## Column-wise Layout

Gauges can be arranged in specified number of columns by using the `ColumnsCount` property.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").ColumnsCount(2)

{% endhighlight  %}

![](Layout/Column-wiseLayout.png)