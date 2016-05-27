---
title: Schedule - Template
description: Customize Scheduler with various available template options
platform: ejmvc
control: schedule
documentation: ug
keywords: appointment template, template, cell template, resource header 
---
# Template

Template is applicable to all the below specified elements of the Scheduler,

* Appointments
* Cells
* Date header
* Resource header
* Priority field
* TimeScale
* Date and time columns in Agenda view
* Tooltip

## Appointment Template

The template design that applies on for the Scheduler appointments. The field names that are mapped from the dataSource to the appropriate field properties within the `AppointmentSettings` can be accessed within the template.

Apart from the dataSource field names, the template can also access the current view of the Scheduler using the name **View** – which can contain either of the following values in lowercase. 

* day
* week
* workweek
* agenda
* month
* customview

It is controlled by an API named `AppointmentTemplateId` which accepts the id value of the template design block preceded by a symbol **#**.

Usually, the appointments are displayed with its **Subject** and **Start/End time** on the Scheduler. If suppose, the subject needs to be accompanied with location text, it can be done with the following code example.

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
        .CurrentDate(new DateTime(2015, 11, 5))
        .AppointmentTemplateId("#apptemplate")
        .AppointmentSettings(fields => fields.Datasource(Model)
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

<!-- Template for Appointment -->
<script id="apptemplate" type="text/x-jsrender">
    {{"{{"}}if View !== "agenda"{{}}}}
    <div style="height:100%; background-color:orange; margin-left: 5px;">
        <div style="margin-left: 2px;">{{"{{"}}:Subject{{}}}}</div>
        <div style="margin-left: 2px;">{{"{{"}}:Location{{}}}}</div>
    </div>
    {{"{{"}}else{{}}}}
        <div>{{"{{"}}:Subject{{}}}}{{"{{"}}:Location{{}}}}</div>
    {{"{{"}}/if{{}}}}
</script>

{% endhighlight %}

## Cells Template

The template design that applies on the Scheduler elements such as all-day cells, work cells and month cells which allows the customization to be done based on the date, view, resources and timescale. The cells can be customized to add images, colors, and other elements etc and can also access the current view of the Scheduler using the name **view**.

**All-day cells** - An API named `AllDayCellsTemplateId` can be used to customize the all-day cells, which accepts the id of the template design block preceded with a symbol **#**.

**Work cells and Month cells** - An API named `WorkCellsTemplateId` can be used to customize the work cells in all the views, which accepts the id of the template design block preceded by a symbol **#**. 

The cells can be customized with the following code example.

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
    .Width("100%")
    .Height("525px")
    .CurrentDate(new DateTime(2015, 11, 5))
    .AllDayCellsTemplateId("#alldayTemplate") // Alldaycells Template ID
    .WorkCellsTemplateId("#workTemplate") // Workcells Template ID
    .AppointmentSettings(fields => fields
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

<!-- Template for Alldaycells -->
<script id="alldayTemplate" type="text/x-jsrender">
    <div class="e-icon e-scheduleallday" style="opacity:0.5"></div>
    <span style="opacity:0.5">AllDay</span>
</script>

<!-- Template for Workcells and Monthcells -->
<script id="workTemplate" type="text/x-jsrender">
    {{"{{"}}if resource.classname == 'e-parentnode'{{}}}}
        {{"{{"}}:resource.text{{}}}}
    {{"{{"}}else{{}}}}
        {{"{{"}}if date.getDay() == 0 || date.getDay() == 6{{}}}}
            <div style="background-color:lightblue">Weekend</div>
        {{"{{"}}else{{}}}}
            {{"{{"}}if view == 'month' && resource.text == 'Party Hall-A' && date.getDay() == 5{{}}}}
                <div style="background-color:burlywood">Meeting</div>
            {{"{{"}}else resource.text != 'Party Hall-B' && date.getDate() == 15{{}}}}
                <div style="background-color:thistle">Holiday</div>
            {{"{{"}}else view != 'month' && resource.text == 'Party Hall-A' && date.getDay() == 5 && date.getHours() == 10{{}}}}
                <div style="background-color:burlywood">Meeting</div>
            {{"{{"}}else view == 'month' && resource.text == 'Party Hall-B' && date.getDay() == 5{{}}}}
                <div style="background-color:lightblue">Conf.</div>
            {{"{{"}}else resource.text == 'Party Hall-B' && date.getDate() == 16{{}}}}
                <div style="background-color:darkkhaki">Happyday</div>
            {{"{{"}}else view != 'month' && resource.text == 'Party Hall-B' && date.getDay() == 5 && date.getHours() == 12{{}}}}
                <div style="background-color:goldenrod">Conf.</div>
            {{"{{"}}else date.getDate() == 10 && date.getMonth() == 11{{}}}}
                <div style="background-color:palegreen">Day Spl</div>
            {{"{{"}}else date.getDate() == 25 && date.getMonth() == 11{{}}}}
                <div style="background-color:sandybrown">Christmas</div>
            {{"{{"}}/if{{}}}}
        {{"{{"}}/if{{}}}}
    {{"{{"}}/if{{}}}}
