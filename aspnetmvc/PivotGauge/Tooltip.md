---
layout: post
title: Tooltip | OLAPGauge | ASP.NET MVC | Syncfusion
description: tooltip
platform: ejmvc
control: OLAPGauge
documentation: ug
---

# Tooltip

Tooltip can be enabled by using the `EnableTooltip` property. By default, this property is set to "false".

{% highlight CSHTML %}

@Html.EJ().Olap().OlapGauge("OlapGauge1").Url(Url.Content("~/OlapGauge")).EnableTooltip(true)

{% endhighlight %}

Tooltip appearance can be customized by overriding its CSS class.

{% highlight css %}

.e-olapgauge-tooltip {
    background-color: aqua!important;
    border: 2px solid red!important;
    color: black!important;
    border-radius: 18px!important;
    margin-top: 20px;
    text-align: left;
    font: 12 px Segoe UI;
    line-height: 20px;
}

{% endhighlight  %}

![](Tooltip_images/tooltip.png) 

