---
layout: post
title: Sunburst Zooming
description: Learn how to Zoom the SunburstChart for better data visualization
platform: ejmvc
control: SunburstChart
documentation: ug
---

# Zooming

Sunburst chart provides zooming (drill down) experience with animation for both mouse and touch enabled devices. It allows you to Virtualize large sets of data into minimum data view.The zooming is achieved by using the property of *zoomSettings*

The following code shows how to initialize the zooming.

{% highlight cshtml %}
@(Html.EJ().SunburstChart("chartContainer")

       .ZoomSettings(zoom => zoom.Enable(true))
 )


{% endhighlight %}

![](Zooming_images/Zooming_img1.gif)

## Zooming toolbar
By default, zooming toolbar will be enabled while zooming the segment.It contains both back and reset option.
You can align the zooming toolbar position by using *ToolbarHorizontalAlignment* and *ToolbarVerticalAlignment* property.

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

       .ZoomSettings(zoom => zoom.Enable(true).ToolbarHorizontalAlignment(SunburstHorizontalAlignment.Left))
 )


{% endhighlight %}

![](Zooming_images/Zooming_img2.png)

[Click](http://mvc.syncfusion.com/demos/web/sunburst/zooming) here to view the online demo sample of Zooming in  the Sunburst Chart.
