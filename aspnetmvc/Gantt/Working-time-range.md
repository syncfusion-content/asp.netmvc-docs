---
layout: post
title: Working Time Range | Gantt | ASP.NET MVC | Syncfusion
description: working time range
platform: ejmvc
control: Gantt
documentation: ug
---

# Working Time Range

In Gantt control, working hours in a day for a project can be defined by using the `DayWorkingTime` property. Based on the working hours, automatic date scheduling and duration validations for a task are performed.

The below code snippet explains on how to define the working time range for the project in Gantt,

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
	// ...
	.DayWorkingTime(dt=>
	{
		dt.From("08:00 AM").To("12:00 PM").Add();
		dt.From("01:00 PM").To("05:00 PM").Add();
	})    
	)
@(Html.EJ().ScriptManager())

{% endhighlight %}

N> 1. Individual tasks can lie between any time within the defined working time range of the project.

N> 2. `DayWorkingTime` property is used to define the working time for the whole project.

The below demo explains the working time range in Gantt.

[Working Time Range](https://mvc.syncfusion.com/demos/web/gantt/ganttworkingtimerange)

The following screen shot shows working time range in Gantt control. 

![](Working-time-range_images/Working-time-range_img1.png)

## Highlight working time range

Highlight the working time range with a background color by using the `DayWorkingTime.Background` property. You can highlight the non-working time ranges in a day. To do this, set the `HighlightNonWorkingTime` property to `true`. To customize the non-working time background, use the `NonWorkingBackground` property.

The following code snippet explains how to define the working time range with background in Gantt.

{% highlight CSHTML %}
@(Html.EJ().Gantt("Gantt")
    // ...
    .HighlightNonWorkingTime(true)
    .NonWorkingBackground("#B7C3D0")
    .DayWorkingTime(dt => {
        dt.From("08:00 AM").To("12:00 PM").Background("#EBF5FB").Add();
        dt.From("01:00 PM").To("05:00 PM").Background("#EBF5FB").Add();
    })
)
@(Html.EJ().ScriptManager())
{% endhighlight %}

N> The background colors of working time range are highlighted only when the `ScheduleHeaderSettings.ScheduleHeaderType` value as `day`.

The following screenshot shows the working time range with background colors.

![](Working-time-range_images/Working-time-range_img2.png)