</script>

{% endhighlight %}

## Date Header Template

The template design that applies on for the date header part of the Scheduler. An API named `DateHeaderTemplateId`] can be used to customize the date header which accepts the id value of the template design block preceded by a symbol **#**. The template can also access the current view of the Scheduler in using the name **view**.

The Date header can be customized with the following code example.

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
    .Width("100%")
    .Height("525px")
    .CurrentDate(new DateTime(2015, 11, 5))
    .DateHeaderTemplateId("#dateTemplate") // Dateheader Template ID
    .AppointmentSettings(fields => fields
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

<!-- Template for Dateheader -->
<script id="dateTemplate" type="text/x-jsrender">
    <div>{{"{{"}}:~dTemplate(date){{}}}}</div>
</script>

<script>
    function _dateFormat(date) {
        var dFormat = ej.format(new Date(date), "dd/MM");
        return dFormat;
    }
    $.views.helpers({ dTemplate: _dateFormat });
</script>

{% endhighlight %}

## Resource Header Template

The template structure that applies on the resource headers of the Scheduler. By default, only the resource names will be displayed on the resource header bar. Also, the way of rendering resource headers on the Scheduler is comparatively different for both the vertical and horizontal scheduler views.  

The field names that are mapped from the dataSource to the appropriate field properties within the **ResourceSettings** can be accessed within the resource header template.

### Resource Header Template in Vertical View

