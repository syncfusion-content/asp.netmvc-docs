---
layout: post
title: Frame Type | PivotGauge | ASP.NET MVC | Syncfusion
description: frame type 
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

![](Frame-Type/FullCircle.png)

## Half Circle
Half Circle frame lets the PivotGauge display in semi-circular shape. For this, frame type needs to be set as "HalfCircle" within the `FrameType` property.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").Frame(frame=> { frame.FrameType(Frame.HalfCircle) })

{% endhighlight %}

![](Frame-Type/HalfCircle.png)
