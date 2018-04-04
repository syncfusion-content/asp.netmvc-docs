---
layout: post
title: How-to
description: How-to section - The frequently used options with ToggleButton 
platform: ejmvc
control: ToggleButton
documentation: ug
---
# How to?

## Render ToggleButton from Code behind

ToggleButton can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of ToggleButton properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (ToggleButton) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class ToggleButtonController : Controller
    {
        // GET: ToggleButton
        public ActionResult ToggleButtonFeatures()
        {
            //Initializing the ToggleButton model

            ToggleButtonProperties BtnObj = new ToggleButtonProperties();

            //Initializing the datasource and other properties
            BtnObj.ActiveText = "pause";
            BtnObj.DefaultText = "Play";
            BtnObj.ShowRoundedCorner = true;
            BtnObj.Size = ButtonSize.Large;

            //Passing ToggleButton properties using the ViewData
            ViewData["BtnModel"] = BtnObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the ToggleButton properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().ToggleButton("searchCustomer",(Syncfusion.JavaScript.Models.ToggleButtonProperties)ViewData["Colorodel"]).Render();
}

{% endhighlight %}