To customize the resource header with some additional images or other customizations in **Vertical** **Scheduler** **View** – refer the below code example.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- Datasource for Grouping -->
    List<String> Group = new List<String>();
    Group.Add("Rooms");

    <!-- Datasource for Rooms -->
    List<ResourceFields> Room = new List<ResourceFields>();
    Room.Add(new ResourceFields { Id = "1", Text = "Room1", Color = "#f8a398", GroupId = "1" });
    Room.Add(new ResourceFields { Id = "2", Text = "Room2", Color = "#56ca85", GroupId = "2" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .Group(gr => { gr.Resources(Group); })
        .ResourceHeaderTemplateId("#resTemplate")
        .Resources(res => {
            res.Field("RoomId").Title("Room").Name("Rooms").AllowMultiple(true).ResourceSettings(flds => flds.Datasource(Room).Text("Text").Id("Id").Color("Color").GroupId("GroupId")).Add();
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
            .ResourceFields("RoomId"))
)

{% endhighlight %}

{% highlight html %}

<!-- Template for ResourceHeader in Vertical -->
<script id="resTemplate" type="text/x-jsrender">
    <div style="height:100%">
        <div style="width:15px;height:15px;margin-left:150px;margin-top:2px;float:left;background:{{"{{"}}:Color{{}}}};"></div><div style="float:left;margin-left:5px;">{{"{{"}}:Text{{}}}}</div>
    </div>
</script>

{% endhighlight %}

### Resource Header Template in Horizontal View

To perform the above specified same customization in **Horizontal** **Scheduler** **view**, the template structure varies a little bit as depicted below.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "", RoomId = "1" });

    <!-- Datasource for Grouping -->
    List<String> Group = new List<String>();
    Group.Add("Rooms");

    <!-- Datasource for Rooms -->
    List<ResourceFields> Room = new List<ResourceFields>();
    Room.Add(new ResourceFields { Id = "1", Text = "Room1", Color = "#f8a398", GroupId = "1" });
    Room.Add(new ResourceFields { Id = "2", Text = "Room2", Color = "#56ca85", GroupId = "2" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .Orientation(Orientation.Horizontal)
        .Group(gr => { gr.Resources(Group); })
        .ResourceHeaderTemplateId("#resTemplate")
        .Resources(res => {
            res.Field("RoomId").Title("Room").Name("Rooms").AllowMultiple(true).ResourceSettings(flds => flds.Datasource(Room).Text("Text").Id("Id").Color("Color").GroupId("GroupId")).Add();
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
            .ResourceFields("RoomId"))
)

{% endhighlight %}

{% highlight html %}

// Template for ResourceHeader in Horizontal
<script id="resTemplate" type="text/x-jsrender">
    <div style="height:100%">
        <div style="width:15px;height:15px;margin-top:2px;float:left;background:{{"{{"}}:Color{{}}}};"></div><div style="float:left;margin-left:5px;">{{"{{"}}:Text{{}}}}</div>
    </div>
</script>

{% endhighlight %}

N> In horizontal Scheduler, the header template makes use of an additional field namely **classname** which holds either **e-parentnode** or **e-childnode** value. The field **classname** can be used in the application scenario to check for the parent or child header node. You can apply the different template customization accordingly based on it.

## TimeScale with Template

The `TimeScale` is an object collection that holds below timescale related properties such as,

The `TimeScale` is also availed with template options to allow customization. It includes the following 2 properties for customization -

* `MajorSlotTemplateId` - Accepts the id value of the template design block preceded by a symbol **#**, which gets applied for the major time slots.
* `MinorSlotTemplateId` - Accepts the id value of the template design block preceded by a symbol **#**, which gets applied for the minor time slots.

The template customization for major and minor timeslots can be referred from the following code example.

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
    .Width("100%")
    .Height("525px")
    .CurrentDate(new DateTime(2015, 11, 5))
    .TimeScale(ts => ts.Enable(true).majorSlot(60).majorSlotTemplateId("#majorTemplate").minorSlotCount(6).minorSlotTemplateId("#minorTemplate"))
    .AppointmentSettings(fields => fields
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

<!-- Template for Majorslot -->
<script id="majorTemplate" type="text/x-jsrender">
    <div>{{"{{"}}:~major(date){{}}}}</div>
</script>

<!-- Template for Minorslot -->
<script id="minorTemplate" type="text/x-jsrender">
    <div>{{"{{"}}:~minor(date){{}}}}</div>
</script>

<script>
    function _majorFormat(date) {
        var dFormat = ej.format(new Date(date), "hh:mm:ss");
        return dFormat;
    }
    $.views.helpers({ major: _majorFormat });

    function _minorFormat(date) {
        var dFormat = ej.format(new Date(date), "hh:mm:ss");
        return dFormat;
    }
    $.views.helpers({ minor: _minorFormat });
</script>

{% endhighlight %}

## Priority Settings Template

The template design which can be applied to the content of the priority field in the appointment window. By default, the appropriate icons are displayed for each priority options such as **None**, **High**, **Medium** and **Low**. 

