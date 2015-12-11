---
layout: post
title: Responsive Layout | OLAPGauge | ASP.NET MVC | Syncfusion
description: responsive layout
platform: ejmvc
control: OLAPGauge
documentation: ug
---

# Responsive Layout

OlapGauge widget supports responsive rendering based on the target device (desktop & tablet) resolution. It supports resolution upto 1024x600. You can enable responsiveness in OlapGauge by setting `IsResponsive` property to true.

{% highlight CSHTML %}

@Html.EJ().Olap().OlapGauge("OlapGauge1").Url(Url.Content("~/OlapGauge")).IsResponsive(true)

{% endhighlight  %}

![](Responsive-Layout_images/responsive 1.png)

_Normal View_


![](Responsive-Layout_images/responsive 2.png)

_Responsive View_



