---
title: Schedule - Customization	
description: Customization of working hours, date, and appointment window
platform: ejmvc
control: schedule
documentation: ug
keywords: customization, work hours, appointment window, display hours, Query cell event
---
# Customization

The Scheduler can be customized in various aspects like - 

* Setting different Start/end hour limits
* Highlighting the working hours 
* Setting different [Date format](/aspnetmvc/schedule/globalization-and-localization#date-format)
* Specifying minimum and maximum date ranges 
* Customize the entire appointment window with the user required fields
* Setting different time Slot duration

## Hour Customization

It includes customization of displaying Scheduler with specific Start/End hours and also defining the working hour time range which is differentiated as business hours.

### Schedule Display Hours

It denotes the start and end hour time limits to be displayed on the Scheduler. To set this time limit, two properties namely `StartHour` and `EndHour` can be used. 

* **StartHour** - Sets the start time. The hour from which the Scheduler time display actually starts.
* **EndHour** - Sets the end time. The hour on which the Scheduler time display should end.

The following code example renders the scheduler from 7.00 AM to 6.00 PM.

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
        .StartHour(7)
        .EndHour(18)
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

### Working Hours

Working hours indicates the work hour limit within the Scheduler. To enable the highlighting of work hours on the Scheduler, set the **Highlight** option available within the `WorkHours` property to **true**. By default, it is set to true and includes the below specified options,

* **Highlight** – enables/disables the work hour highlighting functionality.
* **Start** - sets the time to be depicted as the start of the working/business hour in a day. 
* **End** - sets the time limit to denote the end of the working/business hour in a day. 

The work hours are differentiated from other normal hours, by depicting the Scheduler cells in different color shade that belongs to this working hour time range. 

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
        .WorkHours(hrs => hrs.Highlight(true).Start(8).End(16))
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

N> By default, work hour **Start** is set to **9** and work hour **End** is set to **18**. Also, the Scheduler cells automatically scrolls up or down based on the work start hour that is set to it, to make the user to view that particular time initially.

## TimeScale

The `TimeScale` is an object collection that holds below timescale related properties such as,

* `Enable` - It accepts true or false value, denoting whether to enable/disable the timescale option. Its default value is `true`.
* `majorSlot` – To specify the majorSlot duration.
* `minorSlotCount` – To Specify the minorSlotCount.

The majorSlot and minorSlot can be customized with the following code example.

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
    .Width("100%")
    .Height("525px")
    .CurrentDate(new DateTime(2015, 11, 5))
    .TimeScale(ts => ts.Enable(true).majorSlot(60).minorSlotCount(6))
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

## Date Customization

The dates in the Scheduler can be customized by setting specific minimum and maximum date ranges and also defining various date formats to it.

### Current Date

The Current date indicates the date with which the Scheduler loads initially and based on which the appropriate date range displays in the week/workweek/month/agenda views. To set the current date to the Scheduler – use the following code example,

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

N> By default, the System current date will be taken as Scheduler’s Current date.

### MinDate and MaxDate

Providing the `MinDate` and `MaxDate` property with some date values, allows the Scheduler to set the minimum and maximum date range. The Scheduler dates that lies beyond these minimum and maximum date range will be in a disabled state, so that the date navigation is blocked beyond these specified date range. Also, the appointments that belongs beyond these date ranges will not be displayed on the Scheduler.  

The following code example show how to set the `MinDate` and `MaxDate` properties of the Scheduler.

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
        .MinDate(new DateTime(2015, 11, 4))
        .MaxDate(new DateTime(2015, 11, 8))
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

N> The **MaxDate** value provided should always be greater than that of **MinDate** value.

## Appointment Window Customization

It is possible to use the custom appointment window option to design it with the user-required extra fields apart from the other default available fields. To make use of the customized appointment window, it is necessary to use the `AppointmentWindowOpen` event within which the display of default appointment window is prevented.

The following code example lets you create the custom appointment with a single extra field for defining the appointment type.

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
        .ScheduleClientSideEvents(evt => evt.AppointmentWindowOpen("onAppointmentWindowOpen"))
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

<div id="customWindow" style="display: none">
        <form id="custom">
            <table width="100%" cellpadding="5">
                <tbody>
                    <tr style="display: none">
                        <td>Id:
                        </td>
                        <td colspan="2">
                            <input id="customId" type="text" name="Id" />
                        </td>
                    </tr>
                    <tr>
                        <td>Subject:
                        </td>
                        <td colspan="2">
                            <input id="subject" type="text" value="" name="Subject" onfocus="temp()" style="width: 100%" />
                        </td>
                    </tr>
                    <tr>
                        <td>Description:
                        </td>
                        <td colspan="2">
                            <textarea id="customdescription" name="Description" rows="3" cols="50" style="width: 100%; resize: vertical"></textarea>
                        </td>
                    </tr>
                    <tr>
                        <td>StartTime:
                        </td>
                        <td>
                            @Html.EJ().DateTimePicker("StartTime").Width("150px")
                        </td>
                    </tr>
                    <tr>
                        <td>EndTime:
                        </td>
                        <td>
                            @Html.EJ().DateTimePicker("EndTime").Width("150px")
                        </td>
                    </tr>
                    <tr>
                        <td colspan="3">
                            <div class="customcheck">AllDay:</div>
                            <div class="customcheck">
                                <input id="allday" type="checkbox" name="AllDay" onchange="alldayCheck()"/>
                            </div>
                            <div class="customcheck">Recurrence:</div>
                            <div>
                                <input id="recurrence" type="checkbox" name="Recurrence" onchange="recurCheck()" />
                            </div>
                        </td>
                    </tr>
                    <tr class="recurrence" style="display: none">
                        <td>Type:
                        </td>
                        <td>
                            <select id="rType" name="freq">
                                <option value="daily">Daily</option>
                                <option value="weekly">Weekly</option>
                                <option value="monthly">Monthly</option>
                                <option value="yearly">Yearly</option>
                            </select>
                        </td>
                    </tr>
                </tbody>
            </table>
        </form>
        <div>
			<button type="submit" onclick="cancel()" id="btncancel" style="float:right;margin-right:20px;margin-bottom:10px;">Cancel</button>
	        <button type="submit" onclick="save()" id="btnsubmit"style="float:right;margin-right:20px;margin-bottom:10px;">Submit</button>
        </div>
    </div>

{% endhighlight %}

The styles to be applied for the controls within the custom appointment window are as follows.

{% highlight html %}

<style>
    .customcheck {
    float: left;
    margin-right: 10px;
    }
	
    .error {
    background-color: #FF8A8A;
    }
	
    #custom table td {
    padding:5px;
    }
