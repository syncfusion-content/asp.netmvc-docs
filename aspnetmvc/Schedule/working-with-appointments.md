---
title: Working with appointments
description: Working with Scheduler appointments and its related options like Recurrence.
platform: ejmvc
control: schedule
documentation: ug
keywords: appointments, recurrence, recurring appointment, resize, drag and drop, search, categorize, priority, occurrence, reminder, filter and CRUD  
---
# Working with Appointments

An appointment represents a certain time interval in a schedule cell depicting a plan made for the specified time interval. 

## Appointment Types

The types of appointments available within Scheduler can be categorized as follows 

### Normal 

Represents an appointment that is created for a certain time interval in one or more number of days. If the normal appointment is created for more than 24 hours, then those longer appointments will be rendered on the all-day row.

N> If the normal appointment is to be created for two days (say from November 25, 2015 – 11.00 PM to November 26, 2015 2.00 AM) but less than 24 hour time interval, then the appointment is split into two partitions and will be displayed appropriately on both the days.

### All-Day 

Represents an appointment that is created for an entire day such as holiday events. It renders separately in All-day row, a separate place for all-day appointments. In Timeline (horizontal) view, all-day appointment renders in the usual work cells, as no all-day cells are present in that view.  

N> An all-day row is normally visible on the Scheduler, as the `ShowAllDayRow` property is set to true by default. 

### Recurrence

Represents an appointment that is created for a certain time interval that occurs repeatedly in a daily, weekly, monthly, yearly or every weekday basis at the same time interval based on the recurrence rule. The other available options and validations that can be performed on recurrence appointments can be referred from [here](/aspnetmvc/schedule/working-with-appointments#recurrence-options).

## CRUD operation 

Appointments play a dynamic role within the Schedule control with which the users mostly interact. You can manipulate (add/edit/delete/drag/resize) the required appointments that reveals one of the main purpose of the Schedule control.

### Add/Edit Appointments

The appointments can be added/edited in the Scheduler using any one of the following ways,

* Quick window
* Inline creation/editing
* Default appointment window
* [Context menu](/aspnetmvc/schedule/context-menu)
* Through programmatically

#### Quick Window


The Quick window usually pops out while single clicking on the Scheduler cells or appointments. It requires the user to enter the Subject to proceed with the appointment creation. It also includes an **Edit** **Appointment** option displayed at the bottom left corner – on selection which opens up the normal appointment window.

On single clicking the scheduler appointments, the pop-up that shows up contains the appointment information along with the other options that are listed below,

* Edit Appointment
* Edit Series (only for the recurrence appointments)
* Delete icon

The quick window option can be enabled/disabled by using `ShowQuickWindow` API, whereas its default value is set to **true**.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .ShowQuickWindow(false)
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

N> Select multiple cells either using mouse or keyboard access keys (<kbd>shift</kbd>+<kbd>arrow keys</kbd>) and press <kbd>enter</kbd> key, so that the quick window opens up for the selected date/time range.

Another way to disable the quick window option at dynamic time can be achieved through the `CellClick` and `AppointmentClick` events. The below code example shows the way to disable the quick appointment window only while clicking on the cells, but displays for appointments.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .ShowQuickWindow(true)
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
        .ScheduleClientSideEvents(event => event.CellClick("onCellClick"))
)

{% endhighlight %}

{% highlight js %}

function onCellClick(args) {
    args.cancel = true;
}

{% endhighlight %}


#### Inline Appointment Creation/Editing

Another easier way, for adding or editing the appointment’s subject alone can be achieved using inline Add/Edit support. It allows the user to add and edit the appointments inline.

To get familiar with inline Add mode, single click on any of the Scheduler cells or press `enter` key on the selected cells. When the inline adding mode is ON, a text box will get created within the clicked Scheduler cells with a blinking cursor in it, requiring the user to enter the subject of an appointment. Once the subject is entered, the appointment will be saved on pressing the `enter` key. 

To enable inline edit mode, single click on any of the existing appointment’s subject, so that the user can edit the subject of that appointment. The edited subject of that appointment is then updated on pressing the `enter` key.

The inline option can be enabled/disabled on Scheduler by using the `AllowInline` API, whereas its default value is set to **false**.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .AllowInline(true)
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

##### Enabling Inline Edit alone

It is possible to disable the inline appointment creation and enabling only the editing mode of inline by making use of the `CellClick` event. The below code example shows the way to disable the inline appointment creation while clicking on the cells, but appointments can be edited while clicking on it’s subject.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .AllowInline(true)
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
        .ScheduleClientSideEvents(event => event.CellClick("onCellClick"))
)

{% endhighlight %}

{% highlight js %}

function onCellClick(args) {
    args.cancel = true;
}

{% endhighlight %}


#### Default Appointment Window

The default appointment window is availed with options like 

* Subject
* Start and End Time
* All-Day
* TimeZone (for both Start and End time)
* Repeat options
* Description

The other additional options available are listed below for which the appropriate API’s are needed to be configured to display these options on the appointment window.

