---
layout: post
title: How-to
description: How-to section - The frequently used options with ColorPicker 
platform: ejmvc
control: ColorPicker
documentation: ug
---
# How to?

## Render ColorPicker from Code behind

ColorPicker can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of ColorPicker properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (ColorPicker) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class ColorPickerController : Controller
    {
        // GET: ColorPicker
        public ActionResult ColorPickerFeatures()
        {
            //Initializing the ColorPicker model

            ColorPickerProperties ColorObj = new ColorPickerProperties();

            //Initializing the datasource and other properties
              ColorObj.ShowPreview= true;
              ColorObj.Value = "#278787";

            //Passing ColorPicker properties using the ViewData
            ViewData["ColorModel"] = ColorObjObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the ColorPicker properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().ColorPicker("searchCustomer",(Syncfusion.JavaScript.Models.ColorPickerProperties)ViewData["Colorodel"]).Render();
}

{% endhighlight %}
