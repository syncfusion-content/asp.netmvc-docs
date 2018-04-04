---
layout: post
title: How-to
description: How-to section - The frequently used options with DatePicker 
platform: ejmvc
control: DatePicker
documentation: ug
---
# How to?

## Customizing template with range selection between two DatePicker. 

You can customize the date field to emphasize the particular dates in EJMVC DatePicker calendar with help of [SpecialDates](http://help.syncfusion.com/js/api/ejdatepicker#members:specialdates) and set the date range using [MinDate](http://help.syncfusion.com/js/api/ejdatepicker#members:mindate) and [MaxDate](http://help.syncfusion.com/js/api/ejdatepicker#members:maxdate) property. 

## Validating the date value in server side
	
The EJMVC DatePicker control, is a form control which  allows us to validate the date value in client side and server side actions. Please refer from the [validation](https://www.syncfusion.com/kb/5433/how-to-achieve-the-required-field-validation-for-datepicker-control-in-asp-net-mvc) to know more about this with EJMVC DatePicker control.

## Localize DatePicker with browser specific culture

You can get the browser culture name at page load or document ready state. Based on the culture name, EJMVC DatePicker can be initiated with that specific culture value by assigning to [Locale](http://help.syncfusion.com/js/api/ejdatepicker#members:locale) property. 

## Disable specific dates to restrict user

EJMVC DatePicker allows you to restrict date selection in specific range by using date range option. But you can also restrict selective date in DatePicker calendar by utilizing [BeforeDateCreate](http://help.syncfusion.com/js/api/ejdatepicker#events:beforedatecreate) event. This event will get triggered at each date creation. So you can disable the selective date in this event to restrict the user.

{% highlight cshtml %}

    @*handler to listen each date create*@

    @Html.EJ().DatePicker("datePicker").ClientSideEvents(clientSideEvent => clientSideEvent.BeforeDateCreate("restrictDate"))

    <script>   
   
    //event get triggered for each date create.
    function restrictDate(args) {
       //date to disable in calendar to restrict selection.
       var disableDate = new Date("09/22/2015"); 
       //compares two and adds the disable class.
       if (+args.date === +disableDate)                
           args.element.addClass('e-disable');  
           // args contains current date and its element.          
    }
         
    </script>


{% endhighlight %}

## How to integrate with bootstrap grid system? 

EJMVC DatePicker is responsive control, you have to just set the input element width as 100%. In Bootstrap grid layout use the below code example to get responsive textbox 

{% highlight cshtml %}

    @*sets the height and width to 100%*@

    @Html.EJ().DatePicker("datePicker").Height("100%").Width("100%")


{% endhighlight %}

## Render Datepicker from Code behind

DatePicker can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of DatePicker properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (DatePicker) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class DatePickerController : Controller
    {
        // GET: DatePicker
        public ActionResult DatePickerFeatures()
        {
            //Initializing the DatePicker model

            DatePickerProperties DateObj = new DatePickerProperties();

            //Initializing the datasource and other properties
            DateObj.Width = "300px";
            DateObj.Value = "12/12/2018";

            //Passing DatePicker properties using the ViewData
            ViewData["DateModel"] = DateObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the DatePicker properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().DatePicker("searchCustomer",(Syncfusion.JavaScript.Models.DatePickerProperties)ViewData["DateModel"]).Render();
}

{% endhighlight %}
