---
layout: post
title: Tooltip | PivotGauge | ASP.NET MVC | Syncfusion
description: This document illustrates that how to enable tooltip and its customization in ASP.NET MVC PivotGauge control
platform: ejmvc
control: PivotGauge
documentation: ug
---

# Tooltip

Tooltip can be enabled by using the `EnableTooltip` property.

N> By default, this property is set to "false".

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").EnableTooltip(true)

{% endhighlight %}

Tooltip appearance can be customized by overriding its CSS class.

{% highlight css %}

    .e-pivotgauge-tooltip {
        background-color: #D2E9FE!important;
        border: 2px solid #01465C!important;
        color: #01232E!important;
        border-radius: 5px!important;
        margin-top: 20px;
        text-align: left;
        font: 12 px Segoe UI;
        line-height: 20px;
    }

{% endhighlight  %}

![Tooltip in ASP NET MVC pivot gauge control](Tooltip_images/Tooltip.png) 

