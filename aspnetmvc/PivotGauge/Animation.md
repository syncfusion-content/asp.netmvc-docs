---
layout: post
title: Animation | PivotGauge | ASP.NET MVC | Syncfusion
description: animation
platform: ejmvc
control: PivotGauge
documentation: ug
---

# Animation

The animation option makes the pointer to rotate from minimum value to actual value with animation effects. The animation can be enabled/disabled by using the `EnableAnimation` property. Speed of the pointer can be controlled by using the `AnimationSpeed` property. Time is represented in milliseconds.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").EnableAnimation(true).AnimationSpeed(1000)

{% endhighlight  %}
