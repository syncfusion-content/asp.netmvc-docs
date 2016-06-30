---
layout: post
title: Responsive Layout | PivotGauge | ASP.NET MVC | Syncfusion
description: responsive layout
platform: ejmvc
control: PivotGauge
documentation: ug
---

# Responsive Layout

PivotGauge control supports responsive rendering based on the target device (desktop & tablet) resolution. It supports resolution upto 1024x600. You can enable responsiveness in PivotGauge by setting `IsResponsive` property to true.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").IsResponsive(true)

{% endhighlight  %}

![](Responsive-Layout/Responsive1.png)

_Normal View_


![](Responsive-Layout/Responsive2.png)

_Responsive View_



