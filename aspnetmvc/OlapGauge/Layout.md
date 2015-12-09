---
layout: post
title: Layout | OLAPGauge | ASP.NET MVC | Syncfusion
description: layout 
platform: ejmvc
control: OLAPGauge
documentation: ug
---

# Layout 

## Row-wise Layout

Gauges can be arranged in specified number of rows by using the `RowsCount` property.

{% highlight CSHTML %}

@Html.EJ().Olap().OlapGauge("OlapGauge1").Url(Url.Content("~/OlapGauge")).RowsCount(2)

{% endhighlight %}

![](Layout_images/row based.png) 

## Column-wise Layout

Gauges can be arranged in specified number of columns by using the `ColumnsCount` property.

{% highlight CSHTML %}

@Html.EJ().Olap().OlapGauge("OlapGauge1").Url(Url.Content("~/OlapGauge")).ColumnsCount(2)

{% endhighlight  %}

![](Layout_images/column based.png) 




