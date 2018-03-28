---
layout: post
title: How to
description: How to
platform: ejmvc
control: RadialSlider
documentation: ug
---
# How to

## Render RadialSlider from Code behind

RadialSlider can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of RadialSlider properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (RadialSlider) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class RadialsliderController: Controller
    {
        public ActionResult RadialSliderFeatures()
        {

            //Initializing the RadialSlider model

            RadialSliderProperties sliderObj = new RadialSliderProperties();

            //Initializing the other properties

            sliderObj.StrokeWidth = 4;
            sliderObj.ShowInnerCircle = true;
            sliderObj.InnerCircleImageUrl = "http://js.syncfusion.com/demos/web/content/images/radialslider/chevron-right.png";

            //Passing RadialSlider properties using the ViewData

            ViewData["RSliserModel"] = sliderObj;

            return View();
        }
    }
}

{% endhighlight %}

Binding the RadialSlider properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

  @{
      Html.EJ().RadialSlider("Radialslider1", (Syncfusion.JavaScript.Models.RadialSliderProperties)ViewData["RSliserModel"]).Render();
}

{% endhighlight %}