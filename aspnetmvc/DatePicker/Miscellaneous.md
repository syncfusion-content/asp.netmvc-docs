---
layout: post
title: Miscellaneous
description: Configure start day of week, step month, and enabled/disabled state of DatePicker
platform: ejmvc
control: DatePicker
documentation: ug
---
# Miscellaneous 

## Start Day

By default EJMVC DatePicker calendar starts with "Sunday" and ends with "Monday". You can redefine this start day by using [StartDay](https://help.syncfusion.com/js/api/ejdatepicker#members:startday) property.

Refer below code to start Wednesday as start day. 


{% highlight cshtml %}

        @*sets start day as Wednesday in calendar*@

        @Html.EJ().DatePicker("datePicker").StartDay(3)

{% endhighlight %}


## Step Months

The EJMVC DatePicker calendar allows you to quick navigate back and forth from one month to previous or next month by clicking the arrow button. By default it is navigate one by one month. You can also navigate by skipping months in odd or even or any count by using [StepMonths](https://help.syncfusion.com/js/api/ejdatepicker#members:stepmonths) property. 


{% highlight cshtml %}

        @*skips the one months from current month(July to Sept to Nov)*@

        @Html.EJ().DatePicker("datePicker").StepMonths(2)


{% endhighlight %}


## Read Only

You can make EJMVC DatePicker as read only by setting [ReadOnly](https://help.syncfusion.com/js/api/ejdatepicker#members:readonly) property as true. It allows only to read the value and it cannot be changed by interaction.


{% highlight cshtml %}

        @*sets DatePicker as read only*@

        @Html.EJ().DatePicker("datePicker").ReadOnly(true)

{% endhighlight %}


## Enable or Disable

You can enable or disable the EJMVC DatePicker textbox by using [Enabled](https://help.syncfusion.com/js/api/ejdatepicker#members:enabled) property. In inline mode DatePicker calendar also gets enabled or disabled. 


{% highlight cshtml %}

        @*disables the DatePicker textbox*@

        @Html.EJ().DatePicker("datePicker").Enabled(false)
    

{% endhighlight %}

