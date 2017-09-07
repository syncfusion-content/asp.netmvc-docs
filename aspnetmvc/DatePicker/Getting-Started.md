---
layout: post
title: Getting started with DatePicker
description: To get start with DatePicker with required assemblies,files
platform: ejmvc
control: DatePicker
documentation: ug
---
# Getting Started

## A new MVC application and required assemblies with dependent files

To get start with Essential ASP.NET MVC DatePicker, create a new  MVC application and add the required assemblies in references and then refer the below specified dependent CSS file as well as scripts

To create a MVC project and add necessary assemblies you can use the help of the given [MVC-Getting Started](http://help.syncfusion.com/aspnetmvc/getting-started) Documentation.

CSS file

* [ej.web.all.min.css](http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css)  includes all widgets styles (To know more about theme refer [Theming in Essential JavaScript Component](http://help.syncfusion.com/js/theming-in-essential-javascript-components#))

External script files

* [jQuery](http://jquery.com/#) (from the version 1.7.1 to 3.1.0)

jQuery.easing external dependency has been removed from version 14.3.0.49 onwards. Kindly include this jQuery.easing dependency for versions lesser than 14.3.0.49 in order to support animation effects.
Internal script files

<table>
<tr>
<th>
File</th><th>
Description / Usage </th></tr>
<tr>
<td>
ej.core.min.js<br/><br/></td><td>
Includes only the widget basic functions and Framework features. Must be referred always before using all the JS controls<br/><br/></td></tr>
<tr>
<td>
ej.globalize.min.js<br/><br/></td><td>
To support the globalization.<br/><br/></td></tr>
<tr>
<td>
ej.datepicker.min.js<br/><br/></td><td>
DatePicker plugin.<br/><br/></td></tr>
</table>

N> From V13.4.0.53 onwards, jQuery.globalize.min.js file has been replaced with our script file ej.globalize.min.js to support the globalization for our widgets. For version lower than 13.4.0.53, refer jQuery.globalize.min.js.

You can make use of **ej.web.all.min.js** file which encapsulates all EJMVC components and frameworks in single file.


* [ej.web.all.min.js](http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js) - includes all web widgets.

If you are using NuGet packages, then required files to render the EJMVC components, will get included in corresponding location automatically in your application.

N>  In production, we highly recommend you to use our [custom script generator](http://helpjs.syncfusion.com/js/include-only-the-needed-widgets#) to create custom script file with required controls and its dependencies only. Also to reduce the file size further please use [GZip compression](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer?hl=en#text-compression-with-gzip) in your server. 

Below is a simple Layout CSHTML file with required CSS and script reference added to create the Essential ASP.NET MVC DatePicker


{% highlight cshtml %}
    
    <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>@ViewBag.Title - My ASP.NET MVC Application</title>
       
    <link rel="stylesheet" href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" />
    <script src="https://code.jquery.com/jquery-1.10.2.min.js"></script>
    <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js"> </script>
    <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/common/ej.unobtrusive.min.js"></script>

    </head>
    
{% endhighlight %}

## DatePicker Initialization

The Essential ASP.NET MVC DatePicker can be created using HTML helper like below code example (Razor code)

{% highlight cshtml %}

    @Html.EJ().DatePicker("datePicker")
            
{% endhighlight %}

N>  DatePicker is a form control, so on form submitting its value can be received by its name, and normally id has been treated as name. If you want to set the name manually you can use our HtmlAttributes property. You can get this property related information from [here](http://help.syncfusion.com/js/api/ejdatepicker#members:htmlattributes)

## Get / Set value

The Essential ASP.NET MVC DatePicker provides an options to configure all its properties and to get its value. DatePicker value can be assigned during initialization or at run time. Below code shows how to assign values at initialization.

{% highlight cshtml %}

    @Html.EJ().DatePicker("datePicker").Value(System.DateTime.Now).DateFormat("yyyy/MM/dd")

{% endhighlight %}

You can assign values to existing EJMVC DatePicker using its instance. Consider that you going to set date value at button click, refer the below code example.

{% highlight js %}

        <script>

        //bind below onClick action to button
        function onClick() {

            //create instance for datePicker.
            // only after control creation we can get dateObj otherwise it throws exception.
            var dateObj = $("#datePicker").ejDatePicker('instance');

            //set value using date object
            dateObj.option('value', new Date());

            //get value using date object and displays in alert box
            alert(dateObj.option('value'));
        }
  
    </script>


{% endhighlight %}

N> Existing DatePicker instance can be created by jQuery.data() and you can control the API’s of DatePicker behavior.

## Client Side Events

You can handle the all available client side events in Essential JavaScript DatePicker. Refer the below code example to use the client side event in EJMVC DatePicker

{% highlight cshtml %}

    @Html.EJ().DatePicker("datePicker").Value(System.DateTime.Now).ClientSideEvents(e => e.Change("onChange"))
	
    <script>    
    
    function onChange(args) {
        //args contains entire model of DatePicker to get the value of all properties.

        //alert popup shows the previous date and selected date.
        alert(" previous date is : " + args.prevDate + " \n selected date is : " + args.value);
    }     
    </script>

{% endhighlight %}


## Strongly Typed HTML Helper

EJMVC DatePicker can be created using DatePickerFor extension, which behaves as strongly typed HTML helper. This reduce the run time issues while using model values in DatePickerFor , since it will find the issues if any in compilation time itself. Also, to know about the setting model properties to DatePickerFor control, please refer the link: 

  [https://www.syncfusion.com/kb/4670/how-to-define-properties-for-for-controls](https://www.syncfusion.com/kb/4670/how-to-define-properties-for-for-controls)

Please refer the below code to create the DatePickerFor control in your application

{% highlight cshtml %}

    @Html.EJ().DatePickerFor(model => model.datepicker, (Syncfusion.JavaScript.Models.DatePickerProperties)ViewData["date"])
    @Html.ValidationMessageFor(model => model.datepicker1)


{% endhighlight %}