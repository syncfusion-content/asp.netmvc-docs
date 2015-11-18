---
layout: post
title: Digital Elements | DigitalGauge | ASP.NET MVC | Syncfusion
description: digital elements
platform: ejmvc
control: DigitalGauge
documentation: ug
---

# Digital Elements

## Text Customization

* The attribute value refers the text displayed in the Digital Gauge. This text is applicable only for that item instead of all items. Text color is changed by using the property textColor.
* It is possible to align the text inside the Digital Gauge control by using the property textAlign. Two possible values for text align are as follows
	1. left
	2. right

{% highlight CSHTML %}

@* For Digital Gauge rendering *@

@(Html.EJ().DigitalGauge("DigitalGauge1").Items(it=>{it

// For Setting the text value

.Value("STOP")

// For aligning the text

.TextAlign(TextAlign.Right).Add();

}))

{% endhighlight %}

Execute the above code examples to render the DigitalGauge as follows.

![](Digital-Elements_images/Digital-Elements_img1.png)

Digital Gauge control with text customization
{:.caption}

