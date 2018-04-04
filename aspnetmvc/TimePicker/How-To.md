---
layout: post
title: How-to
description: How-to section - The frequently used options with TimePicker 
platform: ejmvc
control: TimePicker
documentation: ug
---
# How to?

## Render TimePicker from Code behind

TimePicker can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of TimePicker properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (TimePicker) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class TimePickerController : Controller
    {
        // GET: TimePicker
        public ActionResult TimePickerFeatures()
        {
            //Initializing the TimePicker model

            TimePickerProperties TimeObj = new TimePickerProperties();

            //Initializing the datasource and other properties
            TimeObj.Width = "300px";
            TimeObj.Interval= 60;
            TimeObj.Value = "10:10 AM";

            //Passing TimePicker properties using the ViewData
            ViewData["TimeModel"] = TimeObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the TimePicker properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().TimePicker("searchCustomer",(Syncfusion.JavaScript.Models.TimePickerProperties)ViewData["TimeModel"]).Render();
}

{% endhighlight %}