</style>

{% endhighlight %}

Now, define the Schedule control with custom window within script as shown below.

{% highlight html %}

<script>
$(function() {
    // defining sub-controls used within custom appointment window
    $("#btncancel").ejButton({
        width: '85px'
    });
	
    $("#btnsubmit").ejButton({
        width: '85px'
    });
	
    $("#StartTime").ejDateTimePicker({
        width: "150px"
    });
	
    $("#EndTime").ejDateTimePicker({
        width: "150px"
    });
	
    // DataSource values for the appointment type field
    var types = [{
        text: "Tentative",
        id: 1
    }, {
        text: "Busy",
        id: 3
    }, {
        text: "Free",
        id: 5
    }, {
        text: "Out Of Office",
        id: 7
    }];
	
    // defining dropdown controls to be used within custom appointment window
    $("#AppointmentType").ejDropDownList({
        dataSource: types,
        fields: {
            text: "text",
            id: "id",
            value: "text"
        }
    });
	
    // defining dialog control to be used as custom appointment window
    $("#customWindow").ejDialog({
        width: 600,
        height: "auto",
        position: {
            X: 200,
            Y: 100
        },
        showOnInit: false,
        enableModal: true,
        title: "Create Appointment",
        enableResize: false,
        allowKeyboardNavigation: false,
        close: "clearFields"
    });
});
</script>

