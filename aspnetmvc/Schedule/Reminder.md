---
layout: post
title: Reminder
description: reminder
platform: ejmvc
control: Schedule
documentation: ug
---

## Reminder

* Reminder option provides the list of reminder appointments and you can use those appointments for your own customized scenarios like displaying it as an end-user notification. To enable the reminder settings for the Schedule control, you can set the enable property as ‘true’ within the reminderSettings option. 
* The reminderSettings option includes another optional property alertBefore that accepts integer value to denote the time before how long the reminder is notified to the user.
* For such case, you can also use an in-built event reminder that triggers when there is a reminder appointment. It provides the details of the list of reminder appointment details.

The following code example explains how to get the reminder list and display it as a notification for users.



[Razor]



&lt;!-- Reminder list div elements--&gt;

&lt;div id="reminder" class="media" data-content=" "&gt;

&lt;a class="pull-left" href="#" style="margin-top: 9px; outline: medium none;"&gt;

&lt;div class="reminder-icon"&gt;

&lt;/div&gt;

<span id="reminderCount" class="badge badge-success pull-right">0</span> &lt;/a&gt;

&lt;/div&gt;

&lt;!-- Notification div element--&gt;

&lt;div class='notifications bottom-right'&gt;

&lt;/div&gt;

&lt;div&gt;

@(Html.EJ().Schedule("Schedule1")

.Width("100%")

.Height("525px")

.ReminderSettings(rem => rem.Enable(true).AlertBefore(6))

.ScheduleClientSideEvents(eve => eve.Reminder("ongetReminderList").Create("onCreate"))

.AppointmentSettings(fields => fields.Datasource((IEnumerable)ViewBag.datasource)

.Id("Id")

.Subject("Subject")

.StartTime("StartTime")

.EndTime("EndTime")

.AllDay("AllDay")

.Recurrence("Recurrence")

.RecurrenceRule("RecurrenceRule"))

)



&lt;/div&gt;

&lt;style&gt;

#reminderCount

{

position: relative;

min-width: 6px;

top: -36px;

left: 10px;

background-color: #FF0000;

}

#reminder

{

width: 50px;

height: 40px;

margin-top: 1px;

float: right;

}

.reminder-icon

{

background: url("../images/schedule/bell.png") no-repeat scroll 8px 6px rgba(0, 0, 0, 0);

border: 1px solid #BBBCBB;

height: 28px;

width: 28px;

border-radius: 6px;

}

.popover.bottom .arrow

{

margin-top: 0px;

}

.popover

{

width: 300px;

}

.outerDiv

{

border-bottom: 1px solid #BBBCBB;

padding-bottom: 5px;

}

.notifications.top-right

{

top: 25% !important;

}

&lt;/style&gt;

&lt;script type="text/javascript"&gt;

function onCreate() {

//Append the reminder list to the Schedule header

$("#Schedule1").find("tr.e-scheduleheader td").first().append($("#reminder"));

// Reminder list load to the popover control

$("#reminder").popover({ placement: 'bottom' });

//popover content has been updated

$('#reminder').on('shown.bs.popover', function () {

if (parseInt($("#reminderCount").text()) == 0)

return false;

$(".popover-content").html($_remList);

$(".outerDiv .close").on("click", function () {

$(this).parents(".outerDiv").remove();

$_remList = $(".popover-content").html();

$("#reminderCount").html(parseInt($("#reminderCount").text()) - 1);

checkList();

});

$(".outerDiv").on("mouseover", function () {

$(this).find(".close").show();

});

$(".outerDiv").on("mouseout", function () {

$(this).find(".close").hide();

});

});

}

function checkList() {

if (parseInt($("#reminderCount").text()) == 0)

$("#reminderCount").hide();

else

$("#reminderCount").show();

}

var $_remList = "";

function ongetReminderList(args) {

//alert(args.reminderAppointment.Subject);

$("#reminderCount").html(parseInt($("#reminderCount").text()) + 1);

checkList();

$_remList += "&lt;div class='outerDiv'&gt;&lt;span class='e-quicksubject'&gt;" + args.reminderAppointment.Subject +

"&lt;/span&gt;&lt;div class='e-quickstartendtime'&gt;" + args.reminderAppointment.StartTime +

"&lt;/div&gt;&lt;a class='close pull-right' href='#' style='margin-top: -56px;display: none;'&gt;×&lt;/a&gt;&lt;/div&gt;";

var notifiList = "&lt;div&gt;&lt;span class='e-quicksubject'&gt;" + args.reminderAppointment.Subject +

"&lt;/span&gt;&lt;div class='e-quickstartendtime'&gt;" + args.reminderAppointment.StartTime +

"&lt;/div&gt;&lt;/div&gt;";

// Show the notification div

$('.bottom-right').notify({

message: { html: notifiList },

type: "info",

fadeOut: {

enabled: false

}

}).show();

}

&lt;/script&gt;



Execute the above code to render the following output.



{ ![](Reminder_images/Reminder_img1.png) | markdownify }
{:.image }


   _Figure_ _106__:  schedule with Reminder._

