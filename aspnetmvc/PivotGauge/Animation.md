---
layout: post
title: Animation | OLAPGauge | ASP.NET MVC | Syncfusion
description: animation
platform: ejmvc
control: OLAPGauge
documentation: ug
---

# Animation

The animation option makes the pointer to rotate from minimum value to actual value with animation effects.  Animation could be enabled/disabled by using the `EnableAnimation` property.  Speed of the pointer could be controlled by using the `AnimationSpeed` property. Time is represented in milliseconds.

{% highlight CSHTML %}

@Html.EJ().Olap().OlapGauge("OlapGauge1").Url(Url.Content("~/OlapGauge")).EnableAnimation(true).AnimationSpeed(1000)

{% endhighlight  %}
