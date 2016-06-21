---
title: How-to
description: Custom Configuration with Schedule control
platform: ejmvc
control: schedule
documentation: ug
keywords: globalize, localize, localization, globalization 
---
# How To

## Validate the Custom Appointment Window Fields

The client-side validation of the fields present within the custom appointment window can be handled before submitting it, by adding appropriate validation classes to each field.

Refer the steps [here](/aspnetmvc/schedule/customization#appointment-window-customization) and create a sample for Custom Appointment window, before proceeding with the following validations.

In the custom appointment window sample, create an additional CSS class **validation** as mentioned below to add it to the appropriate fields, if the validation of such fields fails.

{% highlight css %}

<style> 
    .validation {
        border-color: red;
    }
</style>

{% endhighlight %}

The sample contains the fields like Subject, Description, StartTime and EndTime which needs to be validated at client-side. To do so, add the required validation code within the script section as follows.

{% highlight html %}

<script type="text/javascript">

// To Validate the Subject field.
$("#subject").focusout(function() {
    if ($.trim($("#subject").val()) == "") {
        $("#subject").addClass("validation");
        return false;
    }
})

// To Validate the Description field.
$("#customdescription").focusout(function() {
    if ($.trim($("#customdescription").val()) == "") {
        $("#customdescription").addClass("validation");
        return false;
    }
})

// To Validate the Time duration of the appointments
$("#EndTime").focusout(function() {
    if (new Date($("#EndTime").val()).getDate() >= new Date($("#StartTime").val()).getDate()) {
        if (new Date($("#StartTime").val()).getTime() >= new Date($("#EndTime").val()).getTime())
            alert("EndTime value is lesser than the StartTime value");
    }
})

</script>

{% endhighlight %}

Now, after adding the above validations – whenever the fields within the custom appointment window are skipped without filling any information, it will be notified to the users appropriately.

## Highlight Different Work Hours for Each Resources

By default, the work hours of the Scheduler is highlighted based on the start and end values provided within the `WorkHours` property. It remains same for all the resources, when the Scheduler is rendered with multiple resources. To customize this behavior so as to highlight different working hour range for each of the resources, the following workaround can be utilized by making use of the Scheduler events `Create` and `ActionComplete`.

Initially, set the `Highlight` as false for the `WorkHours`, so as to disable the highlighting of default work hour range.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "", OwnerId = "1" });

    <!-- Datasource for Grouping -->
    List<String> Group = new List<String>();
    Group.Add("Owners");

    <!-- Datasource for Owners -->
    List<ResourceFields> Owner = new List<ResourceFields>();
    Owner.Add(new ResourceFields { Id = "1", Text = "Nancy", Color = "#f8a398" });
    Owner.Add(new ResourceFields { Id = "3", Text = "Steven", Color = "#56ca85" });
    Owner.Add(new ResourceFields { Id = "5", Text = "Michael", Color = "#51a0ed" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .ShowCurrentTimeIndicator(false)
        .WorkHours(hrs => hrs.Highlight(false))
        .Group(gr => gr.Resources(Group))
        .Resources(res => { res.Field("OwnerId").Title("Owner").Name("Owners").ResourceSettings(flds => flds.Datasource(Owner).Text("Text").Id("Id").Color("Color")).Add(); })
        .ScheduleClientSideEvents(evt => evt.Create("onCreate").ActionComplete("onCreate"))
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

{% highlight js %}

// This function executes during the initial control creation and also on completion of each action like date/view navigation.
function onCreate(args) {
    if (args.requestType == "viewNavigate" || args.requestType == "dateNavigate" || args.type == "create") {
        // declare different start and end work hour values for each resources
        var resourceOneStart = 9,
            resourceOneEnd = 18;

        var resourceTwoStart = 13,
            resourceTwoEnd = 18;

        var resourceThreeStart = 10,
            resourceThreeEnd = 18;

        this.option("workHours.highlight", (this.currentView() != "month") ? false : true);
        var trElements = this.$WorkCellDiv.find("tr");    // Get the Scheduler workcell rows

        for (var i = 0; i < trElements.length; i++) {
            var tdElements = $(trElements[i]).find("td");  // Get the Scheduler workcell columns
            for (var j = 0; j < tdElements.length; j++) {
                switch (this.currentView()) {
                    case "day":
                        switch (j) {
                            case 0: // column index 0 represents first resource in day view
                                $(tdElements[j]).addClass(((i > (resourceOneStart * 2) - 1) && (i <= (resourceOneEnd * 2) - 1)) ? "e-businesshighlightworkcells" : "");
                                break;
                            case 1: // column index 1 represents second resource in day view
                                $(tdElements[j]).addClass(((i > (resourceTwoStart * 2) - 1) && (i <= (resourceTwoEnd * 2) - 1)) ? "e-businesshighlightworkcells" : "");
                                break;
                            case 2: // column index 2 represents third resource in day view
                                $(tdElements[j]).addClass(((i > (resourceThreeStart * 2) - 1) && (i <= (resourceThreeEnd * 2) - 1)) ? "e-businesshighlightworkcells" : "");
                                break;
                        }
                        break;
                    case "week":
                        switch (j) {
                            case 0:
                            case 1:
                            case 2:
                            case 3:
                            case 4:
                            case 5:
                            case 6: // column indexes 0 to 6 belongs to first resource in week view (7 days)
                                $(tdElements[j]).addClass(((i > (resourceOneStart * 2) - 1) && (i <= (resourceOneEnd * 2) - 1)) ? "e-businesshighlightworkcells" : "");
                                break;
                            case 7:
                            case 8:
                            case 9:
                            case 10:
                            case 11:
                            case 12:
                            case 13: // column indexes 7 to 13 belongs to second resource in week view (7 days)
                                $(tdElements[j]).addClass(((i > (resourceTwoStart * 2) - 1) && (i <= (resourceTwoEnd * 2) - 1)) ? "e-businesshighlightworkcells" : "");
                                break;
                            case 14:
                            case 15:
                            case 16:
                            case 17:
                            case 18:
                            case 19:
                            case 20: // column indexes 14 to 20 belongs to third resource in week view (7 days)
                                $(tdElements[j]).addClass(((i > (resourceThreeStart * 2) - 1) && (i <= (resourceThreeEnd * 2) - 1)) ? "e-businesshighlightworkcells" : "");
                                break;
                        }
                        break;
                    case "workweek":
                        switch (j) {
                            case 0:
                            case 1:
                            case 2:
                            case 3:
                            case 4: // column indexes 0 to 4 belongs to first resource in workweek view (5 days)
                                $(tdElements[j]).addClass(((i > (resourceOneStart * 2) - 1) && (i <= (resourceOneEnd * 2) - 1)) ? "e-businesshighlightworkcells" : "");
                                break;
                            case 5:
                            case 6:
                            case 7:
                            case 8:
                            case 9:
                                // column indexes 5 to 9 belongs to second resource in workweek view (5 days)
                                $(tdElements[j]).addClass(((i > (resourceTwoStart * 2) - 1) && (i <= (resourceTwoEnd * 2) - 1)) ? "e-businesshighlightworkcells" : "");
                                break;
                            case 10:
                            case 11:
                            case 12:
                            case 13:
                            case 14:
                                // column indexes 10 to 14 belongs to third resource in workweek view (5 days)
                                $(tdElements[j]).addClass(((i > (resourceThreeStart * 2) - 1) && (i <= (resourceThreeEnd * 2) - 1)) ? "e-businesshighlightworkcells" : "");
                                break;
                        }
                        break;
                }
            }
        }
    }
}

{% endhighlight %}

## Display Scheduler with Appointments Filtered by Subject

It is possible to display the Scheduler with the appointments, which is filtered based on the Subject. For example, if we keep a text box and start typing a character – the appointment’s subject that matches the typed character alone will be shown on the Scheduler. The following code example depicts the way to achieve this.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
    Appoint.Add(new ScheduleFields { Id = "2", Subject = "Bering Sea Gold", StartTime = new DateTime(2015, 11, 10, 01, 00, 00), EndTime = new DateTime(2015, 11, 10, 02, 30, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
    Appoint.Add(new ScheduleFields { Id = "3", Subject = "Deadest Catch", StartTime = new DateTime(2015, 11, 10, 11, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 30, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
    Appoint.Add(new ScheduleFields { Id = "4", Subject = "What Happened Next?", StartTime = new DateTime(2015, 11, 10, 15, 00, 00), EndTime = new DateTime(2015, 11, 10, 17, 30, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
    Appoint.Add(new ScheduleFields { Id = "5", Subject = "Daily Planet", StartTime = new DateTime(2015, 11, 10, 20, 00, 00), EndTime = new DateTime(2015, 11, 10, 22, 30, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .ShowCurrentTimeIndicator(false)
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

<!-- Textbox for entering search character -->
<input id='txtSearch' type='text' onkeyup='searchKeyUp()' />

<script>
    function searchKeyUp() {
        var searchString = $("#txtSearch").val();
        var schObj = $("#Schedule1").data("ejSchedule");
        var result = schObj.searchAppointments(searchString);
        schObj.option("appointmentSettings", { dataSource: [] });
        if (!ej.isNullOrUndefined(result) && result.length != 0 && searchString != "")
            schObj.option("appointmentSettings", { dataSource: result });
        else
            schObj.option("appointmentSettings", { dataSource: schObj._currentAppointmentData });
    }
</script>

{% endhighlight %}

## Customize the Default Appointment Window

Apart from the custom appointment window, it is possible to customize the default appointment window by adding/removing the required number of fields into it. This can be achieved through the `Create` event of the scheduler.

The following code example depicts the way to achieve the customization of default appointment window.

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
        .ShowCurrentTimeIndicator(false)
        .ScheduleClientSideEvents(evt => evt.Create("onCreate").AppointmentWindowOpen("onAppointmentOpen"))
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

    // This function executes when the checkboxes are checked/unchecked
    function onCreate(args) {
        var customDesign = "<tr class='customfields'><td class='e-textlabel'>Event Type</td><td><input class='apptype' type='text'/></td><td class='e-textlabel'>Event Status </td><td><input class='status' type='text'/></td></tr>";
        $("." + this._id + "parrow").after(customDesign);
    }

    // This function executes before the appointment window gets opened.
    function onAppointmentOpen(args) {
        if (!ej.isNullOrUndefined(args.appointment)) {
            // if double clicked on the appointments, retrieve the custom field values from the appointment object and fills it in the appropriate fields.               this._appointmentAddWindow.find(".apptype").val(args.appointment.AppointmentType);
            this._appointmentAddWindow.find(".status").val(args.appointment.Status);
        } else {
            // if double clicked on the cells, clears the field values.               
            this._appointmentAddWindow.find(".apptype").val("");
            this._appointmentAddWindow.find(".status").val("");
        }
    }

{% endhighlight %}


## SignalR Implementation

To implement SignalR concept in Scheduler, add and refer the appropriate SignalR scripts in your project and then create a hub for initiating the action. The SignalR implementation can be achieved with the following code example.

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
        .ScheduleClientSideEvents(d => { d.BeforeAppointmentCreate("actionComplete"); d.Navigation("actionComplete"); d.BeforeAppointmentRemove("actionComplete"); d.BeforeAppointmentChange("actionComplete"); })
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

<script src="~/Scripts/jquery.signalR-1.1.4.min.js"></script>
<script src="@Url.Content("~/signalr/hubs")"></script>

<script type="text/javascript">
    $(function () {
        window.signal = $.connection.scheduleHub;
        window.signal.client.modify = function (action, data) {
            if (data != null) {
                var id = data.Id != null ? data.Id : data[0].Id;
                var subject = data.Subject;
                var startTime = new Date(data.StartTime);
                var endTime = new Date(data.EndTime);
                var description = data.Description;
                var allDay = data.AllDay;
                var recurrence = data.Recurrence;
                var recurrenceRule = data.RecurrenceRule;
                var object = { Id: id, Subject: subject, StartTime: startTime, EndTime: endTime, Description: description, AllDay: allDay, Recurrence: recurrence, RecurrenceRule: recurrenceRule };
                var schedule = $("#Schedule1").data("ejSchedule");
                if (action == "appointmentSaved") {
                    new ej.DataManager(schedule._currentAppointmentData).insert(object);
                    schedule._appointmentProcessing(object);
                    schedule._renderAppointmentAll();
                }
                else if (action == "appointmentEdited") {
                    new ej.DataManager(schedule._currentAppointmentData).update("Id", object);
                    new ej.DataManager(schedule._processed).remove("Id", object.Id);
                    schedule._appointmentProcessing(object);
                    schedule._renderAppointmentAll();
                }
                else if (action == "appointmentDeleted") {
                    var appointment = new ej.DataManager(schedule._processed).executeLocal(new ej.Query().where("Id", ej.FilterOperators.equal, id));
                    new ej.DataManager(schedule._currentAppointmentData).remove("Id", appointment[0].Id);
                    new ej.DataManager(schedule._processed).remove("Id", appointment[0].Id);
                    schedule._renderAppointmentAll();
                }
            }

        };
        $.connection.hub.start().done(function () {
            window.actionComplete = function (args) {
                if(args.methodType=="public")
                    args.appointment=null;
                var appointmentDetails = args.appointment;
                if (args.type == "appointmentSaved" || args.type == "appointmentEdited" || args.type == "appointmentDeleted") {
                    window.signal.server.modify(args.type, appointmentDetails);
                }
            };
        });
    });

</script>

{% endhighlight %}


Create a Hub file and add the following action for accessing the client details.

{% highlight c# %}

public void Modify(string action, Object data)
{
    Clients.Others.modify(action, data);
}

{% endhighlight %}

## Synchronize the Schedule with Outlook

Schedule appointments can be synchronized with Outlook and vice versa, by making use of the Microsoft Outlook 12/15 Object library. 

The following code example depicts the way to synchronize the Schedule with Outlook.

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 12))
               .AppointmentSettings(fields => fields.Datasource(ds => ds.URL("/Home/GetApp").CrudURL("/Home/Batch").Adaptor("UrlAdaptor"))
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

Schedule control is not directly compatible with the Outlook calendar object, as it returns the COM object. Therefore, in order to bind the schedule control with those data retrieved from outlook, then it is necessary to convert the COM object into the schedule acceptable object format. To do so, add the following code example in your code behind. 

{% highlight c# %}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.Mvc;
using System.ComponentModel;
using System.Configuration;
using System.Data;
using System.Data.SqlClient;
using System.Collections;
using Microsoft.Office.Interop.Outlook; // required Microsoft DLL
using System.Web.Script.Serialization;
using System.Web.UI;
using System.Web.UI.WebControls;
using ScheduleCRUD.Models;

namespace ScheduleCRUD.Controllers
{
    public class HomeController : Controller
    {

        DataClasses1DataContext db = new DataClasses1DataContext();
        public ActionResult Index()
        {

            return View();
        }

        public JsonResult GetApp() // function to display the outlook appointments in Schedule initially
        {
            IEnumerable data = GetData();
            return Json(data, JsonRequestBehavior.AllowGet);

        }
        public List<ScheduleData> GetData() // function to return the outlook appointments
        {
            Microsoft.Office.Interop.Outlook.Application oApp = new Microsoft.Office.Interop.Outlook.Application();
            Microsoft.Office.Interop.Outlook.NameSpace mapiNamespace = oApp.GetNamespace("MAPI");
            Microsoft.Office.Interop.Outlook.MAPIFolder CalendarFolder = mapiNamespace.GetDefaultFolder(Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderCalendar);
            Microsoft.Office.Interop.Outlook.Items outlookCalendarItems = CalendarFolder.Items;
            List<Microsoft.Office.Interop.Outlook.AppointmentItem> lst = new List<Microsoft.Office.Interop.Outlook.AppointmentItem>();

            foreach (Microsoft.Office.Interop.Outlook.AppointmentItem item in outlookCalendarItems)
            {
                lst.Add(item);
            }

            List<ScheduleData> newApp = new List<ScheduleData>();
            // converting COM object into IEnumerable object
            for (var i = 0; i < lst.Count; i++)
            {
                ScheduleData app = new ScheduleData();
                app.Id = i;
                app.Subject = lst[i].Subject;
                app.AllDay = lst[i].AllDayEvent;
                app.StartTime = Convert.ToDateTime(lst[i].Start.ToString());
                string endTime = lst[i].End.ToString();
                DateTime appEndDate = Convert.ToDateTime(endTime);
                if (endTime.Contains("12:00:00 AM") && app.AllDay == true)
                    app.EndTime = appEndDate.AddMinutes(-1);
                else
                    app.EndTime = appEndDate;
                app.Recurrence = false;
                app.RecurrenceRule = null;
                newApp.Add(app);
            }
            return newApp;
        }

        public JsonResult Batch(EditParams param)
        {
            if (param.action == "insert" || (param.action == "batch" && param.added != null)) // this block of code will execute while inserting the appointments
            {
                var value = param.action == "insert" ? param.value : param.added[0];
                int intMax = db.ScheduleDatas.ToList().Count > 0 ? db.ScheduleDatas.ToList().Max(p => p.Id) : 1;
                DateTime startTime = Convert.ToDateTime(value.StartTime);
                DateTime endTime = Convert.ToDateTime(value.EndTime);
                ScheduleData appoint = new ScheduleData()
                {
                    Id = value.Id,
                    StartTime = startTime,
                    EndTime = endTime,
                    StartTimeZone=value.StartTimeZone,
                    EndTimeZone=value.EndTimeZone,
                    Subject = value.Subject,                   
                    Description = value.Description,                    
                    Recurrence = value.Recurrence,
                    CategoryId = value.CategoryId,
                    AllDay = value.AllDay,                   
                    RecurrenceRule = value.RecurrenceRule,                   
                };
                db.ScheduleDatas.InsertOnSubmit(appoint);
                db.SubmitChanges();
                Microsoft.Office.Interop.Outlook.Application outlookApp = new Microsoft.Office.Interop.Outlook.Application();
                Microsoft.Office.Interop.Outlook.AppointmentItem newAppointment = null;
                newAppointment = (Microsoft.Office.Interop.Outlook.AppointmentItem)outlookApp.CreateItem(Microsoft.Office.Interop.Outlook.OlItemType.olAppointmentItem);
                newAppointment.Start = Convert.ToDateTime(value.StartTime).ToUniversalTime();
                newAppointment.End = Convert.ToDateTime(value.EndTime).ToUniversalTime();
                newAppointment.Subject = value.Subject.ToString();
                newAppointment.Save();
            }
            IEnumerable data = new DataClasses1DataContext().ScheduleDatas.Take(500); // nw.Appointment.Take(5);
            return Json(data, JsonRequestBehavior.AllowGet);
        }
    }
}

{% endhighlight %}

N> In order to achieve the above scenario, need to refer the Microsoft DLL (Microsoft Outlook 12/15 Object library [Microsoft.Office.Interop.Outlook]) in your application and refer it in the controller page as shown above.