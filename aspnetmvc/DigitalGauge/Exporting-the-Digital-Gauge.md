---
layout: post
title: Exporting-the-Digital-Gauge
description: exporting the digital gauge
platform: ejmvc
control: DigitalGauge
documentation: ug
---

# Exporting the Digital Gauge

Digital Gauge has an exporting feature where Gauge control is converted into image format and then exported to client-side. The method API exportImage exports the Digital Gauge. It has two arguments such as filename and file format. For exporting, you can refer the following code example.


{% highlight js %}

// For Digital Gauge rendering

@(Html.EJ().DigitalGauge("DigitalGauge1")

// For setting text

.Value("Syncfusion"))

<script>

$("#DigitalGauge1").ejDigitalGauge("exportImage", "Digital", "PNG");

<script/>

{% endhighlight %}


Execute the above code examples to render the DigitalGauge as follows.

![](Exporting-the-Digital-Gauge_images/Exporting-the-Digital-Gauge_img1.png)

_Figure 37: Digital Gauge control with Export functionality_



