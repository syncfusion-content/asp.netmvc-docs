---
layout: post
title: Change-Weekend | Gantt | ASP.NET MVC | Syncfusion
description: Change workweek/working days in a week
platform: ejmvc
control: Gantt
documentation: ug
---

## Change workweek/working days in a week
Non-working days/weekend are used to represent the non-productive days in a project. It is possible to change the non-working days in a week using the `WorkWeek` property in Gantt.

By default, Saturdays and Sundays are considered as non-working days/weekend in a project. 

The following code example explains how to change weekend/non-working days

{% highlight CSHTML %}

@(Html.EJ().Gantt("gantt")
    .WorkWeek(new List<string>() { "Sunday","Monday","Tuesday","Wednesday","Thursday" })
    )
@(Html.EJ().ScriptManager())

{% endhighlight %}

![](Change-Workweek_images/Change_Workweek_img1.png)

The above screen shot will be displayed after changing the non-working days in Gantt.
{:.caption}