* Location ([ShowLocationField](/aspnetmvc/schedule/miscellaneous#showhide-location-field))
* Priority ([PrioritySettings](/aspnetmvc/schedule/working-with-appointments#priority))
* Categorize ([CategorizeSettings](/aspnetmvc/schedule/working-with-appointments#categorization))
* [Resources](/aspnetmvc/schedule/resources)    

The appointments can be created by double-clicking the Scheduler cells across the required time slots, which makes the Create Appointment window to pop-up. The start and end time fields will get automatically populated, according to the time-slot selection. Clicking on the done button in an appointment window will create the appointment for the selected time cells.

N> Select multiple cells both using mouse or keyboard access keys (<kbd>shift</kbd>+<kbd>arrow keys</kbd>) and press <kbd>Alt</kbd>+<kbd>N</kbd> key, so that the default appointment window opens up for the selected date/time range with the Start and End time fields automatically filled in.

To prevent the display of default appointment window on double clicking the Scheduler cells, either the `AppointmentWindowOpen` or `CellDoubleClick` event can be used, within which the **args.cancel** needs to be set to true. This behavior is depicted in the below code example.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
         .ScheduleClientSideEvents(event => event.AppointmentWindowOpen("onAppointmentWindowOpen"))
)

{% endhighlight %}

{% highlight js %}

function onAppointmentWindowOpen(args) {
    args.cancel = true;
}

{% endhighlight %}

#### Through Programmatically

You can add/edit the appointments dynamically through the public method `saveAppointment`. It accepts the JSON Object data (either a new or updated appointment object) as its argument.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
         .ScheduleClientSideEvents(event => event.AppointmentWindowOpen("onAppointmentWindowOpen"))
)
@Html.EJ().Button("add").Text("Add").ClientSideEvents(event => event.Click("addAppointment"))

{% endhighlight %}

{% highlight js %}

function addAppointment() {
    //appointment details 
    var appointment = {
        Subject: "Gym",
        StartTime: new Date("2015/11/7 03:30 AM"),
        EndTime: new Date("2015/11/7 04:30 AM")
    };

    //create the schedule object 
    var schObj = $("#Schedule1").data("ejSchedule");
    //pass the JSON object in the public method 
    schObj.saveAppointment(appointment);
}

{% endhighlight %}

### Delete Appointments

The appointments can be deleted in either of the following ways,

* Selecting an appointment and clicking the delete icon in the quick appointment window.
* Hovering the mouse over appointments and clicking on Inline delete option which is enabled by default for all the appointments.
* Selecting an appointment and pressing <kbd>Delete</kbd> key.
* Through Programmatically.

A pop-up with a confirmation message will get displayed before deleting an appointment, which can be either switched on/off using the API `ShowDeleteConfirmationDialog`. Also, the confirmation text in that pop-up can be customized as mentioned [here](/aspnetmvc/schedule/globalization-and-localization#localization:localizing-specific-words).

**For example**, to localize only the delete confirmation message in the delete window - 

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .ShowDeleteConfirmationDialog(true)
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

{% highlight html %}

<script>
var deleteCustomizationMessage = {
    // customize the confirmation message
    DeleteConfirmation: "Do you want to delete this Event?",
    // customize the delete window title
    MouseOverDeleteTitle: "Delete Event",
    // customize the recurrence delete window title
    RecurrenceDeleteTitle: "Delete Repeat Event"
};

// Extend only the required changes to the original locale collection
$.extend(ej.Schedule.Locale["en-US"], deleteCustomizationMessage);
</script>

{% endhighlight %}

N> All these CRUD operations on appointments (add/edit/delete) can also be done through the default [Context Menu](/aspnetmvc/schedule/context-menu#default-menu-options) options **Add Appointment**, **Edit Appointment** and **Delete Appointment** which is available, when context menu settings is enabled within Scheduler.

#### Through Programmatically

You can delete the appointments dynamically using the method `deleteAppointment`, which accepts the Guid of the appointment or complete appointment data as its argument. The Guid is availed as one of the appointment element’s attribute.

#### Example 1 - Using GUID 

The below code example depicts the way to delete the appointments using GUID programmatically by calling the **deleteAppointment** function within the `AppointmentClick` event, which triggers whenever the user clicks on an appointment.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
    @{
        <!-- Datasource for Appointments -->
        List<ScheduleFields> Appoint = new List<ScheduleFields>();
        Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
    }

    @(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
            .ScheduleClientSideEvents(event => event.AppointmentClick("onAppointmentClick"))
    )

{% endhighlight %}

{% highlight js %}

    function onAppointmentClick(args) {
        var schObj = $("#schedule").data("ejSchedule");
        schObj.deleteAppointment(args.appointment.Guid);
    }

{% endhighlight %}

#### Example 2 - Using Appointment object 

The below code example depicts the way to delete the appointments using appointment data programmatically by calling the **deleteAppointment** function within the `AppointmentClick` event, which triggers whenever the user clicks on an appointment.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
    @{
        <!-- Datasource for Appointments -->
        List<ScheduleFields> Appoint = new List<ScheduleFields>();
        Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
    }

    @(Html.EJ().Schedule("Schedule1")
            .Width("100%")
            .Height("525px")
            .CurrentDate(new DateTime(2014, 6, 2))
            .AppointmentSettings(fields => fields.Datasource(Appoint)
                .Id("Id")
                .Subject("Subject")
                .StartTime("StartTime")
                .EndTime("EndTime")
                .AllDay("AllDay")
                .Recurrence("Recurrence")
                .RecurrenceRule("RecurrenceRule"))
                .ScheduleClientSideEvents(event => event.AppointmentClick("onAppointmentClick"))
    )

{% endhighlight %}

{% highlight js %}

    function onAppointmentClick(args) {
        var schObj = $("#schedule").data("ejSchedule");
        schObj.deleteAppointment(args.appointment);
    }

{% endhighlight %}

## Handling Appointment Actions

It is possible to define some specific actions to take place before the CRUD operation occurs on the Scheduler appointments through the following available client-side events,

* BeforeAppointmentCreate
* BeforeAppointmentChange
* BeforeAppointmentRemove

**BeforeAppointmentCreate** – Triggers before saving a new appointment.

**BeforeAppointmentChange** – Triggers when an appointment is edited and before it is being updated to the dataSource.

**BeforeAppointmentRemove** – Triggers before deleting an existing appointment.

To stop the save, edit and delete actions on the Scheduler appointments, following code example can be used.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
        .ScheduleClientSideEvents(event => event.BeforeAppointmentCreate("onAppointmentSave").BeforeAppointmentChange("onAppointmentEdit").BeforeAppointmentRemove("onAppointmentDelete"))
)

{% endhighlight %}

{% highlight js %}

function onAppointmentSave(args) {
    args.cancel = true; // cancels the save action on appointments.
}

function onAppointmentEdit(args) {
    args.cancel = true; // cancels the edit action on appointments.
}

function onAppointmentDelete(args) {
    args.cancel = true; // cancels the delete action on appointments.
}

{% endhighlight %}

## Read Only

An interaction with the appointments of the Scheduler can be enabled/disabled through the `ReadOnly` property. When the `ReadOnly` property is set to `true`, it is not possible to do any actions on the appointments, but you can navigate between the schedule dates, views and can also be able to see the appointment details in the quick window. By default, this property is set to `false`.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .ReadOnly(true)
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

N> When the `ReadOnly` property is set to true – double clicking the cells will open the appointment window filled with appointment details, which can be allowed to view but cannot be edited or saved.

## Drag and Drop

The appointment time can be modified through the drag and drop behavior, by dragging and dropping it to the new location, so that the start time and end time of the appointment gets changed automatically. We can enable/disable the drag and drop functionality through the `AllowDragAndDrop` property. By default, it is set to `true`.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .AllowDragAndDrop(false)
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

### Handling Drag Actions Dynamically

The drag and drop functionality can be handled with the following three events,

* DragStart
* Drag
* DragStop

**dragStart** – Triggers when the appointments are started to drag from its source location.

**drag** – Triggers when the appointments are being dragged over.

**dragStop** – Triggers when the appointments are dropped on a destined location.

The following code example shows how to cancel the dragging functionality with the help of one of these events.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
        .ScheduleClientSideEvents(event=>event.DragStop("onDragStop"))
)

{% endhighlight %}

{% highlight js %}

function onDragStop(args) {
    args.cancel = true; // cancels the drag action on appointments.
}	

{% endhighlight %}

### External Drag and Drop

It is possible to drag and drop the external items to and fro the Scheduler control. This action is handled through the property `AppointmentDragArea` which specifies the draggable area which states whether the appointments can be dragged outside of the control or within it.

The following code example lets you dragging and dropping external items to and from the Scheduler control.

{% highlight html %}

<div class="row">
    <div class="col-md-2">
        <span class=""><b>Tutorials </b> </span>
        @Html.EJ().TreeView("drag").Items(items => {
            items.Add().Text("HTML").Expanded(true).Children(child => {
                child.Add().Text("Introduction");
                child.Add().Text("Editors");
                child.Add().Text("Styles");
                child.Add().Text("Formatting");
                child.Add().Text("Tables");
            });
        }).AllowDragAndDrop(true).AllowDropChild(false).AllowDropSibling(false).AllowDragAndDropAcrossControl(true).Width("auto").ClientSideEvents(s => s.NodeDropped("onDropped").NodeDragStart("onNodeDrag"))
    </div>
    <div class="col-md-9">
     @using MyProject.Models; // Here MyProject defines your project name to access the model class
        @{
            <!-- Datasource for Owners -->
            List<ResourceFields> resources = new List<ResourceFields>();
            resources.Add(new ResourceFields { Id = "1", Text = "Nancy", Color = "#f8a398" });
            resources.Add(new ResourceFields { Id = "3", Text = "Steven", Color = "#56ca95" });
            resources.Add(new ResourceFields { Id = "5", Text = "Michael", Color = "#51a0ed" });

            <!-- Datasource for Grouping -->
            List<String> Group = new List<String>();
            Group.Add("Owners");
        }
        @(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .AppointmentDragArea("body")
        .ShowCurrentTimeIndicator(false)
        .CurrentDate(new DateTime(2015, 11, 5))
        .Resources(res => { res.Field("OwnerId").Title("Owner").Name("Owners").AllowMultiple(true).ResourceSettings(fields => fields.Datasource(resources).Text("Text").Id("Id").Color("Color")).Add(); })
        .Group(gr => { gr.Resources(Group); })
        .ScheduleClientSideEvents(event => event.DragStop("onDragStop"))
        .AppointmentSettings(fields => fields.Datasource(Model)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .Description("Description")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule")
            .ResourceFields("OwnerId"))
        )
    </div>
</div>

<div id="customWindow" style="display: none">
    <form id="custom">
        <table width="100%" cellpadding="5">
            <tbody>
                <tr>
                    <td>Subject:</td>
                    <td colspan="2">
                        <input id="subject" type="text" value="" name="Subject" style="width: 100%" readonly />
                    </td>
                </tr>
                <tr>
                    <td>Description:</td>
                    <td colspan="2">
                        <textarea id="customDescription" name="Description" rows="3" cols="50" style="width: 100%; resize: vertical"></textarea>
                    </td>
                </tr>
                <tr>
                    <td>StartTime:</td>
                    <td>
                        @Html.EJ().DateTimePicker("StartTime").Width("150px")
                    </td>
                </tr>
                <tr>
                    <td>EndTime:</td>
                    <td>
                        @Html.EJ().DateTimePicker("EndTime").Width("150px")
                    </td>
                </tr>
                <tr>
                    <td>Resource:</td>
                    <td colspan="2">
                        <input id="resource" type="text" value="" name="Resource" style="width: 100%" readonly />
                    </td>
                </tr>
                <tr style="display: none">
                    <td>ownerId:</td>
                    <td colspan="2">
                        <input id="ownerId" type="text" name="OwnerId" />
                    </td>
                </tr>
            </tbody>
        </table>
    </form>
    <div>
        <button type="submit" onclick="cancel()" id="buttonCancel" style="float:right;margin-right:20px;margin-bottom:10px;">Cancel</button>
        <button type="submit" onclick="save()" id="buttonSubmit" style="float:right;margin-right:20px;margin-bottom:10px;">Save</button>
    </div>
</div>

{% endhighlight %}

{% highlight js %}

    $(function () {
        $("#customWindow").ejDialog({
            width: 600,
            height: "auto",
            position: { X: 400, Y: 200 },
            showOnInit: false,
            enableModal: true,
            title: "Create Appointment",
            enableResize: false,
            allowKeyboardNavigation: false,
            close: "clearFields"
        });
        $("#buttonCancel").ejButton({ width: '85px' });
        $("#buttonSubmit").ejButton({ width: '85px' });
    });

    function onNodeDrag(e) {
        if (e.targetElementData.parentId == "") return false;
    }

    function onDropped(e) {
        if ($(e.target).parents(".e-schedule").length != 0) {
            var scheduleObj = $("#Schedule1").data("ejSchedule");
            var index = $($(e.target).context).hasClass("e-workcells") || $($(e.target).context).hasClass("e-alldaycells") ? $($(e.target).context).index() : $($(e.target).context).hasClass("e-alldaycells") ? $($(e.target).context).index() : 7 - ((parseInt($($(e.target).context).index() / 7) + 1) * 7 - $($(e.target).context).index()) + ($($(e.target).context).parent().index() * 7);
            if (scheduleObj.model.orientation == "horizontal") {
                index = scheduleObj.model.showTimeScale ? scheduleObj.currentView() !== "month" && !(scheduleObj._isCustomView()) ? Math.floor(index / ((scheduleObj.model.endHour - scheduleObj.model.startHour) * 2)) : index : $(e.event.target).index();

            }
            var renderDate = (scheduleObj.model.orientation == "horizontal" && scheduleObj.currentView() == "month") ? scheduleObj.monthDays : scheduleObj.model.orientation == "vertical" ? scheduleObj.dateRender : scheduleObj._dateRender;
            renderDate = scheduleObj.model.orientation == "horizontal" && scheduleObj.currentView() == "customview" && scheduleObj._dateRender.length <= 7 ? scheduleObj._dateRender : renderDate;
            var curDate = new Date(renderDate[index]);

            var _target = $($(e.target).context);
            if ($(_target).hasClass("e-workcells") && (scheduleObj.model.showTimeScale) && scheduleObj.currentView() !== "month" && !(scheduleObj._isCustomView())) {
                var time = scheduleObj.model.orientation == "vertical" ? scheduleObj.model.startHour + ($(e.event.target).parent().index() / 2) : scheduleObj.model.startHour + (($(e.event.target).index() - (((scheduleObj.model.endHour - scheduleObj.model.startHour) * 2) * index)) / 2);
                var timeMin = time.toString().split(".");
                var cur_StartTime = new Date(curDate).setHours(parseInt(timeMin[0]), parseInt(timeMin[1]) == 5 ? 30 : 00);
                var min = (parseInt(new Date(cur_StartTime).getHours()) == 23 && parseInt(new Date(cur_StartTime).getMinutes()) == 30) ? new Date(cur_StartTime).getMinutes() + 29 : new Date(cur_StartTime).getMinutes() + 30;
                var cur_EndTime = new Date(new Date(cur_StartTime).setMinutes(min));
            }
            else if ($(_target).hasClass("e-workcells") && scheduleObj.model.orientation == "horizontal" && scheduleObj.currentView() == "month") {
                var cur_StartTime = new Date(new Date(curDate).setHours(0, 0));
                var cur_EndTime = new Date(new Date(curDate).setHours(23, 59));
            }
            else {
                var cur_StartTime = new Date(new Date(curDate).setHours(0, 0));
                var cur_EndTime = new Date(new Date(curDate).setHours(23, 59));
                scheduleObj._appointmentAddWindow.find(".allday").ejCheckBox({ checked: true });
            }

            var StartDate = new Date(cur_StartTime);
            var StartTime = new Date(cur_StartTime);
            var endTime = cur_EndTime;

            // To find the resource details
            var resource = scheduleObj._getResourceValue($($(e.target).context));

            // custom appointment window

            $("#subject").val(e.droppedElementData.text);
            $("#customDescription").val(e.droppedElementData.text);
            $("#StartTime").ejDateTimePicker({ value: new Date(StartTime) });
            $("#EndTime").ejDateTimePicker({ value: new Date(endTime) });
            $("#resource").val(resource.Text);
            $("#ownerId").val(resource.Id);
            $("#customWindow").ejDialog("open");
        }
    }

    function save() {
        var obj = {};
        var formElement = $("#customWindow").find("#custom").get(0);
        for (var index = 0; index < formElement.length; index++) {
            var columnName = formElement[index].name, $element = $(formElement[index]);
            if (columnName != undefined) {
                if (columnName == "Subject")
                    var value = formElement[index].value;
                if (columnName == "Description")
                    value = formElement[index].value;
                if (columnName == "StartTime")
                    value = new Date(formElement[index].value);
                if (columnName == "EndTime")
                    value = new Date(formElement[index].value);
                if (columnName == "OwnerId")
                    value = formElement[index].value;
                if (columnName != "Resource")
                    obj[columnName] = value;
            }

        }
        $("#customWindow").ejDialog("close");
        var object = $("#Schedule1").data("ejSchedule");
        object.saveAppointment(obj);
    }

    function cancel() {
        $("#customWindow").ejDialog("close");
    }

    function onDragStop(args) {
        if ($(args.event.target).parents(".e-treeview").length != 0) {
            $("#drag").ejTreeView({ allowDropChild: true, allowDropSibling: true });
            treeObj = $("#drag").ejTreeView('instance');
            var newNode = { id: args.appointment.Id, text: args.appointment.Subject };
            treeObj.addNode(newNode, $(args.event.target));
            args.cancel = true;
        }
    }

{% endhighlight %}

## Resize

Resizing an appointment is another way to change its start and end time. Mouse hover on the appointments, so that the resizing handlers gets displayed on either sides of the appointment which allows resizing. The resizing functionality can be enabled/disabled by setting the `EnableAppointmentResize` property. By default it is set to `true`.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .EnableAppointmentResize(false)
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

### Handling Resize Actions Dynamically

The appointment resizing functionality can be handled through the following three events,

* ResizeStart
* Resize
* ResizeStop

**ResizeStart** – Triggers when the appointments are started resizing from its original time.

**Resize** – Triggers when the appointment resizing is in progress.

**ResizeStop** – Triggers when the appointment resizing is done.

The following code example shows how to cancel the resizing functionality with the help of one of these events.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
        .ScheduleClientSideEvents(event=>event.ResizeStart("onResizeStart"))
)

{% endhighlight %}

{% highlight js %}

function onResizeStart(args) {
    args.cancel = true; // Blocks the resize action on appointments.
}

{% endhighlight %}

## Categorization

It allows to differentiate the appointments with various categorize options and individual colors. You can also denote the status of the appointments using this categorize option and can specify your own user-defined category collection. It is also possible to select multiple categorize for a single appointment.

### Categorize Settings

The `CategorizeSettings` holds the below categorize related properties such as,

* `Enable` - It accepts true or false value, denoting whether to enable/disable the categorize option. Its default value is `false`.
* `AllowMultiple` – It enables or disables the multiple selection of categories for each appointments in the appointment window as well as in the context menu. Its default value is `false`.
* `DataSource` – Binds the categorize dataSource collection. This property should be assigned with the JSON data array collection or instance of [ej.DataManger](/aspnetmvc/datamanager/overview).

We have below 6 default values for Categorize dataSource collection. 

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for CategorizeSettings -->
    List<CategorizeSettings> CategorizeValue = new List<CategorizeSettings>();
    CategorizeValue.Add(new CategorizeSettings { Text = "Blue Category", Id = "1", Color = "#43b496", FontColor = "#ffffff" });
    CategorizeValue.Add(new CategorizeSettings { Text = "Green Category", Id = "2", Color = "#7f993e", FontColor = "#ffffff" });
    CategorizeValue.Add(new CategorizeSettings { Text = "Orange Category", Id = "3", Color = "#cc8638", FontColor = "#ffffff" });
    CategorizeValue.Add(new CategorizeSettings { Text = "Purple Category", Id = "4", Color = "#ab54a0", FontColor = "#ffffff" });
    CategorizeValue.Add(new CategorizeSettings { Text = "Red Category", Id = "5", Color = "#dd654e", FontColor = "#ffffff" });
    CategorizeValue.Add(new CategorizeSettings { Text = "Yellow Category", Id = "6", Color = "#d0af2b", FontColor = "#ffffff" });
}

{% endhighlight %}

The below categorize fields holds the appropriate column names from the dataSource - 

<table>
<tr>
<th>
Field name<br/><br/></th><th>
Description<br/><br/></th></tr>
<tr>
<td>
Id<br/><br/></td><td>
It holds the binding name for <b>Id</b> field in the categorize dataSource<br/><br/></td></tr>
<tr>
<td>
Text<br/><br/></td><td>
It holds the binding name for <b>Text</b> field in the categorize dataSource<br/><br/></td></tr>
<tr>
<td>
Color<br/><br/></td><td>
It holds the binding name for <b>Color</b> field in the categorize dataSource.<br/><br/></td></tr>
<tr>
<td>
FontColor<br/><br/></td><td>
It holds the binding name for <b>FontColor</b> field in the categorize dataSource. This font color apply in the appointment.<br/><br/></td></tr>
</table>

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- Datasource for CategorizeSettings -->
    List<CategorizeSettings> CategorizeValue = new List<CategorizeSettings>();
    CategorizeValue.Add(new CategorizeSettings { Text = "Blue Category", Id = "1", Color = "#43b496", FontColor = "#ffffff" });
    CategorizeValue.Add(new CategorizeSettings { Text = "Green Category", Id = "2", Color = "#7f993e", FontColor = "#ffffff" });
    CategorizeValue.Add(new CategorizeSettings { Text = "Orange Category", Id = "3", Color = "#cc8638", FontColor = "#ffffff" });
    CategorizeValue.Add(new CategorizeSettings { Text = "Purple Category", Id = "4", Color = "#ab54a0", FontColor = "#ffffff" });
    CategorizeValue.Add(new CategorizeSettings { Text = "Red Category", Id = "5", Color = "#dd654e", FontColor = "#ffffff" });
    CategorizeValue.Add(new CategorizeSettings { Text = "Yellow Category", Id = "6", Color = "#d0af2b", FontColor = "#ffffff" });
}
@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .CategorizeSettings(fields => fields.Datasource(CategorizeValue).Enable(true).AllowMultiple(true).Id("Id").Text("Text").Color("Color").FontColor("FontColor"))
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

## Priority

This option prioritize the appointments based on its importance and it can be differentiated with each individual icons/images. By default, there are some specific set of default priority collection and you can also customize it with your own priority collection.

### Priority Settings

The `PrioritySettings` holds the below priority related properties such as,

* `Enable` - It accepts true or false value, denoting whether to enable/disable the priority option. Its default value is **false**.
* `Template` – Customize the priority icon/images using template options.
* `DataSource` – binds the priority dataSource collection. This property should be assigned with the JSON data array collection or instance of [ej.DataManger](/aspnetmvc/datamanager/overview). 

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for PrioritySettings -->
    List<PrioritySettings> PriorityValue = new List<PrioritySettings>();
    PriorityValue.Add(new PrioritySettings { Text = "None", Value = "none" });
    PriorityValue.Add(new PrioritySettings { Text = "High", Value = "high" });
    PriorityValue.Add(new PrioritySettings { Text = "Medium", Value = "medium" });
    PriorityValue.Add(new PrioritySettings { Text = "Low", Value = "low" });
}

