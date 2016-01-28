---
title: Getting started with Schedule component	
description: Rendering a basic Scheduler with remote data
platform: ejmvc
control: schedule
documentation: ug
keywords: ejschedule, schedule, schedule widget, js schedule 
---
# Getting Started

Follow the steps pointed out in the [Getting Started](http://help.syncfusion.com/aspnetmvc/getting-started) page of the Introduction part to create an MVC application with required assembly references, scripts and stylesheets.

Create a new Class in controller page to define the data to be passed to the Scheduler as mentioned below,

{% highlight c# %}

public class ScheduleData
{
    public int ProgramId { get; set; }
    public string ProgramName { get; set; }
    public string Comments { get; set; }
    public DateTime ProgramStartTime { get; set; }
    public DateTime ProgramEndTime { get; set; }
    public bool IsAllDay { get; set; }
    public bool IsRecurrence { get; set; }
    public string RecurrenceRule { get; set; }
}

{% endhighlight %}

Now create an instance of the class and add the list of Scheduler data to it within the Index method in controller page, which will then be passed to the View page and bound to the Scheduler dataSource.

{% highlight c# %}

public ActionResult Index()
{
    List<ScheduleData> data = new List<ScheduleData> {
     new ScheduleData {
            ProgramName = "Turtle Walk",
            Comments = "Night out with turtles",
            ProgramStartTime = new DateTime(2016, 6, 2, 3, 0, 0),
            ProgramEndTime = new DateTime(2016, 6, 2, 4, 0, 0),
            IsAllDay = true
     },
     new ScheduleData {
            ProgramName = "Winter Sleepers",
            Comments = "Long sleep during winter season",
            ProgramStartTime = new DateTime(2016, 6, 3, 1, 0, 0),
            ProgramEndTime = new DateTime(2016, 6, 3, 2, 0, 0)
     },
     new ScheduleData {
            ProgramName = "Estivation",
            Comments = "Sleeping in hot season",
            ProgramStartTime = new DateTime(2016, 6, 4, 3, 0, 0),
            ProgramEndTime = new DateTime(2016, 6, 4, 4, 0, 0)
     }
    };
    return View(data);
}

{% endhighlight %}

Add the Scheduler code in View page as shown below,

{% highlight razor %}

  @(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014,6,2))
        .AppointmentSettings(fields => fields.Datasource(Model)
            .Id("ProgramId")
            .Subject("ProgramName")
            .StartTime("ProgramStartTime")
            .EndTime("ProgramEndTime")
            .Description("Comments")
            .AllDay("IsAllDay")
            .Recurrence("IsRecurrence")
            .RecurrenceRule("RecurrenceRule"))
            )

{% endhighlight %}

N> The appointment fields like Id, Subject, Description and other required fields are needed to be mapped with the appropriate column names from the dataSource as done in the above code example.

To bind the remote data directly to the Scheduler instead of passing data from the Model as previously depicted, refer the below code snippet.

{% highlight razor %}

  @(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014,6,2))
        .AppointmentSettings(fields => fields.Datasource("http://mvc.syncfusion.com/OdataServices/Northwnd.svc/")
            .Query("ej.Query().from('Events').take(10)")
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .Description("Description")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
            )

{% endhighlight %}

To bind the data to the Scheduler from database or any other dataSources, refer [here](/aspnetmvc/schedule/data-binding).