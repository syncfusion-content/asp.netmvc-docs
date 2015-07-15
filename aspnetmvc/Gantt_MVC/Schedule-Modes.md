---
layout: post
title: Schedule-Modes
description: schedule modes
platform: ejmvc
control: Gantt
documentation: ug
---

## Schedule Modes

Gantt contains built-in support to switch over to various schedule mode. You can achieve this by defining a schedule header type for the Gantt.

Schedule Header Types

Gantt contains the following built-in schedule header types:

* Day – Hour
* Week – Day
* Month – Week
* Year – Month

The following code example illustrates you on how to change the schedule mode.

### Week Schedule Mode

In the Week schedule mode, the upper part of the schedule header displays the weeks whereas the bottom half of the header displays the days. Refer the following code example.





{% highlight html %}



@(Html.EJ().Gantt("Gantt")

           //...                             

  .ScheduleHeaderSettings(sh=>sh.ScheduleHeaderType(GanttscheduleHeaderType.Week)

  .WeekHeaderFormat("MMM dd , yyyy ")

  .DayHeaderFormat("ddd "))



)



{% endhighlight %}





The following screenshot illustrates the Week Schedule in Gantt control.

{ ![](Schedule-Modes_images/Schedule-Modes_img1.png) | markdownify }
{:.image }




_Figure_ _41__: Week Schedule in Gantt control_

### Month Schedule Mode

In the Week schedule mode, the upper part of the schedule header displays the Months whereas the bottom header of the schedule displays its corresponding Weeks. Refer the following code example.





{% highlight html %}



@(Html.EJ().Gantt("Gantt")

//...                             

.ScheduleHeaderSettings(sh=>sh.ScheduleHeaderType(GanttscheduleHeaderType.Month)

.MonthHeaderFormat("MMM yyyy")

.WeekHeaderFormat("M/dd"))



)



{% endhighlight %}





The following screenshot illustrates the Month Schedule in Gantt control.

{ ![](Schedule-Modes_images/Schedule-Modes_img2.png) | markdownify }
{:.image }


### Year Schedule Mode

In the Week schedule mode, the upper schedule header displays the Years whereas the bottom header displays its corresponding Months. Refer the following code example.



{% highlight html %}



@(Html.EJ().Gantt("Gantt")

           //...

.ScheduleHeaderSettings(sh=>sh.ScheduleHeaderType(GanttscheduleHeaderType.Year)

.YearHeaderFormat("yyyy")

.MonthHeaderFormat("MMM"))



)



{% endhighlight %}




The following screen shot shows the Year Schedule in Gantt control.


{ ![](Schedule-Modes_images/Schedule-Modes_img3.png) | markdownify }
{:.image }


### Day Schedule Mode

In the Week schedule mode, the upper part of the header displays the Days whereas the bottom schedule header displays its corresponding Hours. Refer the following code example.



{% highlight html %}



@(Html.EJ().Gantt("Gantt")

  //...

 .ScheduleHeaderSettings(sh=>sh.ScheduleHeaderType(GanttscheduleHeaderType.Day)

 .DayHeaderFormat("dd,MM,yy ")

 .HourHeaderFormat("HH"))



)



{% endhighlight %}





The following screenshot illustrates the Day Schedule in Gantt control.

{ ![](Schedule-Modes_images/Schedule-Modes_img4.png) | markdownify }
{:.image }


### Hour Schedule Mode

An Hour-Minute Schedule Mode tracks the tasks in minutes scale. In this mode, upper schedule header displays hour scale and the lower schedule header displays its corresponding Minutes. The minute split-up in the lower schedule header can be defined by using the MinutesPerIntervalEnum property. The enumeration values of the MinutesPerInterval are,

* Auto
* OneMinute
* FiveMinutes
* FifteenMinutes
* ThirtyMinutes



The value, Auto, automatically calculates the interval depending upon the ScheduleStartDate and 

ScheduleEndDate, whereas the other enumeration values splits up accordingly.



The Hour Schedule Mode supports both the Minute and Hour duration units.





{% highlight html %}



@(Html.EJ().Gantt("ganttContainer")



                                                          // ...



                                       .DateFormat("M/d/yyyy hh:mm:ss tt")



                                       .DurationUnit(GanttDurationUnit.Minute)



                                      .ScheduleHeaderSettings(sh =>{



                                                     sh.ScheduleHeaderType(GanttscheduleHeaderType.Hour);



                                                     sh.MinutesPerInterval(GanttminutesPerInterval.FiveMinutes);   



                                             })



                                                           // ...



                                           )





{% endhighlight %}





{ ![](Schedule-Modes_images/Schedule-Modes_img5.png) | markdownify }
{:.image }


