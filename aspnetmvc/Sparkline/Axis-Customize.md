---
layout: post
title: Axis Customize
description: Learn how to customize axis in Sparkline.
platform: ejmvc
control: Sparkline
documentation: ug
---

## Axis Customize 

The Sparkline axis can be collapsed using visible property in `AxisLineSettings` and this not applicable for win-loss. You can customize `Color`, `Width` and `DashArray` of axis line.

 {% highlight cshtml %}
 
 @(Html.EJ().Sparkline("container")

 //To customize the axis line of the sparkline
 .AxisLineSettings(as => as.Visible(true).Color("#ff14ae"))
 
 )

{% endhighlight %}

![](Axis-Customize_images/Axis-Customize_img1.png)
