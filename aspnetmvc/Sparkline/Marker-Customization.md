---
layout: post
title: Markers Customization
description: Learn how to add markers to Sparkline.
platform: ejmvc
control: Sparkline
documentation: ug
---

## Marker Customization

You can customize markers by initializing the `MarkerSettings` property. The customization options allow you to change the `Fill`, `Width`, `Opacity`and `Border` for marker. This customization only applicable for line, column and area type Sparkline.

{% highlight cshtml %}

@(Html.EJ().Sparkline("container")

 //To customize the marker of the sparkline
 .MarkerSettings(mr => mr.Visible(true).Fill("#ff14ae").Width(4).Border(br=> br.Width(1)))

 )


{% endhighlight %}

![](Marker-Customization_images/Marker-Customization_img1.png)
