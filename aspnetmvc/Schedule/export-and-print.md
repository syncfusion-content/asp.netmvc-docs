---
title: Export, import and print the Schedule with its appointments	
description: Export-Import/Print the complete Scheduler or specific appointment alone
platform: ejmvc
control: schedule
documentation: ug
keywords: export, import and print 
---
# Export and Print

## Export Appointments

The Appointments can be exported as a whole collection or else a single appointment alone can be exported from the Scheduler. By default, the appointments are exported to .ics format which can then be imported and used in any of the other external calendars.

### Single Appointment Exporting

A single appointment can be exported by making use of its Id. You can achieve this functionality by making use of a client-side `exportSchedule` method by passing the id of an appointment to export as one of its parameter. 

It can also be achieved in another way by enabling the context menu settings and then adding a custom menu option for export appointment functionality. When right clicked on an appointment, and **export Appointment** option is chosen, the exporting functionality can be handled through the `MenuItemClick` event, within which the `exportSchedule` method should be defined with the following parameters,

* Action name (to be called in the server-side)
* Server Event (optional)
* Appointment Id (mandatory for single Appointment exporting)

The following code example shows the way to export single appointment from the Scheduler.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- List of Appointment Menu options -->
    List<Appointment> AppMenu = new List<Appointment>();
    AppMenu.Add(new Appointment { Id = "open", Text = "Open Appointment" });
    AppMenu.Add(new Appointment { Id = "delete", Text = "Delete Appointment" });
    AppMenu.Add(new Appointment { Id = "export", Text = "Export Appointment" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .ContextMenuSettings(cxt => cxt.Enable(true).MenuItems(items => items.Appointment(AppMenu)))
        .ScheduleClientSideEvents(evt => evt.MenuItemClick("onMenuItemClick"))
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
    if (args.events.ID == "export") {
        var obj = $("#Schedule1").data("ejSchedule");
        obj.exportSchedule("ExportToICS", null, args.targetInfo.Id);
    }
}

{% endhighlight %}

N> The Id value of the appointment passed in the above code example can be retrieved in the server-side action through Request.Form["AppointmentId"], as the id passed from the script is stored as hidden value in the input field of the form under this name internally.

### Exporting all Appointments

To export the entire appointments, the same `exportSchedule` method can be used without passing the id value to its parameter list. To achieve this, keep an individual button to export, and when it is clicked - the Scheduler can be allowed to export all the appointments.

The following code example depicts the way to export all the Scheduler appointments as a whole.

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
        .CurrentDate(new DateTime(2014, 6, 2))
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

@(Html.EJ().Button("export").Text("Export").ClientSideEvents(evt => evt.Click("onClick")))


{% endhighlight %}

{% highlight js %}

function onClick() {
    var obj = $("#Schedule1").data("ejSchedule");
    obj.exportSchedule("ExportToICS", null, null);
}

{% endhighlight %}

The server-side action **ExportToICS** contains the following code example to export the Scheduler appointments.

{% highlight c# %}

public void ExportToICS(FormCollection form)
{
	IEnumerable data;
	string JSONModel = Request.Form["ScheduleModel"];
	var model = JsonConvert.DeserializeObject<Dictionary<string, object>>(JSONModel);
	var Id = Request.Form["AppointmentId"];
	if(Id != null)
		// To export single appointment
		data = db.DefaultSchedules.Where(app => app.Id.ToString() == Id.ToString()).ToList();
	else
		// To export all the appointments
		data = db.DefaultSchedules.ToList();
	ScheduleExport obj = new ScheduleExport(model, data);
}

{% endhighlight %}

## Print

Two types of Print options are available – either to print the entire Scheduler layout including all the appointments in it or else to print any particular appointment alone. The public method `Print` is used to print the entire Scheduler.

### Print the Scheduler

The following code example shows the way to print the entire Scheduler, by keeping an extra button in a page – on which clicking the button will print the entire Scheduler.

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
        .CurrentDate(new DateTime(2014, 6, 2))
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

@Html.EJ().Button("print").Text("Print").ClientSideEvents(evt => evt.Click("onClick"))


{% endhighlight %}

{% highlight js %}

function onClick(args) {
    var obj = $("#Schedule1").data("ejSchedule");
    obj.print();
}

{% endhighlight %}

### Printing specific appointments

To print a particular appointment, the context menu **print** option can be used. The print option is handled internally by default, so that when an appointment is right clicked – choosing print option from the context menu that pops-out will automatically print that appointment.

N> To handle this functionality, the context menu settings needs to be enabled with print option added to the appointment items.

The following code example depicts the way to print a particular appointment.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{ 
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- List of Appointment Menu options -->
    List<Appointment> AppMenu = new List<Appointment>();
    AppMenu.Add(new Appointment { Id = "open", Text = "Open Appointment" });
    AppMenu.Add(new Appointment { Id = "delete", Text = "Delete Appointment" });
    AppMenu.Add(new Appointment { Id = "print", Text = "Print Appointment" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .ContextMenuSettings(cxt => cxt.Enable(true).MenuItems(items => items.Appointment(AppMenu)))
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

## Import Appointments

To Import appointments to the Scheduler, server-side method `renderingImportAppointments` can be used which is depicted in the following code example.

{% highlight razor %}

@Html.EJ().Button("submit").Text("Submit").ClientSideEvents(evt => evt.Click("ScheduleImport"))
@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
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

{% highlight js %}

    function ScheduleImport() {
        var dataManger = ej.DataManager({ url: '@Url.Action("ScheduleImportData", "Schedule")', crossDomain: true });
        $("#Schedule1").ejSchedule({
            appointmentSettings: {
                dataSource: dataManger
            }
        });
    }

{% endhighlight %}

The server-side code example to import the Scheduler appointments are as follows.

{% highlight c# %}

public JsonResult ScheduleImportData() {
    var destinationPath = @"Filepath\iCalender.ics";
    ScheduleImport importApps = new ScheduleImport();
    var app = importApps.renderingImportAppointments(destinationPath);
    int intMax = app.Max(a => a.Id);
    List<ScheduleAppointmentsObjData> result = new List<ScheduleAppointmentsObjData>();
    for (var i = 0; i < app.Count; i++) {
        app[i].Id = intMax + 1;
        ScheduleAppointmentsObjData row = new ScheduleAppointmentsObjData(app[i].Id, app[i].Subject, app[i].Location, app[i].StartTime, app[i].EndTime, app[i].Description, null, null, app[i].Recurrence, null, null, app[i].AppointmentCategorize, null, app[i].AllDay, null, null, app[i].RecurrenceRules, null, null);
        result.Add(row);
        intMax = app[i].Id;
    }
    return Json(result, JsonRequestBehavior.AllowGet);
}

{% endhighlight %}