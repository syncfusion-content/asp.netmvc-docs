---
layout: post
title: Frame Type | PivotGauge | ASP.NET MVC | Syncfusion
description: This document illustrates that how to define frames and its types with respective to the angles and scales in ASP.NET MVC PivotGauge control 
platform: ejmvc
control: PivotGauge
documentation: ug
---

# Frame Type

## Full Circle

Full Circle frame lets the PivotGauge display in circular shape. Frame type can be set using the `FrameType` property.  By default, the frame type is "FullCircle".

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").Frame(frame=> { frame.FrameType(Frame.FullCircle) })

{% endhighlight %}

![](Frame-Type_images/FullCircle.png)

## Half Circle
Half Circle frame lets the PivotGauge to display in semi-circular shape. For this, frame type needs to be set as "HalfCircle" within the `FrameType` property and need to set `StartAngle` and `SweepAngle` for the PivotGauge in the `Scales` property.


{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").Frame(frame=>frame.FrameType(Frame.HalfCircle).HalfCircleFrameStartAngle(180).HalfCircleFrameEndAngle(360)).Scales(scale =>{ scale.StartAngle(180).SweepAngle(180).Add();})

{% endhighlight %}

![](Frame-Type_images/HalfCircle.png)
