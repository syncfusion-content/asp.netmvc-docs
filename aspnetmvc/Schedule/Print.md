---
layout: post
title: Print
description: print
platform: ejmvc
control: Schedule
documentation: ug
---

## Print

Schedule control is provided with the Print feature. You can print the entire Schedule control or separately print the appointment based on your requirement.

Schedule Print

You can print the Schedule control by using print() method. Use the following code example to print the Schedule control.



<table>
<tr>
<td>
[Razor]&lt;div&gt;&lt;input class="print" type="button" value="Print" /&gt;@(Html.EJ().Schedule("Schedule1")// Add the necessary schedule properties here)&lt;script type="text/javascript"&gt;$(document).ready(function () {// function to bind the click event to the button$('.print').bind("click", function () {var obj = $("#Schedule1").data("ejSchedule");// Public method to print the scheduleobj.print();});});&lt;/script&gt;</td></tr>
<tr>
<td>
[Controller]           // follow the code as same as declared in Read Only part</td></tr>
</table>


Execute the above code to render the following output.

{ ![](Print_images/Print_img1.png) | markdownify }
{:.image }


_Figure_ _121__: Schedule with print button_

Click the print button to render the following output.



{ ![](Print_images/Print_img2.png) | markdownify }
{:.image }


_Figure_ _122__: Schedule with Print window_

Appointment Print

* In Schedule control, you can print the appointment alone by using context menu. Add print as menu item in the context menu settings as in the following code example.



<table>
<tr>
<td>
[Razor]@(Html.EJ().Schedule("Schedule1")// To Add the Context menu settings.ContextMenuSettings(cms =>cms.Enable(true)// To Add menu items.MenuItems(item=>item.Appointment(ViewBag.app)))// Add the Appointment setting collection here)</td></tr>
<tr>
<td>
[Controller]public ActionResult Print(){// create list for menu item collectionList<Appointment> appointment = new List<Appointment>();appointment.Add(new Appointment() { Id = "open", Text = "Open Appointment" });appointment.Add(new Appointment() { Id = "delete", Text = "Delete Appointment" });// To Add print item in that collection.appointment.Add(new Appointment() { Id = "print", Text = "Print Appointment" });var DataSource = new ScheduleDataDataContext().DefaultSchedules.ToList();ViewBag.dataSource = DataSource;ViewBag.app = appointment;return View();}</td></tr>
</table>
* Right click on the appointment and select print appointment in the context menu as follows.



{ ![](Print_images/Print_img3.png) | markdownify }
{:.image }


_Figure_ _123__: Schedule with Print option in Context Menu_

* Now, the widow is promoted to new document with appointment details and print window opens.



{ ![](Print_images/Print_img4.png) | markdownify }
{:.image }


_Figure_ _124__: Schedule with Appointment Print_