{% endhighlight %}

The below priority fields holds the appropriate column names from the dataSource,

<table>
<tr>
<th>
Field name<br/><br/></th><th>
Description<br/><br/></th></tr>
<tr>
<td>
Text<br/><br/></td><td>
It holds the binding name for <b>text</b> field in the priority dataSource<br/><br/></td></tr>
<tr>
<td>
Value<br/><br/></td><td>
It holds the binding name for <b>value</b> field in the priority dataSource.<br/><br/></td></tr>
</table>

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- Datasource for PrioritySettings -->
    List<PrioritySettings> PriorityValue = new List<PrioritySettings>();
    PriorityValue.Add(new PrioritySettings { Text = "None", Value = "none" });
    PriorityValue.Add(new PrioritySettings { Text = "High", Value = "high" });
    PriorityValue.Add(new PrioritySettings { Text = "Low", Value = "low" });
}
@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .PrioritySettings(fields => fields.Datasource(PriorityValue).Enable(true).Text("Text").Value("Value"))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Priority("Priority")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

## Search or Filter Appointments

### Appointment Search

The public method `searchAppointments` is used to search the appointments in the Scheduler dataSource. It contains the below four arguments such as search string, search field, filter operator and ignore case.

**searchString** - It is used to search the given word/sentence within the appointment data.

