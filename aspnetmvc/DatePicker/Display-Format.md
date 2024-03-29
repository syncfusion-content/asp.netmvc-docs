---
layout: post
title: Syncfusion Essential JS DatePicker Display Format
description: Configuring display format of DatePicker
platform: ejmvc
control: DatePicker
documentation: ug
---
# Formatting

Formatting is the way of displaying the date or number as string in some standard format which is based on culture specific or user need.

Below table shows the patterns to format date value.

<table>
<tr>
<th>
Format Pattern </th><th>
Description </th><th>
Result</th></tr>
<tr>
<td>
d<br/><br/></td><td>
The day of the month between 1 and 31 <br/><br/></td><td>
"1"  to "31"<br/><br/></td></tr>
<tr>
<td>
dd<br/><br/></td><td>
The day of the month with leading zero if required.<br/><br/></td><td>
"01" to "31"<br/><br/></td></tr>
<tr>
<td>
ddd<br/><br/></td><td>
Abbreviated day name.<br/><br/></td><td>
"Mon" to "Sun"<br/><br/></td></tr>
<tr>
<td>
dddd<br/><br/></td><td>
The full day name<br/><br/></td><td>
"Monday" to "Sunday"<br/><br/></td></tr>
<tr>
<td>
<br/><br/></td><td>
<br/><br/></td><td>
<br/><br/></td></tr>
<tr>
<td>
M<br/><br/></td><td>
The month of the year between 1 - 12<br/><br/></td><td>
"1" to "12"<br/><br/></td></tr>
<tr>
<td>
MM<br/><br/></td><td>
The month of the year with leading zero if required<br/><br/></td><td>
"01" to "12"<br/><br/></td></tr>
<tr>
<td>
MMM<br/><br/></td><td>
Abbreviated month name<br/><br/></td><td>
"Jan" to "Dec"<br/><br/></td></tr>
<tr>
<td>
MMMM<br/><br/></td><td>
The full month name<br/><br/></td><td>
"January" to "December"<br/><br/></td></tr>
<tr>
<td>
<br/><br/></td><td>
<br/><br/></td><td>
<br/><br/></td></tr>
<tr>
<td>
yy<br/><br/></td><td>
The year as a two-digit number<br/><br/></td><td>
"99" or "08"<br/><br/></td></tr>
<tr>
<td>
yyyy<br/><br/></td><td>
The full four digit year<br/><br/></td><td>
"1999" or "2008"<br/><br/></td></tr>
</table>

## Date Format

Each culture has some specific date format. Date format defines a format or structure of the displayed date in the textbox of EJMVC DatePicker component. You can change the date format by using [DateFormat](https://help.syncfusion.com/js/api/ejdatepicker#members:dateformat) property

The standard formats are listed as follows

<table>
<tr>
<th>
Format Name <br/><br/></th><th>
Formats <br/><br/></th><th>
Input Date <br/><br/></th><th>
Formatted Date<br/><br/></th></tr>
<tr>
<td>
Default<br/><br/></td><td>
M/d/yyyy<br/><br/></td><td>
"12/01/2020"<br/><br/></td><td>
"12/1/2020"<br/><br/></td></tr>
<tr>
<td>
Short<br/><br/></td><td>
"d M, y"<br/><br/></td><td>
"12/14/2020"<br/><br/></td><td>
"14 12,20"<br/><br/></td></tr>
<tr>
<td>
Medium <br/><br/></td><td>
"d MM, y"<br/><br/></td><td>
"12/14/2020"<br/><br/></td><td>
"14 12, 20"<br/><br/></td></tr>
<tr>
<td>
Full <br/><br/></td><td>
dddd, d MMMM, yy<br/><br/></td><td>
"12/14/2020"<br/><br/></td><td>
"Monday, 14 December, 20"<br/><br/></td></tr>
<tr>
<td>
UTC<br/><br/></td><td>
yyyy-MM-dd<br/><br/></td><td>
"12/14/2020"<br/><br/></td><td>
"2020-12-14"<br/><br/></td></tr>
</table>
By default **en-US** culture Date format is "M/d/yyyy".


{% highlight cshtml %}

        @*sets en-US culture with specified date format*@

        @Html.EJ().DatePicker("datePicker").Value(System.DateTime.Now).Locale("en-US").DateFormat("yyyy/dd/MM")

{% endhighlight %}

![date-format](display-format-images/image1.png)

To get the culture and date format of DatePicker, refer the below code example


{% highlight js %}

        // create instance for datePicker

        // only after control creation we can get dateObj otherwise it throws exception

        var dateObj = $("#datePicker").ejDatePicker('instance');

        dateObj.option('locale'); //returns the culture in string

        dateObj.option('dateFormat');// returns the date Format in string  

{% endhighlight %}


N> By default date format is based on culture specific. You have to refer the required culture specific files in layout page of your web application in order to localize DatePicker and customize different format for that culture. Refer this [link](https://help.syncfusion.com/aspnetmvc/datepicker/globalization) to know more about this functionality support in DatePicker.

## Header Format

EJMVC DatePicker calendar consists of header, day header, days and footer section. In which header section shows the current view of DatePicker calendar by displaying the selected day or month or year. It can be formatted as like date format by using [HeaderFormat](https://help.syncfusion.com/js/api/ejdatepicker#members:headerformat) property.

{% highlight cshtml %}

        @*sets the selected header format to display in header*@

        @Html.EJ().DatePicker("datePicker").HeaderFormat("yyyy MMMM").Value("12/14/2020")


{% endhighlight %}

![header-format](display-format-images/image2.png)

## Day Header

Day header determines the days name to be displayed in terms of short, medium and long in EJMVC DatePicker calendar by using [DayHeaderFormat](https://help.syncfusion.com/js/api/ejdatepicker#members:dayheaderformat) property. Also the DatePicker calendar size varies with this specified values.

{% highlight cshtml %}

            @*sets the day header as long*@

            @Html.EJ().DatePicker("datePicker").DayHeaderFormat(Header.Long)


{% endhighlight %}

![day-header](display-format-images/image4.png)

## Tooltip with Formatting

The EJMVC DatePicker calendar shows tooltip on hovering the date by specifying the formatted date of hovered date. Its helps you to get clear view about the date going to select. You can show or hide this tooltip option by using [ShowTooltip](https://help.syncfusion.com/js/api/ejdatepicker) property.

You can also change the format of tooltip by using [TooltipFormat](https://help.syncfusion.com/js/api/ejdatepicker) property. Below codes example allows to show tooltip and format its value. 

{% highlight cshtml %}
   
    @*sets and shows tooltip on hovering date on calendar*@

    @Html.EJ().DatePicker("datePicker").ShowTooltip(true).TooltipFormat("dd/MM/yy").Value("12/14/2020")
       
{% endhighlight %}

![tooltip](display-format-images/image3.png)
