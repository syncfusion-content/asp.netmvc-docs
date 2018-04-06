---
layout: post
title: How-to
description: How-to section - The frequently used options with Button 
platform: ejmvc
control: Button
documentation: ug
---
# How to?

## Render Button from Code behind

Button can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of Button properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (Button) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class ButtonController : Controller
    {
        // GET: Button
        public ActionResult ButtonFeatures()
        {
            //Initializing the Button model

            ButtonProperties BtnObj = new ButtonProperties();

            //Initializing the datasource and other properties
            BtnObj.Text = "Button";
            BtnObj.ShowRoundedCorner = true;

            //Passing Button properties using the ViewData
            ViewData["BtnModel"] = BtnObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the Button properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().Button("searchCustomer",(Syncfusion.JavaScript.Models.ButtonProperties)ViewData["BtnModel"]).Render();
}

{% endhighlight %}