**fields** - It is the field with which the search operation takes place. It’s an optional argument.

**filterOperator** – It denotes the filter type like `contains`, `greaterthan` or `lessthan`. It’s an optional argument.

**ignoreCase** – It is a boolean value to set the search string as case sensitive or not. It’s an optional argument.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
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

{% highlight html %}

<div id="grid1" />
<input id="txtSearch" type="text" placeholder="Search Appointments" />
<button id="search" onclick="onSearch()">Search</button>

<script>
    function onSearch() {
        var _searchString = $("#txtSearch").val();
        var schObj = $("#Schedule1").data("ejSchedule");
        // method to retrieve the appointment based on search string
        var result = schObj.searchAppointments(_searchString);
        showResult(result, _searchString);
    }

    // method to show the result in a grid
    function showResult(list, _searchString) {
        if (!ej.isNullOrUndefined(list) && list.length != 0 && _searchString != "") {
            $("#grid1").show();
            $("#grid1").data("ejGrid") && $("#grid1").ejGrid("destroy");
            $("#grid1").ejGrid({
                allowScrolling: true,
                dataSource: list,
                allowPaging: true
            });
        }
    }
</script>

{% endhighlight %}

### Appointment Filters

The appointments can be filtered or shortlisted based on the simple or complex conditions with four available properties such as **field**, **operator**, **value** and **predicate** which is passed to the public method `filterAppointments`.

