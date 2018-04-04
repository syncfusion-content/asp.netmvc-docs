---
layout: post
title: How-to
description: How-to section - The frequently used options with DateTimePicker 
platform: ejmvc
control: DateTimePicker
documentation: ug
---
# How to?

## Render DateTimePicker from Code behind

DateTimePicker can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of DateTimePicker properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (DateTimePicker) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class DateTimePickerController : Controller
    {
        // GET: DateTimePicker
        public ActionResult DateTimePickerFeatures()
        {
            //Initializing the DateTimePicker model

            DateTimePickerProperties DateObj = new DateTimePickerProperties();

            //Initializing the datasource and other properties
              DateObj.Width = "300px";
              DateObj.Value = "05/15/2015 09:00 AM";

            //Passing DateTimePicker properties using the ViewData
            ViewData["DateModel"] = DateObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the DateTimePicker properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().DateTimePicker("searchCustomer",(Syncfusion.JavaScript.Models.DateTimePickerProperties)ViewData["DateModel"]).Render();
}

{% endhighlight %}
