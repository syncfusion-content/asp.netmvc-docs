---
layout: post
title: Time Format | TimePicker | ASP.NET MVC | Syncfusion
description: Learn here about time format in Syncfusion Essential ASP.NET MVC TimePicker Control, its elements, and more.
platform: ejmvc
control: TimePicker
documentation: ug
---

# Time Format in ASP.NET MVC TimePicker

TimePicker widget provides you an option to change the TimeFormat property.

## Steps to change Time Format of TimePicker widget

The following steps explains you to change the time format for the TimePicker.

1. Add the following code to the corresponding view page to render the TimePicker.



{% highlight CSHTML %}

@*Add the following code example to the corresponding CSHTML page to render TimePicker widget with time format*@

@Html.EJ().TimePicker("time").TimeFormat("hh:mm:ss tt")

{% endhighlight %}


Execute the above code to render the following output.

![ASP.NET MVC TimePicker time format](Time-Format_images/Time-Format_img1.png)

TimePicker with TimeFormat.
{:.caption}