**field** - It is the field, with which the search operation takes place. It’s an optional argument.

**operator** – It is generally used to specify the `filter` type. 

**value** – It is the filter keyword based on which the records are filtered.

**predicate** – To add more than one conditional query, need to use `and`, `or` `predicate`.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
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

{% highlight html %}

<div id="grid1" />
<input id="txtSearch" type="text" placeholder="Search Appointments" />
<button id="search" onclick="onFilter()">Filter</button>

<script>
    function onFilter() {
        // Add the filter data as like in the below format
        var filter = [{
            field: "Subject", // field configure
            operator: "contains",
            value: "Music",
            predicate: "or" // predicate 
        }, {
            field: "Subject", // field configure
            operator: "contains",
            value: "School",
            predicate: "or" // predicate
        }];

        var schObj = $("#Schedule1").data("ejSchedule");
        // Method to get the Filtered appointment
        var result = schObj.filterAppointments(filter);
        showResult(result);
    }

    // method to show the result in a grid
    function showResult(list, _searchString) {
        if (!ej.isNullOrUndefined(list) && list.length != 0 && _searchString != "") {
            $("#grid1").show();
            $("#grid1").data("ejGrid") && $("#grid1").ejGrid("destroy");
            $("#grid1").ejGrid({
                allowScrolling: true,
                dataSource: list,
                allowPaging: true
            });
        }
    }
