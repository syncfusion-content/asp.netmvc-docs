---
layout: post
title: Time Interval | DateTimePicker | ASP.NET MVC | Syncfusion
description: Learn hera about time interval with Syncfusion Essential ASP.NET MVC DateTimePicker Control, its elements and more.
platform: ejmvc
control: DateTimePicker
documentation: ug
---

# Time Interval in ASP.NET MVC DateTimePicker

You can set time interval between two adjacent time values in the time popup manually using the “Interval” property. By default the value of the “Interval” property is 30 minutes. Setting this value as 60 is considered as 1 hour. Sometimes you need to update for every hour work log reports. In that case to select time from time popup window with 1 hour interval to update the every 1 hour report you can use Interval option by setting time interval value as “60 minutes”.

1. Add the following code in your CSHTML page to render DateTimePicker widget.

   ~~~ cshtml

	@*Add the following code example to the corresponding CSHTML page to render DateTimePicker widget with customized interval*@

	@Html.EJ().DateTimePicker("DateTime").Interval(60).Width("175px")

   ~~~
   
   
   
2. The following screenshot displays the output for the above code.

    ![Time interval in ASP.NET MVC DateTimePicker.](Time-Interval_images/aspnetmvc-datetimepicker-time-interval.png)
	
	Showcase for DateTimePicker with I hour interval in time picker popup
	{:.caption}