{% endhighlight %}

The following function needs to be defined within script section, which gets called before the default appointment window opens.

{% highlight js %}

function onAppointmentWindowOpen(args) {
    args.cancel = true; // prevents the display of default appointment window
    // When double clicked on the Scheduler cells, fills the StartTime and EndTime fields appropriately
    $("#StartTime").ejDateTimePicker({
        value: args.startTime
    });
    $("#EndTime").ejDateTimePicker({
        value: args.endTime
    });
    if (!ej.isNullOrUndefined(args.target)) {
        // When double clicked on the Scheduler cells, if the target is allday or month cells – only then enable check mark on the allday checkbox
        if ($(args.target.currentTarget).hasClass("e-alldaycells"))
            $("#allday").prop("checked", true);
        else
            args.model.currentView == "month" ? $("#allday").prop("checked", true) : $("#allday").prop("checked", false);
        // If the target is allday or month cells – disable the StartTime and EndTime fields
        $("#StartTime,#EndTime").ejDateTimePicker({
            enabled: ($(args.target.currentTarget).hasClass("e-alldaycells") || $(args.target.currentTarget).hasClass("e-monthcells") || args.model.currentView == "month") ? false : true
        });
    }

    // If double clicked on the appointments, fill the custom appointment window fields with appropriate values.
    if (!ej.isNullOrUndefined(args.appointment)) {
        $("#customId").val(args.appointment.Id);
        $("#subject").val(args.appointment.Subject);
        $("#customdescription").val(args.appointment.Description);
        $("#StartTime").ejDateTimePicker({
            value: new Date(args.appointment.StartTime)
        });
        $("#EndTime").ejDateTimePicker({
            value: new Date(args.appointment.EndTime)
        });
        // Fills the Appointment type dropdown with its value
        var value = args.appointment.AppointmentType;
        $("#AppointmentType").ejDropDownList("clearText");
        $("#AppointmentType").ejDropDownList({
            text: value,
            value: value
        });
        $("#allday").prop("checked", args.appointment.AllDay);
        $("#recurrence").prop("checked", args.appointment.Recurrence);
        if (args.appointment.Recurrence) {
            $("#rType").val(args.appointment.RecurrenceRule.split(";")[0].split("=")[1].toLowerCase());
            $("tr.recurrence").css("display", "table-row");
        }
        $("#customWindow").ejDialog("open");
    } else
        $("#customWindow").ejDialog("open");
}

{% endhighlight %}

On clicking the **Submit** button within the Custom Appointment window, the following function gets executed – which will validate the appointment fields and then save it appropriately.

{% highlight js %}

function save() {
    // checks if the subject value is not left blank before saving it.
    if ($.trim($("#subject").val()) == "") {
        $("#subject").addClass("error");
        return false;
    }
    var obj = {},
        temp = {},
        rType;
    var formelement = $("#customWindow").find("#custom").get(0);
    // looping through the custom form elements to get each value and form a JSON object
    for (var index = 0; index < formelement.length; index++) {
        var columnName = formelement[index].name,
            $element = $(formelement[index]);
        if (columnName != undefined) {
            if (columnName == "")
                columnName = formelement[index].id.replace(this._id, "");
            if (columnName != "" && obj[columnName] == null) {
                var value = formelement[index].value;
                if (columnName == "Id" && value != "")
                    value = parseInt(value);
                if ($element.hasClass("e-datetimepicker"))
                    value = new Date(value);
                if (formelement[index].type == "checkbox")
                    value = formelement[index].checked;
                if (columnName == "freq") {
                    if (formelement[index].type == "select-one") {
                        rType = document.getElementById("rType");
                        temp[columnName] = rType.options[rType.selectedIndex].value;
                    }
                }
                obj[columnName] = value;
            }
        }
    }
    if (obj.Recurrence) {
        if (temp.freq.toUpperCase() == "DAILY")
            obj["RecurrenceRule"] = "FREQ=DAILY;INTERVAL=1;COUNT=5";
        else if (temp.freq.toUpperCase() == "WEEKLY")
            obj["RecurrenceRule"] = "FREQ=WEEKLY;BYDAY=MO,WE,TH;INTERVAL=1;COUNT=10";
        else if (temp.freq.toUpperCase() == "MONTHLY")
            obj["RecurrenceRule"] = "FREQ=MONTHLY;BYMONTHDAY=" + obj.StartTime.getDate() + ";INTERVAL=1;COUNT=5";
        else if (temp.freq.toUpperCase() == "YEARLY")
            obj["RecurrenceRule"] = "FREQ=YEARLY;BYMONTHDAY=" + obj.StartTime.getDate() + ";BYMONTH=" + (obj.StartTime.getMonth() + 1) + ";INTERVAL=1;COUNT=3";
    } else
        obj["RecurrenceRule"] = null;
    var appTypeObj = $("#AppointmentType").data("ejDropDownList");
    obj["AppointmentType"] = appTypeObj.getSelectedValue();
    $("#customWindow").ejDialog("close");
    var object = $("#Schedule1").data("ejSchedule");
    object.saveAppointment(obj);
    clearFields();
}