</script>

{% endhighlight %}

## Recurrence Options

There are scenarios where you require the same appointments to be repeatedly created for multiple days on daily, weekly, monthly, and yearly or on every weekday basis.  

In appointment data collection, **Recurrence** and **RecurrenceRule** are dependent fields. While creating or binding the recurrence appointment, the **Recurrence** field is set to **true** and **RecurrenceRule** contains recurrence pattern in string format.

### Recurrence Rule

The recurrence appointments are created based on the recurrence rule. The RecurrenceRule is a string value that contains the details of the recurrence appointments like 

* repeat type - daily/weekly/monthly/yearly/every weekday 
* how many times it needs to be repeated 
* the interval duration
* the time period to render the appointment, etc.,

It has the following properties based on which the recurrence appointments are rendered in the Schedule control with its respective time period.

<table>
<tr>
<th>
S.No<br/><br/></th><th>
Property<br/><br/></th><th>
Purpose<br/><br/></th></tr>
<tr>
<td>
1<br/><br/></td><td>
FREQ<br/><br/></td><td>
Maintains the Repeat type value of the appointment. <br/><br/>(<b>Example</b>: Daily, Weekly, Monthly, Yearly, Every week day)<br/><br/>Example: <b>FREQ=DAILY</b>;INTERVAL=1<br/><br/></td></tr>
<tr>
<td>
2<br/><br/></td><td>
INTERVAL<br/><br/></td><td>
Maintains the Repeat type value of the appointment. <br/><br/>(<b>Example</b>: Daily, Weekly, Monthly, Yearly, Every weekday)<br/><br/>Example: <b>FREQ=DAILY</b>;INTERVAL=1<br/><br/></td></tr>
<tr>
<td>
3<br/><br/></td><td>
COUNT<br/><br/></td><td>
It holds the appointment’s count value. <br/><br/><b>For example</b>, When the recurrence appointment count value is 10, which means that 10 instances of appointments are created in the recurrence series.<br/><br/>Example: FREQ=DAILY;INTERVAL=1;<b>COUNT=10</b><br/><br/></td></tr>
<tr>
<td>
4<br/><br/></td><td>
UNTIL<br/><br/></td><td>
This property is used to store the recurrence end date value. <br/><br/><b>For example</b>, when you set the end date of appointment as 11/30/2015, the UNTIL property holds the end date value denoting when the recurrence actually ends.<br/><br/>Example: FREQ=DAILY;INTERVAL=1;<b>UNTIL=11/30/2015</b><br/><br/></td></tr>
<tr>
<td>
5<br/><br/></td><td>
BYDAY<br/><br/></td><td>
It holds the <b>DAY</b> values, representing on which the appointments actually renders. <br/><br/><b>For example</b>, Create the weekly appointment, and select the day(s) from the day options (Monday/Tuesday/Wednesday/Thursday/Friday/Saturday/Sunday). When Monday is selected, the first two letters of the selected day “MO” is saved in the <b>BYDAY</b> property. When multiple days are selected, the values are separated by commas.<br/><br/>Example: FREQ=WEEKLY;INTERVAL=1;<b>BYDAY=MO,WE</b>;COUNT=10<br/><br/></td></tr>
<tr>
<td>
6<br/><br/></td><td>
BYMONTHDAY<br/><br/></td><td>
This property is used to store the date value of the Month, while creating the Month recurrence appointment.<br/><br/><b>For example</b>, when you create a Monthly recurrence appointment for every 3rd day of the month, then <b>BYMONTHDAY</b> holds the value 3 and creates the appointment on 3rd day of every month.<br/><br/>Example: FREQ=MONTHLY;<b>BYMONTHDAY=3</b>;INTERVAL=1;COUNT=10<br/><br/></td></tr>
<tr>
<td>
7<br/><br/></td><td>
BYMONTH<br/><br/></td><td>
This property is used to store the index value of the selected Month while creating the yearly appointments.<br/><br/><b>For example</b>, when you create the yearly appointment on June month, the index value of June month 6 will get stored in the BYMONTH field. The appointment is created on every 6th month of a year.<br/><br/>Example: FREQ=YEARLY;BYMONTHDAY=16;<b>BYMONTH=6</b>;INTERVAL=1;COUNT=10<br/><br/></td></tr>
<tr>
<td>
8<br/><br/></td><td>
BYSETPOS<br/><br/></td><td>
This property is used to store the index value of the week. <br/><br/><b>For example</b>, when you create the monthly appointment in second week of a month, the index value of the second week (2) is stored in BYSETPOS.<br/><br/>Example: FREQ=MONTHLY;BYDAY=MO;<b>BYSETPOS=2</b>;UNTIL=8/11/2015<br/><br/></td></tr>
<tr>
<td>
9<br/><br/></td><td>
WKST<br/><br/></td><td>
This property is used to store the start day value of a week.<br/><br/><b>For example</b>, when you render the workweek the “WKST” value is Monday.<br/><br/></td></tr>
<tr>
<td>
10 <br/><br/></td><td>
EXDATE<br/><br/></td><td>
EXDATE is used to hold the modified appointment date details (date value) in the recurrence appointment series.<br/><br/><b>For example</b>, when you change the recurrence appointment instance under the date “6/19/2015”, then this date is added to the recurrence rule EXDATE field. “EXDATE” is also used to differentiate the edited occurrence of the recurrence series for some internal process while doing the “Edit Series or Delete series” actions.<br/><br/>Example: FREQ=WEEKLY;BYDAY=MO,TU,WE,TH,FR;COUNT=10;<b>EXDATE=6/18/2015,6/20/2015</b>;RECUREDITID=1651<br/><br/></td></tr>
<tr>
<td>
11<br/><br/></td><td>
RECUREDITID<br/><br/></td><td>
This property contains the Parent Id value of the edited appointment. It is used to track the edited appointment occurrence with its parent recurrence appointment series.<br/><br/><b>For example</b>, when you edit the particular occurrence of the recurrence appointment series, the “RECUREDITID” is added to that edited appointment depicting its parent Id.<br/><br/>Example:<br/><br/>FREQ=WEEKLY;BYDAY=MO,TU,WE,TH,FR;COUNT=10;EXDATE=6/18/2015,6/20/2015;<b>RECUREDITID=1651</b><br/><br/></td></tr>
</table>
To know more about other possible combinations of above specified recurrence rule properties, refer [here](http://www.syncfusion.com/kb/3719/what-is-recurrencerule-in-the-schedule-control).

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "FREQ=DAILY;INTERVAL=1;COUNT=5" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .Description("Description")
            .AllDay("AllDay")
            // Recurrence mapper field
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

### Recurrence Validation

The default recurrence validation has been included for recurrence appointments similar to the one available in outlook. The validation occurs during the recurrence appointment creation, drag and drop or resizing of the recurrence appointments and also if any single occurrence changes. The validation can be disabled by setting the `EnableRecurrenceValidation` to `false`.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "FREQ=DAILY;INTERVAL=1;COUNT=5" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .EnableRecurrenceValidation(false) // Disable Recurrence Validation
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .Description("Description")
            .AllDay("AllDay")
            // Recurrence mapper field
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

N> You can parse the **RecurrenceRule** of an appointment from the server-side by making use of a new generic utility class **RecurrenceHelper**. Refer this [KB document](https://www.syncfusion.com/kb/5390/how-to-parse-the-recurrencerule-in-server-side).

### Recurrence Edit and Delete options

The recurring appointments can be edited or deleted in three ways as below:

* Single occurrence
* Following appointments
* Entire series

#### Single occurrence

When an option "Only this Appointment" is selected, a single occurrence of the recurrence appointment alone will be edited or deleted.

#### Following appointments

When an option "Following Appointments" is selected, all the following events of the recurrence appointment from the current instance will be edited or deleted. The previous instances of the recurrence appointment before this current instances will be retained as it is on the Scheduler.

#### Entire series

The entire recurrence series will be edited / deleted, on selecting this option.

## Reminder

Reminder option notifies all the appointments before some specific time. By default, it notifies before 5 minutes. Each and every appointment triggers the `Reminder` event and can utilize this event for other user actions like mailing particular event to someone or to do any kind of manipulations with the reminder appointments and so on. The `ReminderSettings` includes the following 2 properties namely,

* **Enable** - To enable the reminder settings of the Schedule control, set the **Enable** property as `true` within the `Reminder`

* **AlertBefore** - Accepts the integer value to denote the time, before how long the reminder should be notified to the user.

{% highlight razor %}

@using MyProject.Models; // Here MyProject defines your project name to access the model class
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "FREQ=DAILY;INTERVAL=1;COUNT=5" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .ReminderSettings(rem => rem.Enable(true).AlertBefore(10))
        .ScheduleClientSideEvents(event => event.Reminder("reminderCustom"))
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

{% highlight razor %}

function reminderCustom(args) {
    alert("Reminder Appointment");
}
    
{% endhighlight %}

N>  Whenever the reminder setting is enabled in the Scheduler with some specific value (in minutes) assigned to the **AlertBefore** property, the **Reminder** event gets triggered before this specified value. It includes the reminder appointment’s entire information within its arguments.

## Block Time Intervals

It allows to block the particular timeslots in Schedule. When specific timeslots are blocked, the appointments that lies in that range can either be made read-only or else can be allowed to interact with the users based on the value assigned to the `IsBlockAppointment` property.

### Blockout Settings

The `BlockoutSettings` holds the below block intervals related properties such as,

* `Enable` - It accepts true or false value, denoting whether to enable/disable the block intervals option. It's default value is `false`.
* `TemplateId` – It applies the template design to block the intervals.
* `Datasource` – Binds the block intervals dataSource collection. This property should be assigned either with the JSON data array collection or instance of DataManager (`ej.DataManager`).

The below blockout fields holds the appropriate column names from the dataSource - 

<table>
<tr>
<th>
Field name<br/><br/></th><th>
Description<br/><br/></th></tr>
<tr>
<td>
Id<br/><br/></td><td>
It holds the binding name for <b>Id</b> field in the blockout dataSource<br/><br/></td></tr>
<tr>
<td>
Subject<br/><br/></td><td>
It holds the binding name for <b>Subject</b> field in the blockout dataSource<br/><br/></td></tr>
<tr>
<td>
StartTime<br/><br/></td><td>
It holds the binding name for <b>StartTime</b> field in the blockout dataSource.<br/><br/></td></tr>
<tr>
<td>
EndTime<br/><br/></td><td>
It holds the binding name for <b>EndTime</b> field in the blockout dataSource.<br/><br/></td></tr>
<tr>
<td>
IsBlockAppointment<br/><br/></td><td>
It holds the binding name for <b>IsBlockAppointment</b> field in the blockout dataSource.<br/><br/></td></tr>
<tr>
<td>
IsAllDay<br/><br/></td><td>
It holds the binding name for <b>IsAllDay</b> field in the blockout dataSource.<br/><br/></td></tr>
<tr>
<td>
ResourceId<br/><br/></td><td>
It holds the binding name for <b>ResourceId</b> field in the blockout dataSource.<br/><br/></td></tr>
<tr>
<td>
CustomStyle<br/><br/></td><td>
It holds the binding name for <b>CustomStyle</b> field in the blockout dataSource.<br/><br/></td></tr>
</table>
The below example depicts the appointment fields accepting the string type mapper fields.

Create a new Class to define the block intervals to be passed to the Scheduler as mentioned below,

{% highlight c# %}
    
    public class BlockData
    {
        public int Id { get; set; }
        public string Subject { get; set; }
        public DateTime StartTime { get; set; }
        public DateTime EndTime { get; set; }
        public Boolean IsBlockAppointment { get; set; }
        public string ResourceId { get; set; }
        public bool IsAllDay { get; set; }
    }
    
{% endhighlight %}

{% highlight razor %}

    @using MyProject.Models; // Here MyProject defines your project name to access the model class
    @{
        <!-- Datasource for Block Intervals -->
        List<BlockData> blockData = new List<BlockData>();
        blockData.Add(new BlockData { Id = 1, Subject = "Service", StartTime = new DateTime(2015, 11, 10, 9, 00, 00), EndTime = new DateTime(2015, 11, 10, 10, 00, 00), IsBlockAppointment = true });
        blockData.Add(new BlockData { Id = 2, Subject = "Maintenance", StartTime = new DateTime(2015, 11, 11, 11, 00, 00), EndTime = new DateTime(2015, 11, 11, 13, 00, 00), IsBlockAppointment = true });
    }

    @(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 10))
        .BlockoutSettings(fields => fields.Enable(true)
            .Datasource(blockData)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .IsBlockAppointment("IsBlockAppointment"))        
        )

{% endhighlight %}


### Blocking Appointments

The Appointments that lies within the blocked time range can be restricted to perform CRUD operations in it and can be made read-only. This can be achieved by setting `IsBlockAppointment` property to true.


{% highlight razor %}

    @using MyProject.Models; // Here MyProject defines your project name to access the model class
    @{
        <!-- Datasource for Block Intervals -->
        List<BlockData> blockData = new List<BlockData>();
        blockData.Add(new BlockData { Id = 1, Subject = "Service", StartTime = new DateTime(2015, 11, 10, 9, 00, 00), EndTime = new DateTime(2015, 11, 10, 10, 00, 00), IsBlockAppointment = true });        
    }

    @(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 10))
        //Configure the blockout settings
        .BlockoutSettings(fields => fields.Enable(true)
            .Datasource(blockData)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            //Bind the block appointment field in datasource                    
            .IsBlockAppointment("IsBlockAppointment"))
        )

