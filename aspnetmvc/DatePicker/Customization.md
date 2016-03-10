---
layout: post
title: DatePicker Customization
description: DatePicker customization options such as dimension, highlight dates, other months, etc.
platform: ejmvc
control: DatePicker
documentation: ug
---
# Customization

EJMVC DatePicker appearance can be customized using below listed properties. 

## Set Dimension 

By default DatePicker has standard height and width (height: "30" and width: "143"). You can change this height and width by using [Height](http://help.syncfusion.com/js/api/ejdatepicker#members:height) and [Width](http://help.syncfusion.com/js/api/ejdatepicker#members:width) property respectively.


{% highlight cshtml %}

        @*sets height and width of the datepicker control*@

        @Html.EJ().DatePicker("datepick").Height("50px").Width("300px")


{% endhighlight %}


Since EJMVC DatePicker is a form control and you can make it as responsive by specifying its width as **100%**.


{% highlight cshtml %}

        @*sets width as 100 percentage*@

        @Html.EJ().DatePicker("datepick").Width("100%")


{% endhighlight %}


## Show Footer

You can show or hide the footer of EJMVC DatePicker calendar by using [ShowFooter](http://help.syncfusion.com/js/api/ejdatepicker#members:showfooter) property. 

{% highlight cshtml %}
    
    @*hides the footer in popup calendar*@

    @Html.EJ().DatePicker("datepick").ShowFooter(false)
    
{% endhighlight %}


N>  Footer contains the today button to quickly navigate to the current date. By turning off it, you have to select current date by manually. 


## Show Popup Button

EJMVC DatePicker input textbox  contains a button to open the DatePicker calendar. You can hide this DatePicker calendar button using [ShowPopupButton](http://help.syncfusion.com/js/api/ejdatepicker#members:showpopupbutton) value as false.

By hiding this button, you can open the DatePicker by focusing the input textbox element itself.

{% highlight cshtml %}

    @*hides the popup calendar button*@

    @Html.EJ().DatePicker("datepick").ShowPopupButton(false)


{% endhighlight %}

## Show Other Months

You can show or hide the other month days from EJMVC DatePicker calendar by using [ShowOtherMonths](http://help.syncfusion.com/js/api/ejdatepicker#members:showothermonths) property.

{% highlight cshtml %}

    @*hides the days of other months in calendar*@

    @Html.EJ().DatePicker("datepick").ShowOtherMonths(false)


{% endhighlight %}

## Highlight Special Date

The Essential ASP.NET MVC DatePicker allows you to highlight the special dates in EJMVC DatePicker calendar by using [SpecialDates](http://help.syncfusion.com/js/api/ejdatepicker#members:specialdates) property. It receives the list of "dataSpecial" date fields such as, in which the data should contain the date value, icon CSS class and tooltip as field values with any names.

Special Date property has following properties,

<table>
<tr>
<th>
Members</th><th>
Description</th></tr>
<tr>
<td>
Date<br/><br/></td><td>
It specifies the mapping field of special date<br/><br/></td></tr>
<tr>
<td>
IconClass<br/><br/></td><td>
It specifies the mapping field of icon CSS class.<br/><br/></td></tr>
<tr>
<td>
Tooltip<br/><br/></td><td>
It specifies the mapping field of tool tip text.<br/><br/></td></tr>
</table>


{% highlight cshtml %}

    @*sets the special date in datepicker calendar*@

    @Html.EJ().DatePicker("datepick").SpecialDates(spl => { spl.Add().Date("28/06/2015").IconClass("birthday").Tooltip("xxx birthday"); })
       
{% endhighlight %}
