---
layout: post
title: How-to
description: How-to section - The frequently used options with Pager 
platform: ejmvc
control: Pager
documentation: ug
---
# How to?

## Render Pager from Code behind

Pager can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of Pager properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (Pager) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class PagerController : Controller
    {
        // GET: Pager
        public ActionResult PagerFeatures()
        {
            //Initializing the Pager model

            PagerProperties PagerObj = new PagerProperties();

            //Initializing the datasource and other properties
            PagerObj.TotalRecordsCount = 20;
            PagerObj.PageSize = 1;

            //Passing Pager properties using the ViewData
            ViewData["PagerModel"] = PagerObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the Pager properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().Pager("searchCustomer",(Syncfusion.JavaScript.Models.PagerProperties)ViewData["PagerModel"]).Render();
}

{% endhighlight %}