{% endhighlight %}

### Customizing block time intervals

The `BlockoutSettings` holds the below properties to customize the block intervals such as,

* `TemplateId` - Template design that applies on the block intervals.
* `CustomStyle` - The custom CSS that applies on the blocked intervals.

{% highlight razor %}

    @using MyProject.Models; // Here MyProject defines your project name to access the model class
    @{
        <!-- Datasource for Block Intervals -->
        List<BlockData> blockData = new List<BlockData>();
        blockData.Add(new BlockData { Id = 1, Subject = "Service", StartTime = new DateTime(2015, 11, 10, 9, 00, 00), EndTime = new DateTime(2015, 11, 10, 10, 00, 00), IsBlockAppointment = true });        
    }

    @(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 10))
        //Configure the blockout settings
        .BlockoutSettings(fields => fields.Enable(true)
            .TemplateId("#blockTemplate")
            .Datasource(blockData)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .IsBlockAppointment("IsBlockAppointment"))
        )

{% endhighlight %}

{% highlight html %}

<!--Template to apply block intervals-->
<script id="blockTemplate" type="text/x-jsrender">
   <div style="height:100%">
      <div>{{:Subject}}</div>
   </div>
</script>

{% endhighlight %}

### Blocking time interval based on resources

* `ResourceId` property used within the `BlockoutSettings` which accepts the resource id's can be used to apply the block intervals based on the resources.

