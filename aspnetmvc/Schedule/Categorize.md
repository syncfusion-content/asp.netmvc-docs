---
layout: post
title: Categorize
description: categorize	
platform: ejmvc
control: Schedule
documentation: ug
---

# Categorize	

* This feature allows you to differentiate the appointments with various categorize options and individual colors. You can also denote the status of the appointments using this categorize option and can specify your own user-defined category collection.

You can use the following code example to include the categorize option.

{% highlight html %}


@(Html.EJ().Schedule("Schedule1")

.CategorizeSettings(Fields=>Fields.Datasource((IEnumerable)ViewBag.categorize).Enable(true).AllowMultiple(false).Id("id").Text("text").Color("color").FontColor("fontColor"))

)

{% endhighlight %}

## Categorize Settings

* The categorizeSettings is an object collection that holds the categorize related information such as the dataSource. It provides the collection of categorize values that are to be used in appointments, allowMultiple that enables/disables the multiple selection of categorize values and other mapper field names to bind the fields of the dataSource. 

The following are the sub-properties used within the categorizeSettings.

## enable

* This option accepts either true or false, denoting whether to enable/disable the categorize option.

## allowMultiple

* This property enables or disables the multiple selection of categories in the appointment window. 

## dataSource

* It either accepts the local JSON data or remote data for binding the category related information. 

## text

* It holdsthe binding name for text field in the categorize dataSource.

## id

* It holds the binding name for id field in the categorize dataSource.

## color

* It holds the binding name for color field in the categorize dataSource.

## fontColor

* It holds the binding name for fontcolor field in the categorize dataSource.

The following code example illustrates on how to render categorize feature in the Schedule control.


{% highlight html %}

@(Html.EJ().Schedule("Schedule1")

.CurrentDate(new DateTime(2014,5,5))

.CurrentView(CurrentView.Month)

.CategorizeSettings(Fields=>Fields.Datasource(ViewBag.categorize).Enable(true).AllowMultiple(true).Id("id").Text("text").Color("color").FontColor("fontColor"))

.AppointmentSettings(fields => fields.Datasource(ViewBag.datasource)

.Id("Id")

.Subject("Subject")

.StartTime("StartTime")

.EndTime("EndTime")

.AllDay("AllDay")

.Recurrence("Recurrence")

.RecurrenceRule("RecurrenceRule")

// bind the resource id fields collection of each level

.Categorize("Categorize"))

)


{% endhighlight %}

{% highlight c# %}

public partial class ScheduleController : Controller

{

public ActionResult CategorizeOption()

{

List<person> persons = new List<person>();

persons.Add(new person() { Id = 100, Subject = "product meeting", StartTime = new DateTime(2014, 4, 1, 1, 0, 20), EndTime = new DateTime(2014, 4, 1, 5, 0, 20), AllDay = false, Recurrence = false, RecurrenceRule = "FREQ=DAILY;COUNT=10;INTERVAL=2;BYDAY=MO,TU,WE,TH,FR,SA,SU", RoomId = "1", OwnerId = "1", 	 Categorize = "2,3" });

persons.Add(new person() { Id = 101, Subject = "conference meeting", StartTime = new DateTime(2014, 4, 1, 6, 0, 20), EndTime = new DateTime(2014, 4, 1, 7, 0, 20), AllDay = false, Recurrence = false, RecurrenceRule = "FREQ=WEEKLY;COUNT=10;INTERVAL=1;BYDAY=MO,TU", RoomId = "2", OwnerId = "3", 	 Categorize = "1,2" });

persons.Add(new person() { Id = 102, Subject = "New Meeting ", StartTime = new DateTime(2014, 4, 3, 4, 0, 20), EndTime = new DateTime(2014, 4, 3, 7, 0, 20), AllDay = false, Recurrence = false, RecurrenceRule = "FREQ=WEEKLY;COUNT=10;INTERVAL=1;BYDAY=MO,TU", RoomId = "1", OwnerId = "1", 	 Categorize = "3" });

persons.Add(new person() { Id = 103, Subject = "New Meeting ", StartTime = new DateTime(2014, 4, 2, 4, 0, 20), EndTime = new DateTime(2014, 4, 2, 7, 0, 20), AllDay = false, Recurrence = false, RecurrenceRule = "FREQ=WEEKLY;COUNT=1;INTERVAL=1;BYDAY=MO,TU", RoomId = "1", OwnerId = "5", 	 Categorize = "2,3" });

// categorize data collection

List<Categorize> CategorizeValue = new List<Categorize>();

CategorizeValue.Add(new Categorize { text = "Blue Category", id = 1, color = "#7499e1", fontColor = "Red" });

CategorizeValue.Add(new Categorize { text = "Green Category", id = 2, color = "#7cce6e", fontColor = "White" });

CategorizeValue.Add(new Categorize { text = "Orange Category", id = 3, color = "#ffaa00", fontColor = "Green" });

ViewBag.datasource = persons;

ViewBag.categorize = CategorizeValue;

return View();

}

Public class person

{

Public int Id;

Public string Subject;

Public string RoomId;

Public string OwnerId;

Public string Categorize;

Public DateTime StartTime;

Public DateTime EndTime;

Public bool AllDay;

Public bool Recurrence;

Public string RecurrenceRule;

}



public class Categorize

{

public string text { set; get; }

public int id { set; get; }

public string fontColor { set; get; }

public string color { set; get; }

}

}

{% endhighlight %}

The output of the above code is illustrated as follows.

![](Categorize_images/Categorize_img1.png)



