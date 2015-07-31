---
layout: post
title: Time-Format
description: time format
platform: ejmvc
control: TimePicker
documentation: ug
---

# Time Format

TimePicker widget provides you an option to change the TimeFormat property.

## Steps to change Time Format of TimePicker widget

The following steps explains you to change the time format for the TimePicker.

1. Add the following code to the corresponding view page to render the TimePicker.



{% highlight html %}

@*Add the following code example to the corresponding CSHTML page to render TimePicker widget with time format*@

@Html.EJ().TimePicker("time").TimeFormat("hh:mm:ss tt")

{% endhighlight %}


Execute the above code to render the following output.

![](Time-Format_images/Time-Format_img1.png)



_Figure 17: TimePicker with TimeFormat._

