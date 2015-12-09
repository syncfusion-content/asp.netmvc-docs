---
layout: post
title: Frame Type | OLAPGauge | ASP.NET MVC | Syncfusion
description: frame type 
platform: ejmvc
control: OLAPGauge
documentation: ug
---

# Frame Type

## Full Circle

Full Circle frame lets the OlapGauge display in circular shape. Frame type can be set using the `FrameType` property.  By default, the frame type is "FullCircle".

{% highlight CSHTML %}

@Html.EJ().Olap().OlapGauge("OlapGauge1").Url(Url.Content("~/OlapGauge")).Frame(Frame.FullCircle)

{% endhighlight %}

![](Frame-Type_images/fullCircle.png) 

## Half Circle
Half Circle frame lets the OlapGauge display in semi-circular shape. For this, frame type needs to be set as "HalfCircle" within the `FrameType` property.

{% highlight CSHTML %}

@Html.EJ().Olap().OlapGauge("OlapGauge1").Url(Url.Content("~/OlapGauge")).Frame(Frame.HalfCircle)

{% endhighlight %}

![](Frame-Type_images/halfCircle.png) 
