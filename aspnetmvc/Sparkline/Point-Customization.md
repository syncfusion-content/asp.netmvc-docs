---
layout: post
title: Point Customization
description: Learn how to customize points in Sparkline.
platform: ejmvc
control: Sparkline
documentation: ug
---

## Point Customization

You can customize points by initializing the point colors. The customization options allow you to differentiate the `First`, `Last`, `Highest`, `Lowest`, and `Negative` points. This customization only applicable for line, column and area type Sparkline.

{% highlight cshtml %}

@(Html.EJ().Sparkline("container")

 //To customize the point color of the sparkline
 .NegativePointColor("Red")
 .HighPointColor("Blue")
 .LowPointColor("Orange")
 .StartPointColor("Green")
 .EndPointColor("Green")
 )

{% endhighlight %}

![](Point-Customization_images/Point-Customization_img1.png)
