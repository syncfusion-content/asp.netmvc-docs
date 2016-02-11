---
layout: post
title: Globalization and Localization
description: Globalize formatting and Localize strings in DatePicker  
platform: ejmvc
control: DatePicker
documentation: ug
---
# Globalization

Essential ASP.NET MVC DatePicker has been provided with inbuilt localization support, so that it will be able adapt based on culture specific locale defined for it. 

More than 350 culture specific files are available to localize the date. To know more about EJ globalize support, please refer the below link      
 [http://help.syncfusion.com/js/localization](http://help.syncfusion.com/js/localization) 

N> All the culture-specific script files are available within the below specified location, once you have installed Essential Studio in your machine, therefore it is not necessary to download these files explicitly.

<table>
<tr>
<td>

    (installed location)\Syncfusion\Essential Studio\13.4.0.53\JavaScript\assets\scripts\cultures

    For example, If you have installed the Essential Studio package within C:\Program Files (x86), then navigate to the below location, 
    C:\Program Files (x86)\Syncfusion\Essential Studio\13.4.0.53\JavaScript\assets\scripts\cultures

</td></tr>
</table>
To translate our control content from default English to any of the culture, say For example - German language, then you need to refer the ej.culture.de-DE.min.js file in your application,

The **en-US** locale is currently being used as default culture in DatePicker. You can set any other culture to DatePicker by using **Locale** property. Below code example shows German cultured DatePicker.

Refer the below German culture file in head section of html page after the reference of **ej.web.all.min.js** file.

 {% highlight cshtml %}
   
    <script src="http://cdn.syncfusion.com/13.4.0.53/js/cultures/ej.culture.de-DE.min.js"></script>
                
 {% endhighlight %}
 

Set German culture to DatePicker at initialization.


{% highlight cshtml %}

    @Html.EJ().DatePicker("datepick").Value(System.DateTime.Now).Locale("de-DE")

{% endhighlight %}

## Watermark and Today Button Text

By default the EJMVC DatePicker input has “select date” as watermark text, you can change this value by using [WatermarkText](http://help.syncfusion.com/js/api/ejdatepicker#members:watermarktext) property. Also there’s a today button in DatePicker calendar which allows you to quick select the current date, you can change this value by using **ButtonText** property.

{% highlight cshtml %}

    @*sets watermark text and button text*@

    @Html.EJ().DatePicker("datepick").Value(System.DateTime.Now).WatermarkText("enter the date value").ButtonText("current date")


{% endhighlight %}

Based on culture specific, only date gets localized but by changing the watermark and button text, you can completely localize the DatePicker UI too.

Refer below code example to update those value based some culture say for example English and German.

{% highlight js %}

        //create instance for datePicker.
    // only after control creation we can get dateObj otherwise it throws exception.
    var dateObj = $("#datepick").ejDatePicker('instance');

    //condition to check English culture and change watermark and button text using dateObj.
    if (ej.cultureObject.name == "en-US") {
        dateObj.option({ buttonText: "Today", watermarkText: "select date" })
    }

    //condition to check German culture and change watermark and button text using dateObj.
    if (ej.cultureObject.name == "de-DE") {
        dateObj.option({ buttonText: "heute", watermarkText: "Datum auswählen" })
    } 


{% endhighlight %}
