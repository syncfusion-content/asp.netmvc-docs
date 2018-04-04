---
layout: post
title: How-to
description: How-to section - The frequently used options with RadioButton 
platform: ejmvc
control: RadioButton
documentation: ug
---
# How to?

## Render RadioButton from Code behind

RadioButton can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of RadioButton properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (RadioButton) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class RadioButtonController : Controller
    {
        // GET: RadioButton
        public ActionResult RadioButtonFeatures()
        {
            //Initializing the RadioButton model

            RadioButtonProperties BtnObj = new RadioButtonProperties();

            //Initializing the datasource and other properties
            BtnObj.Checked = true;
            BtnObj.Size = RadioButtonSize.Medium;
            BtnObj.Text = "Computer";

            //Passing RadioButton properties using the ViewData
            ViewData["BtnModel"] = BtnObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the RadioButton properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().RadioButton("searchCustomer",(Syncfusion.JavaScript.Models.RadioButtonProperties)ViewData["Colorodel"]).Render();
}

{% endhighlight %}
