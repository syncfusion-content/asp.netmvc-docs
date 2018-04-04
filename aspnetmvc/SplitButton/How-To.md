---
layout: post
title: How-to
description: How-to section - The frequently used options with SplitButton 
platform: ejmvc
control: SplitButton
documentation: ug
---
# How to?

## Render SplitButton from Code behind

SplitButton can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of SplitButton properties in the controller.

{% highlight c# %}

<ul id="target">

     <li><span>Open</span></li>

     <li><span>Save</span></li>

     <li><span>Delete</span></li>

</ul>

//Namespace to get the JavaScript (SplitButton) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class SplitButtonController : Controller
    {
        // GET: SplitButton
        public ActionResult SplitButtonFeatures()
        {
            //Initializing the SplitButton model

            SplitButtonProperties BtnObj = new SplitButtonProperties();

            //Initializing the datasource and other properties
            BtnObj.Text = "login";
            BtnObj.Size= ButtonSize.Medium;
            BtnObj.TargetID = "target";
            BtnObj.ShowRoundedCorner=true;

            //Passing SplitButton properties using the ViewData
            ViewData["BtnModel"] = BtnObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the SplitButton properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().SplitButton("searchCustomer",(Syncfusion.JavaScript.Models.SplitButtonProperties)ViewData["BtnModel"]).Render();
}

{% endhighlight %}
