---
layout: post
title: Print | Schedule | ASP.NET MVC | Syncfusion
description: print
platform: ejmvc
control: Schedule
documentation: ug
---

# Print

Schedule control is provided with the Print feature. You can print the entire Schedule control or separately print the appointment based on your requirement.

## Schedule Print

You can print the Schedule control by using print() method. Use the following code example to print the Schedule control.

{% tabs %}
 

{% highlight CSHTML %}

<div>
<input class="print" type="button" value="Print" />
@(Html.EJ().Schedule("Schedule1")
// Add the necessary schedule properties here)
<script type="text/javascript">$(document).ready(function () {
// function to bind the click event to the button$('.print').bind("click", function () {
var obj = $("#Schedule1").data("ejSchedule");
// Public method to print the scheduleobj.print();});});
</script>
{% endhighlight %}
{% highlight C# %}     
      // follow the code as same as declared in Read Only part</td></tr>
{% endhighlight %}
{% endtabs %} 

Execute the above code to render the following output.

![](Print_images/Print_img1.png)


Schedule with print button
{:.caption}

Click the print button to render the following output.



![](Print_images/Print_img2.png)

Schedule with Print window
{:.caption}

## Appointment Print

* In Schedule control, you can print the appointment alone by using context menu. Add print as menu item in the context menu settings as in the following code example.


{% tabs %}

{% highlight CSHTML %}

@(Html.EJ()
.Schedule("Schedule1")
// To Add the Context menu settings
.ContextMenuSettings(cms =>
cms.Enable(true)
// To Add menu items.MenuItems(item=>
item.Appointment(ViewBag.app)))
// Add the Appointment setting collection here)
{% endhighlight %}
{% highlight C# %}

public ActionResult Print()
{
	// create list for menu item collection
	List<Appointment> appointment = new List<Appointment>();
	appointment.Add(new Appointment() { Id = "open", Text = "Open Appointment" });
	appointment.Add(new Appointment() { Id = "delete", Text = "Delete Appointment" });
	// To Add print item in that collection.
	appointment.Add(new Appointment() { Id = "print", Text = "Print Appointment" });
	var DataSource = new ScheduleDataDataContext().DefaultSchedules.ToList();
	ViewBag.dataSource = DataSource;ViewBag.app = appointment;
	return View();
}
{% endhighlight %}
{% endtabs %} 

* Right click on the appointment and select print appointment in the context menu as follows.



![](Print_images/Print_img3.png)

Schedule with Print option in Context Menu_
{:.caption}

* Now, the widow is promoted to new document with appointment details and print window opens.



![](Print_images/Print_img4.png)

Schedule with Appointment Print
{:.caption}
