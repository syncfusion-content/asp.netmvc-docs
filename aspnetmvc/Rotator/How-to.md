---
layout: post
title: How to
description: How to
platform: ejmvc
control: Rotator
documentation: ug
---
# How to

## Render Rotator from Code behind

Rotator can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side

The following code illustrates the initialization of Rotator properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (Rotator) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class RotatorController: Controller
    {
        public ActionResult RotatorFeatures()
        {

             // initialize the data list

           List<LocalData> localValues = new List<LocalData>();

            localValues.Add(new LocalData { Text = "Beautiful Bird", Url = "../Images/rotator/bird.jpg" });

            localValues.Add(new LocalData { Text = "Colorful Night", Url = "../Images/rotator/night.jpg" });

            localValues.Add(new LocalData { Text = "Technology", Url = "../Images/rotator/tablet.jpg" });

            localValues.Add(new LocalData { Text = "Nature", Url = "../Images/rotator/nature.jpg" });

            localValues.Add(new LocalData { Text = "Snow Fall", Url = "../Images/rotator/snowfall.jpg" });

            localValues.Add(new LocalData { Text = "Credit Card", Url = "../Images/rotator/card.jpg" });

            localValues.Add(new LocalData { Text = "Amazing Sculptures", Url = "../Images/rotator/sculpture.jpg" });

            //Initializing the Rotator model

            RotatorProperties RotatorObj = new RotatorProperties();

            //Initializing the datasource and other properties

            RotatorObj.DataSource = localValues;
            RotatorObj.RotatorFields.Text = "Text";
            RotatorObj.RotatorFields.Url = "Url";
            RotatorObj.SlideWidth = "600px";
            RotatorObj.SlideHeight = "350px";
            RotatorObj.ShowPlayButton = true;

            //Passing Rotator properties using the ViewData

            ViewData["RotatorModel"] = RotatorObj;

            return View();
        }
    }
}

{% endhighlight %}

Binding the Rotator properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

   @{
       Html.EJ().Rotator("sliderContent", (Syncfusion.JavaScript.Models.RotatorProperties)ViewData["RotatorModel"]).Render();
 }

{% endhighlight %}
