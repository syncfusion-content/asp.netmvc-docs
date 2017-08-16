---
layout: post
title: Getting Started | TimePicker | ASP.NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: TimePicker
documentation: ug
---

# Getting Started

This section explains briefly about how to create a TimePicker in your application with ASP.NET MVC.

## Create your first TimePicker in MVC

Essential MVCTimePicker provides support to display the time in your web page and allows you to pick a time from the list. In this section you can learn how to customize TimePickers in a real-time application. The following example shows you how to use the TimePicker control to book a hotel dining table booking application, within a limited time, in any day.

![](Getting-Started_images/Getting-Started_img1.png)



The above screenshot illustrates the functionality of a TimePicker, with a time range from morning to evening. You can select the time to book a table ranging from 9.00 AM to 10.00 PM in the current day. This avoids selecting a time prior to that day.



### Create a TimePicker

Essential MVC TimePicker widget has built-in features such as keyboard navigation, other time navigation with animations, and flexible APIs. You can easily create the TimePicker widget using simple TimePicker element as follows.

1. You can create an MVC Project and add necessary assemblies and scripts to it. Refer [MVC-Getting Started](https://help.syncfusion.com/aspnetmvc/getting-started) Documentation.
2. Add the following code to the corresponding view page to render the TimePicker.

   ~~~ cshtml


	@*Add the following code example to the corresponding CSHTML page to render TimePicker widget*@

	<table>

		<tr>

		<td class="table-cell">Date</td>

		<td class="table-cell">Time</td>

		<td class="table-cell">Person</td>

		</tr>

		<tr>

		<td class="table-cell">

			<span class="inner-display">

			@Html.EJ().DatePicker("startDate")

			</span>

		</td>

		<td class="table-cell">

			<span class="inner-display">

			@Html.EJ().TimePicker("timeStart")

			</span>

		</td>

		<td class="table-cell">

			<span class="inner-display">

			@Html.EJ().NumericTextbox("NumericTextbox").Value("0")

			</span>

		</td>

		</tr>

		<tr>

		<td></td>

		<td></td>

		<td class="table-cell">

			<span class="inner-display">

			@Html.EJ().Button("Submit").Width("100px").Size(ButtonSize.Small).Text("Submit").ClientSideEvents(s => s.Click("button"))

			</span>

		</td>

		</tr>

	</table>

   ~~~
   



3. Add the following styles to show the TimePicker control in horizontal order in the Content folder.

   ~~~ css


	<style type="text/css" class="cssStyles">

		.table-cell 
		{

		width: 70px;

		height: 10px;

		font-weight: bold;

		padding: 10px;

		}

		.inner-display 
		{

		display: inline-block;

		}

	</style>

   ~~~
   




4. Add the following code to the Layout page for DatePicker and TimePicker initialization.

   ~~~ js


	<script type="text/javascript">

		function button()

		{

		alert("You have Successfully booked");

		}

	</script>

   ~~~
   



5. The following screenshot displays the output for the above code.

   ![](Getting-Started_images/Getting-Started_img2.png)





6. Click the submit button in the application to render the following output.



   ![](Getting-Started_images/Getting-Started_img3.png)



### Set Min and Max Date

In a real-time scenario, the booking is open only for a limited time. You can select a date and time from the given range using the properties MinDate, MinTime and MaxDate, MaxTime that enables only the dates and times ranging between the MinDate, MinTime and MaxDate, MaxTime in the DatePicker and TimePicker.

1. Add the following code to the corresponding view page to render the TimePicker.

   ~~~ cshtml

	@*Add the following code example to the corresponding CSHTML page to render TimePicker widget*@

	<table>

		<tr>

			<td class="table-cell">Date</td>

			<td class="table-cell">StartTime</td>

			<td class="table-cell">EndTime</td>

			<td class="table-cell">Person</td>

		</tr>

		<tr>

			<td class="table-cell">

				<span class="inner-display">

					@Html.EJ().DatePicker("startDate").Value("5/11/2015").MinDate("5/11/2015").MaxDate("6/11/2015")

				</span>

			</td>

			<td class="table-cell">

				<span class="inner-display">

					@Html.EJ().TimePicker("timeStart").MinTime("9:00 AM").MaxTime("10:00 PM").Interval(60).ClientSideEvents(e => e.Select("selectedStartTime"))

				</span>

			</td>

			<td class="table-cell">

				<span class="inner-display">

					@Html.EJ().TimePicker("timeEnd").MinTime("9:00 AM").MaxTime("10:00 PM").Interval(60)

				</span>

			</td>

			<td class="table-cell">

				<span class="inner-display">

					@Html.EJ().NumericTextbox("NumericTextbox").Value("0")

				</span>

			</td>

		</tr>

		<tr>

			<td></td>

			<td></td>

			<td></td>

			<td class="table-cell">

				<span class="inner-display">

					@Html.EJ().Button("Submit").Width("100px").Size(ButtonSize.Small).Text("Submit").ClientSideEvents(s => s.Click("button"))

				</span>

			</td>

		</tr>

	</table>

   ~~~
   

2. Add the following styles to show the TimePicker control in horizontal order in the Content folder.

   ~~~ css

	<style type="text/css" class="cssStyles">

		.table-cell 
		{

		width: 70px;

		height: 10px;

		font-weight: bold;

		padding: 10px;

		}

		.inner-display 
		{

		display: inline-block;

		}


	</style>

   ~~~
   




3. Add the following code to the Layout page for DatePicker and TimePicker initialization.

   ~~~ js


		<script type="text/javascript">

		    function selectedStartTime(sender) {

			var selDate = sender.value; // mentions the selected time.

			minTimepicker = $("#timeEnd").data("ejTimePicker");// creating TimePicker object

			minTimepicker.setModel({ "minTime": selDate });// setting minTime property through setModel of TimePicker object.

		    }

		    function button()

		    {

			alert("You have Successfully booked");

		    }

		</script>

   ~~~
   





4. The following screenshot displays the output for the above code. 

![](Getting-Started_images/Getting-Started_img4.png)





You can select the Start time in the first TimePicker and select the End time within the given range. The second TimePicker start value is based on the first TimePicker’s selected value. This is illustrated in the following screenshots.



![](Getting-Started_images/Getting-Started_img5.png)


![](Getting-Started_images/Getting-Started_img6.png)



### Display Reserved Time 

An acknowledgment message appears when you click the Submit button. 

You can specify the alert message in the script as follows.

{% highlight js %}

<script type="text/javascript">

        function button()

            {



                    var a = $('#startDate').val();



                    var b = $('#timeStart').val();



                    var d = $('#timeEnd').val();



                    var c = $('#NumericTextbox').val();



                    alert("You have successfully booked\nDate    : " + a + "\nStartTime: " + b + "\nEndTime: " + d + " \nPerson   :  " + c);



            }

</script>

{% endhighlight %}


![](Getting-Started_images/Getting-Started_img7.png)



