---
layout: post
title: Range
description: range
platform: ejmvc
control: TimePicker
documentation: ug
---

# Range

TimePicker widget provide options to set the Range (MinTime & MaxTime) for the time.

## Steps to change MinTime & MaxTime of the TimePicker

The following steps explains you to change the Range of the TimePicker.

1. Add the following code to the corresponding view page to render the TimePicker.



{% highlight html %}

@*Add the following code example to the corresponding CSHTML page to render TimePicker widget with Min and Max time*@

@Html.EJ().TimePicker("time").MinTime("10:00 AM").MaxTime("10:00 PM")


{% endhighlight %}

Execute the above code to render the following output.

![](Range_images/Range_img1.png)



_Figure 16: Range for TimePicker widget_

