---
layout: post
title: Animation
description: Learn how to animate the SunburstChart .
platform: ejmvc
control: SunburstChart
documentation: ug
---

# Animation

Sunburst chart allows you to animate the chart segments. You can enable animation using **EnableAnimation** property. 

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     //...Enable Animation
      .EnableAnimation(true)
      //...
 )

{% endhighlight %}


## Animation Types 
Sunburst chart provide options to animate the chart segments in different ways using **AnimationType** property.
FadeIn – It gradually changes opacity of the chart segment.
Rotation – During an animation, control rotate from 0 to 360 angle.

### Fade In

The Fade In animation is enabled as follows 

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     //...Enable Animation
      .EnableAnimation(true)
      .SunburstAnimationType(SunburstAnimationType.FadeIn)
      //...
 )

{% endhighlight %}

![](Animation_images/Animation_img1.gif)




### Rotation

The following example shows how to enable rotation animation in ejSunburstChart

{% highlight cshtml %}
@(Html.EJ().SunburstChart("chartContainer")

     //...Enable Animation
      .EnableAnimation(true)
      .SunburstAnimationType(SunburstAnimationType.Rotation)
      //...
 )


{% endhighlight %}

![](Animation_images/Animation_img2.gif)

[Click](http://mvc.syncfusion.com/demos/web/sunburst/animation) here to view the online demo sample of  Animation in  the Sunburst Chart.
