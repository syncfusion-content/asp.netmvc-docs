---
layout: post
title: How to
description: How to
platform: ejmvc
control: RadialMenu
documentation: ug
---
# How to

## Render RadialMenu from Code behind

RadialMenu can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of RadialMenu properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (RadialMenu) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class RadialmenuController: Controller
    {
        public ActionResult RadialmenuFeatures()
        {

                   //Initializing the RadialMenu model

                  RadialMenuProperties RadialmenuObj = new RadialMenuProperties();

                   //Initializing the items and other properties

                    List<RadialMenuBaseItem> obj = new List<RadialMenuBaseItem> ();
                    obj.Add(new RadialMenuBaseItem(){ Text = "Copy" , ImageURL = "http://mvc.syncfusion.com/demos/web/Images/RadialMenu/copy.png"});
                    obj.Add(new RadialMenuBaseItem() { Text = "Paste", ImageURL = "http://mvc.syncfusion.com/demos/web/Images/RadialMenu/paste.png" });
                    obj.Add(new RadialMenuBaseItem() { Text = "Undo", ImageURL = "http://mvc.syncfusion.com/demos/web/Images/RadialMenu/undo.png" });
                    obj.Add(new RadialMenuBaseItem() { Text = "Redo", ImageURL = "http://mvc.syncfusion.com/demos/web/Images/RadialMenu/redo.png" });


                   RadialmenuObj.Items = obj;

                   RadialmenuObj.ImageClass = "e-radial";
                   RadialmenuObj.TargetElementId = "radialtarget1";

                   //Passing Radialmenu properties using the ViewData

                   ViewData["RadialMenuModel"] = RadialmenuObj;

            return View();
        }
    }

{% endhighlight %}

Binding the RadialMenu properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

  <div id="radialtarget11" class="content-container-fluid">
    
  </div>

@{
    Html.EJ().RadialMenu("RadialMenu1", (Syncfusion.JavaScript.Models.RadialMenuProperties)ViewData["RadialMenuModel"]).Render();
 }

<style type="text/css" class="cssStyles">

    .e-radialmenu .e-radial {

        background-image: url("http://mvc.syncfusion.com/demos/web/Images/RadialMenu/settings.png");
    }

    .e-radialmenu.e-displaynone {

        display: block;

    }
</style>

{% endhighlight %}