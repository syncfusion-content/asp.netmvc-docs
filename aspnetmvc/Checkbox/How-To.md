---
layout: post
title: How-to
description: How-to section - The frequently used options with Checkbox 
platform: ejmvc
control: Checkbox
documentation: ug
---
# How to?

## Render Checkbox from Code behind

Checkbox can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of Checkbox properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (Checkbox) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class CheckboxController : Controller
    {
        // GET: Checkbox
        public ActionResult CheckboxFeatures()
        {
            //Initializing the Checkbox model

            CheckBoxProperties BtnObj = new CheckBoxProperties();

            //Initializing the datasource and other properties
            BtnObj.Checked = true;
            BtnObj.Text = "Checkbox";
            BtnObj.ShowRoundedCorner = true;

            //Passing Checkbox properties using the ViewData
            ViewData["BtnModel"] = BtnObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the Checkbox properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().CheckBox("searchCustomer",(Syncfusion.JavaScript.Models.CheckBoxProperties)ViewData["Colorodel"]).Render();
}

{% endhighlight %}