// Clears all the field values of the custom window after saving appointments
function clearFields() {
    $("#customId").val("");
    $("#subject").val("");
    $("#customdescription").val("");
    $("#AppointmentType").val("");
    $("#allday").prop("checked", false);
    $("#recurrence").prop("checked", false);
    document.getElementById("rType").selectedIndex = "0";
    $("tr.recurrence").css("display", "none");
    $("#StartTime,#EndTime").ejDateTimePicker({
        enabled: true
    });
}

// This function executes when the recurrence checkbox is checked in the custom appointment window
function recurCheck() {
    // Displays the recurrence field, when recurrence checkbox is checked.
    if ($("#recurrence").get(0).checked == true)
        $("tr.recurrence").css("display", "table-row");
    else
        $("tr.recurrence").css("display", "none");
}

// This function executes when the All-day checkbox is checked in the custom appointment window
function alldayCheck() {
    // Disables and sets the specific hours to the StartTime and EndTime fields, when the all-day checkbox is checked
    if ($("#allday").prop("checked")) {
        var a = $("#StartTime").data("ejDateTimePicker").model.value;
        a.setHours(0, 0, 0);
        var b = $("#EndTime").data("ejDateTimePicker").model.value;
        b.setHours(23, 59, 0);
        $("#StartTime").ejDateTimePicker({
            value: new Date(a),
            enabled: false
        });
        $("#EndTime").ejDateTimePicker({
            value: new Date(b),
            enabled: false
        });
    } else {
        $("#StartTime").ejDateTimePicker({
            enabled: true
        });
        $("#EndTime").ejDateTimePicker({
            enabled: true
        });
    }
}

// This function executes when the subject text field is currently being focussed
function temp() {
    $("#subject").removeClass("error");
}

// This function executes when the cancel button in the custom appointment window is pressed.
function cancel() {
    clearFields();
    $("#customWindow").ejDialog("close");
}

{% endhighlight %}

## Query cell info

It is possible to customize the scheduler DOM element in that scheduler using `QueryCellEvent` event. There are several main things that we can customize through query cell info event.

* Work cell
* Month cell
* All day cell
* Appointment
* Time cells
* Date header cells
* Resource header cell
* Agenda time cell
* Agenda resource cell
* Agenda date cell
* Agenda event cell

The following code snippet shows how to customize the appointment and work cells based on the query cell info event.
     
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
        .ScheduleClientSideEvents(evt => evt.QueryCellInfo("checkFormat"))
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

While loading the above scheduler the below function called by `QueryCellInfo` event and format the DOM element based on given scenario


{% highlight html %}

    <script type="text/javascript">
     function checkFormat(args) {
	    switch (args.requestType) {
		case "workcells":
			args.element.css("background-color", "#ffe9cc");
			break;
		case "monthcells":
			args.element.css("background-color", "#faa41a");
			args.element.css("border-color", "#faa41a");
			break;
		}
    }
    </script>

{% endhighlight %}