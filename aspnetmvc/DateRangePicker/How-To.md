---
layout: post
title: How-to
description: How-to section - The frequently used options with DateRangepicker 
platform: ejmvc
control: DateRangePicker
documentation: ug
---
# How to?

## Render DateRangePicker from Code behind

DateRangePicker can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of DateRangePicker properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (DateRangePicker) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class DateRangePickerController : Controller
    {
        // GET: DateRangepicker
        public ActionResult DateRangePickerFeatures()
        {
            //Initializing the DateRangePicker model

            DateRangePickerProperties DateObj = new DateRangePickerProperties();

            //Initializing the datasource and other properties
             DateObj.Width = "300px";
             DateObj.StartDate = "2/2/2018";
             DateObj.EndDate = "2/25/2018";

            //Passing DateRangePicker properties using the ViewData
            ViewData["DateModel"] = DateObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the DateRangePicker properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().DateRangePicker("searchCustomer",(Syncfusion.JavaScript.Models.DateRangePickerProperties)ViewData["DateModel"]).Render();
}

{% endhighlight %}
