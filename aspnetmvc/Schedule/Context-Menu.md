---
title: Schedule - Context Menu	
description: Default and Custom context menu options for appointments and cells in Scheduler
platform: ejmvc
control: schedule
documentation: ug
keywords: context-menu
---
# Context Menu

Scheduler provides default context menu options for both appointments as well as work cells. It also allows to define additional custom context menu options.

The options that are available under `ContextMenuSettings` are as follows,

* **Enable** - Enables/disables the context menu option in Scheduler.
* **MenuItems** - Contains the sub-menu collections related to both the appointment and cells.

## Default Menu Options

The menu items contains two separate collection based on the appointment and cells. 

### Appointment

The appointment collection includes the following options. 

<table>
<tr>
<td>
Open Appointment (default)</td></tr>
<tr>
<td>
Delete Appointment (default)</td></tr>
<tr>
<td>
Print Appointment</td></tr>
<tr>
<td>
Categorize</td></tr>
</table>

### Cells

The default options available within the cell collection includes - 

<table>
<tr>
<td>
New Appointment</td></tr>
<tr>
<td>
New Recurring Appointment</td></tr>
<tr>
<td>
Today</td></tr>
<tr>
<td>
Go to date</td></tr>
<tr>
<td>
Settings (View, TimeMode, Work Hours) </td></tr>
</table>

The following code snippet shows how to enable the context menu settings in Scheduler and to make use of it with default available options. 

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- List of Appointment menu options -->
    List<Appointment> AppMenu = new List<Appointment>();
    AppMenu.Add(new Appointment { Id = "open", Text = "Open Appointment" });
    AppMenu.Add(new Appointment { Id = "delete", Text = "Delete Appointment" });

    <!-- List of Cell menu options -->
    List<Cells> CellMenu = new List<Cells>();
    CellMenu.Add(new Cells { Id = "new", Text = "New Appointment" });
    CellMenu.Add(new Cells { Id = "recurrence", Text = "New Recurring Appointment" });
    CellMenu.Add(new Cells { Id = "today", Text = "Today" });
    CellMenu.Add(new Cells { Id = "goToDate", Text = "Go to date" });
    CellMenu.Add(new Cells { Id = "settings", Text = "Settings" });
    CellMenu.Add(new Cells { Id = "view", Text = "View", ParentId = "settings" });
    CellMenu.Add(new Cells { Id = "timeMode", Text = "TimeMode", ParentId = "settings" });
    CellMenu.Add(new Cells { Id = "view_Day", Text = "Day", ParentId = "view" });
    CellMenu.Add(new Cells { Id = "view_Week", Text = "Week", ParentId = "view" });
    CellMenu.Add(new Cells { Id = "view_Workweek", Text = "WorkWeek", ParentId = "view" });
    CellMenu.Add(new Cells { Id = "view_Month", Text = "Month", ParentId = "view" });
    CellMenu.Add(new Cells { Id = "timeMode_Hour12", Text = "12 Hour", ParentId = "timeMode" });
    CellMenu.Add(new Cells { Id = "timeMode_Hour24", Text = "24 Hour", ParentId = "timeMode" });
    CellMenu.Add(new Cells { Id = "workhours", Text = "Work Hours", ParentId = "settings" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .ContextMenuSettings(contextMenu => contextMenu.Enable(true).MenuItems(items => items.Appointment(AppMenu).Cells(CellMenu)))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
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

N> In agenda view, only the appointment menu items shows up in the context menu options. For default menu items, the id must be defined with the same value as mentioned in the above code example – as we have processed the menus based on this id within our source.


## Custom Menu Options


Apart from the default available options, it is also possible to add custom menu options to the context-menu of both the appointment and cell collection.

The following code example depicts how **to add the custom menu items** to the appointment and cell collection of the context menu settings.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- List of Appointment menu options -->
    List<Appointment> AppMenu = new List<Appointment>();
    AppMenu.Add(new Appointment { Id = "open", Text = "Open Appointment" });
    AppMenu.Add(new Appointment { Id = "delete", Text = "Delete Appointment" });
    AppMenu.Add(new Appointment { Id = "option1", Text = "User Option 1" });

    <!-- List of Cell menu options -->
    List<Cells> CellMenu = new List<Cells>();
    CellMenu.Add(new Cells { Id = "customOption", Text = "User Option" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .ContextMenuSettings(contextMenu => contextMenu.Enable(true).MenuItems(items => items.Appointment(AppMenu).Cells(CellMenu)))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
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

N> The **Id** given for the custom menu items **must be unique** in both the appointment and cell collection. 

## Handling Menu Actions

To define specific actions for a click made on the custom menu items, the client-side event `MenuItemClick` can be used as depicted in the below code example.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- List of Appointment menu options -->
    List<Appointment> AppMenu = new List<Appointment>();
    AppMenu.Add(new Appointment { Id = "open", Text = "Open Appointment" });
    AppMenu.Add(new Appointment { Id = "delete", Text = "Delete Appointment" });
    AppMenu.Add(new Appointment { Id = "option1", Text = "User Option 1" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .ContextMenuSettings(contextMenu => contextMenu.Enable(true).MenuItems(items => items.Appointment(AppMenu).Cells(CellMenu)))
        .ScheduleClientSideEvents(event => event.MenuItemClick("onMenuItemClick"))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
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

{% highlight js %}

function onMenuItemClick(args) {
    //args.events contains information of the clicked menu item.
    if (args.events.ID == "option1")
        alert("Custom menu clicked");
}

{% endhighlight %}

Also, it is possible to predict the target on which the right click is made, either on the cells or appointments with the use of the event `BeforeContextMenuOpen`. The below code example shows how to block the display of context menu when right clicked on the cells by setting **args.cancel** as **true**.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- List of Appointment menu options -->
    List<Appointment> AppMenu = new List<Appointment>();
    AppMenu.Add(new Appointment { Id = "open", Text = "Open Appointment" });
    AppMenu.Add(new Appointment { Id = "delete", Text = "Delete Appointment" });
    AppMenu.Add(new Appointment { Id = "option1", Text = "User Option 1" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .ContextMenuSettings(contextMenu => contextMenu.Enable(true).MenuItems(items => items.Appointment(AppMenu).Cells(CellMenu)))
        .ScheduleClientSideEvents(event => event.BeforeContextMenuOpen("beforeContextMenuOpen"))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
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

{% highlight js %}

function beforeContextMenuOpen(args) {
    //args.events.target – target information to depict either cell/appointment
    if ($(args.events.target).hasClass("e-workcells") || $(args.events.target).hasClass("e-monthcells"))
        args.cancel = true;
}

{% endhighlight %}

## Adding Categorize Option

To include the default categorize options within the context menu, it is necessary to enable the `CategorizeSettings` property as shown in the below code example.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- List of Appointment menu options -->
    List<Appointment> AppMenu = new List<Appointment>();
    AppMenu.Add(new Appointment { Id = "open", Text = "Open Appointment" });
    AppMenu.Add(new Appointment { Id = "delete", Text = "Delete Appointment" });
    AppMenu.Add(new Appointment { Id = "categorize", Text = "Categorize" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .ContextMenuSettings(contextMenu => contextMenu.Enable(true).MenuItems(items => items.Appointment(AppMenu).Cells(CellMenu)))
        .CategorizeSettings(cat => cat.Enable(true))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
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

N> The **Categorize** option must be added to the **Appointment** collections simply with an id "categorize", which displays on right clicking the appointments.

