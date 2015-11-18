---
layout: post
title: Segment Settings | DigitalGauge | ASP.NET MVC | Syncfusion
description: segment settings
platform: ejmvc
control: DigitalGauge
documentation: ug
---

# Segment Settings

## Appearance

* Digital Gauge consists of several digital segments. Segment is customized with some properties. Color of the segment is set by using color property. Color is either given as string or hexadecimal value. 
* You can add gradient effects to the segments with the help of gradient attribute. The opacity of the segment is also adjustable. The space between two  segments are adjusted with spacing property.


{% highlight CSHTML %}

@* For Digital Gauge rendering *@

@(Html.EJ().DigitalGauge("DigitalGauge1")

.Width(800)

.Value("GO AHEAD")

.Items(it=>

{ it.SegmentSettings(ss =>

// For setting segment opacity

ss.Opacity(0.1)

// For setting segment spacing

.Spacing(4)

// For setting segment color

.Color("Green")).Add();   }))

{% endhighlight %}


Execute the above code examples to render the DigitalGauge as follows.

![](Segment-Settings_images/Segment-Settings_img1.png)

Digital Gauge control with segment settings
{:.caption}

## Dimension Modification

* Digital Gauge consists of several digital segments. Segment is customized with some properties. Color of the segment is set by using color property. Color is either given as string or hexadecimal value. 
* You can add gradient effects to the segments with the help of gradient attribute. The opacity of the segment is also adjustable. The space between two  segments are adjusted with spacing property.


{% highlight CSHTML %}

@* For Digital Gauge rendering *@

@(Html.EJ().DigitalGauge("DigitalGauge1")

.Width(800)

.Value("WELCOME")

.Items(it=>

{ it.SegmentSettings(ss =>

// For setting segment opacity

ss.Length(3)

// For setting segment color

.Width(3)).Add();

}))

{% endhighlight %}


Execute the above code examples to render the DigitalGauge as follows.


![](Segment-Settings_images/Segment-Settings_img2.png)

Digital Gauge control with segment dimension
{:.caption}