{% highlight razor %}

    @using MyProject.Models; // Here MyProject defines your project name to access the model class
    @{
        <!-- Datasource for Block Intervals -->
        List<BlockData> blockData = new List<BlockData>();
        blockData.Add(new BlockData { Id = 1, Subject = "Service", StartTime = new DateTime(2015, 11, 10, 9, 00, 00), EndTime = new DateTime(2015, 11, 10, 10, 00, 00), IsBlockAppointment = true, ResourceId = "1" });        
    
        <!-- Datasource for Appointments -->
        List<ScheduleData> Appoint = new List<ScheduleData>();
        Appoint.Add(new ScheduleData { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 11, 10, 00, 00), EndTime = new DateTime(2015, 11, 11, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "",OwnerId="1" });

        <!-- Define the Group -->
        List<String> Group = new List<String>();
        Group.Add("Owners");

        <!-- Datasource for Owners -->
        List<ResourceFields> Owner = new List<ResourceFields>();
        Owner.Add(new ResourceFields { Id = "1", Text = "Nancy", Color = "#f8a398", GroupId = "1" });
        Owner.Add(new ResourceFields { Id = "2", Text = "Steven", Color = "#56ca95", GroupId = "1" });
    }
    @(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 10))
         //Configure the blockout settings
        .BlockoutSettings(fields => fields.Enable(true)
            .Datasource(blockData)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .IsBlockAppointment("IsBlockAppointment")
            //resource id mapper field
            .ResourceId("ResourceId"))
        .Group(gr => { gr.Resources(Group); })
        .Resources(res =>
        {
            res.Field("OwnerId").Title("Owner").Name("Owners").AllowMultiple(true).ResourceSettings(fields => fields.Datasource(Owner).Text("Text").Id("Id").Color("Color")).Add();
        })
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .Description("Description")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule")
            .ResourceFields("OwnerId"))
        )

{% endhighlight %}

