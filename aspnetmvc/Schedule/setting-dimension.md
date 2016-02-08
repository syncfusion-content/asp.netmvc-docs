---
title: Setting dimension
description: Setting dimension for Schedule control
platform: ejmvc
control: schedule
documentation: ug
keywords: dimension, cell dimension, cell width, cell height 
---
# Setting Dimension

The dimension normally refers to the height and width of the element. With Scheduler, it is possible to set 2 kinds of dimensions.

* Scheduler dimension (Scheduler control height and width)
* Cell dimension (Scheduler cells height and width)

## Scheduler Dimension

The `Height` and `Width` properties can be defined to set the outer dimension of the Scheduler control.

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
        .Width("70%")
        .Height("500px")
        .CurrentDate(new DateTime(2015,11, 5))
)

{% endhighlight %}

N> The height and width properties accepts both **Pixel** and **Percentage** values.

## Scheduler Cell Dimensions

### Cell Height

The `CellHeight` property allows the Scheduler to set the height of the cells in pixels. The appointment height in vertical mode changes accordingly as per the cell size within which it renders.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CellHeight("40px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

N> In **Desktop** mode, the default height value of the cells is set to **20px**, whereas for **Mobile** mode – the Scheduler cells are rendered with **40px** by default.

## Cell Auto-Height

The height of the cells especially in timeline view can be made to adjust automatically based on its exceeding appointment count. It is controlled by an API named [showOverflowButton](/js/api/ejschedule#members:showOverflowButton) which accepts true or false value, denoting whether to enable/disable the cell auto-height adjusting option. To enable this option, set the value of `showOverflowButton` as `false` whereas its default value is `true`.

In **Vertical** view, the same functionality is made applicable only in the **Month View** whereas in **Horizontal** mode, it is applicable in all the views.

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
    .Width("100%")
    .Height("525px")
    .CurrentDate(new DateTime(2015, 11, 5))
    .CurrentView(CurrentView.Month)
    .ShowOverflowButton(false)
    .AppointmentSettings(fields => fields
        .Id("Id")
        .Subject("Subject")
        .StartTime("StartTime")
        .EndTime("EndTime")
        .Description("Description")
        .AllDay("AllDay")
        .Recurrence("Recurrence")
        .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

### Cell Width

The `CellWidth` property allows the Scheduler to set the width of the cells in pixels. The appointment width adjusts based on the cell width of the Scheduler.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CellWidth("97px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

N> When the **CellHeight** and **CellWidth** properties are set with some specific pixel values, the cell size does not adapt to the responsive behaviour of the Scheduler when it is resized either in desktop/mobile mode.

