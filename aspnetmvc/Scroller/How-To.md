---
layout: post
title: How-to
description: How-to section - The frequently used options with Scroller 
platform: ejmvc
control: Scroller
documentation: ug
---
# How to?

## Render Scroller from Code behind

Scroller can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of Scroller properties in the controller.

{% highlight c# %}

<div>
        @* Wrapper div for Scroller.*@

        <div class="inner-content" style="width:400px;padding:15px">
            @* Content div*@

            <h3> MVC </h3>

            <p>

                Model–view–controller (MVC) is a software architecture pattern which

                separates the representation of information from the user's interaction

                with it. The model consists of application data, business rules, logic, and

                functions. A view can be any output representation of data, such as a chart

                or a diagram.

            </p>

        </div>

    </div>

</div>


//Namespace to get the JavaScript (Scroller) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class ScrollerController : Controller
    {
        // GET: Scroller
        public ActionResult ScrollerFeatures()
        {
            //Initializing the Scroller model

            ScrollerProperties ScrollerObj = new ScrollerProperties();

            //Initializing the datasource and other properties
            ScrollerObj.Height = 150;
            ScrollerObj.Width = 300;

            //Passing Scroller properties using the ViewData
            ViewData["ScrollerModel"] = ScrollerObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the Scroller properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().Scroller("scrollContent",(Syncfusion.JavaScript.Models.ScrollerProperties)ViewData["ScrollerModel"]).Render();
}

{% endhighlight %}