When template is applied for the `PrioritySettings`, these default icons will be replaced by the custom icons or styles defined newly. The following code example depicts the way to enable the priority settings and to define the new custom styles to replace the default icons in the Priority field.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "", Priority = "critical" });
    
    <!-- Datasource for PrioritySettings -->
    List<PrioritySettings> Priority = new List<PrioritySettings>();
    Priority.Add(new PrioritySettings { Text = "none", Value = "none" });
    Priority.Add(new PrioritySettings { Text = "critical", Value = "critical" });
    Priority.Add(new PrioritySettings { Text = "ultracritical", Value = "ultracritical" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .PrioritySettings(prty => prty.Enable(true).Datasource(Priority).Text("Text").Value("Value").Template("<div class='${Text}'></div>"))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .Description("Description")
            .AllDay("AllDay")
            .Priority("Priority")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

{% highlight html %}

<!-- Style for Priority Template -->
<style type="text/css">
    .critical,
    .ultracritical,
    .none {
        height: 13px;
        width: 13px;
        float: left;
        margin-right: 4px;
        background-repeat: no-repeat;
        background-size: 60px;
        padding: 1px;
        margin-top: 2px;
    }

    .critical {
        background-color: orange;
        background-position: -13px;
    }

    .ultracritical {
        background-color: #56ca85;
        background-position: -59px;
    }
</style>

{% endhighlight %}

The custom style class names defined for the priority template should be same as that of the values defined for each priority option within the dataSource, so that it applies properly.

N> Additionally, the priority field within the `AppointmentSettings` should be defined with appropriate dataSource field name. When an appointment is assigned with a priority value, the custom style/icon defined for that priority option will get applied over that appointment.

## Tooltip Template

The tooltip can be applied with the customized template design. Currently the tooltip support is provided only for the appointments and the default tooltip displays the Subject and duration on hovering across the appointments. 

By making use of template feature with tooltip, all the field names that are mapped from the dataSource to the appropriate field properties within the **AppointmentSettings** can be accessed.

To define the template option for tooltip, the  `TooltipSettings` must be enabled first. The following code example depicts the way to add the tooltip template.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "", Location = "US" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .ToolTipSettings(tooltip => tooltip.Enable(true).TemplateId("#tooltipTemplate"))
        .AppointmentSettings(fields => fields.Datasource(Model)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .Description("Description")
            .AllDay("AllDay")
            .Location("Location")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

{% highlight html %}

<!-- Template for Tooltip -->
<script id="tooltipTemplate" type="text/x-jsrender">
    <div style="width:145px">
        <div style="padding-top:3px;">
            <div style="float:left; font:13px Segoe UI; font-weight:bold;">Subject:&nbsp;</div>
            <div style="padding-top:2px; font:12px Segoe UI SemiBold;">{{"{{"}}:Subject{{}}}}</div>
        </div>
        <div style="padding-top:3px">
            <div style="float:left; font:13px Segoe UI; font-weight:bold;">Location:&nbsp;</div>
            <div style="padding-top:2px; font:12px Segoe UI SemiBold;">{{"{{"}}:Location{{}}}}</div>
        </div>
    </div>
</script>

{% endhighlight %}

## Agenda View Templates

Agenda View provides two separate templates – one for date column and another for time column. These templates allows the customization of the content of both the date and time columns. Apart from this, the event column can also be customized through the existing API named `AppointmentTemplateId`.

The following code snippet shows how to customize the content of the date, time and event column.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    // Datasource for Appointments
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .AgendaViewSettings(agenda => agenda.TimeColumnTemplateId("#timetemplate").DateColumnTemplateId("#datetemplate"))
        .AppointmentTemplateId("#apptemplate")
        .AppointmentSettings(fields => fields.Datasource(Model)
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

<!-- Template for date column -->
<script id="datetemplate" type="text/x-jsrender">
    <div style="height:100%">
        <div>
            <div>{{"{{"}}:~dateDisplay(StartTime){{}}}}</div>
        </div>
    </div>
</script>

<!-- Template for time column -->
<script id="timetemplate" type="text/x-jsrender">
    <div style="height:100%">
        <div>
            <div>{{"{{"}}:~timeDisplay(StartTime){{}}}}</div>
        </div>
    </div>
</script>

<!-- Template for appointment which applies for event column in agenda view. -->
<script id="apptemplate" type="text/x-jsrender">
    {{"{{"}}if View !== "agenda"{{}}}}
    <div style="height:100%; background-color:orange; margin-left: 5px;">
        <div style="margin-left: 2px;">{{"{{"}}:Subject{{}}}}</div>
        <div style="margin-left: 2px;">{{"{{"}}:Location{{}}}}</div>
    </div>
    {{"{{"}}else{{}}}}
    <div>{{"{{"}}:Subject{{}}}} {{"{{"}}:Location{{}}}}</div>
    {{"{{"}}/if{{}}}}
</script>

{% endhighlight %}

{% highlight js %}

function _getDate(date) {
        var dateCol = new Date(date);
        return dateCol.toDateString();
    }

    function _getTime(date) {
        var time = new Date(date);
        return time.toLocaleTimeString();
    }

    $.views.helpers({
        dateDisplay: _getDate,
        timeDisplay: _getTime
    });

{% endhighlight %}
