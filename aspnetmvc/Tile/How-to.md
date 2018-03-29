---
layout: post
title: How to
description: How to
platform: ejmvc
control: TileView
documentation: ug
---
# How to

## Render TileView from Code behind

TileView can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side

The following code illustrates the initialization of TileView properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (TileView) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class TileController: Controller
    {
        public ActionResult TileFeatures()
        {

             //Initializing the TileView model

            TileProperties tileObj = new TileProperties();

            //Initializing the other properties

            tileObj.TileSize = Syncfusion.JavaScript.TileSize.Medium;
            tileObj.ImageUrl = "http://js.syncfusion.com/ug/web/content/tile/alerts.png";
            tileObj.Text = "Alerts";

            //Passing TileView properties using the ViewData

             ViewData["TileModel"] = tileObj;

            return View();
        }
    }
}

{% endhighlight %}

Binding the TileView properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().Tile("Tile1", (Syncfusion.JavaScript.Models.TileProperties)ViewData["TileModel"]).Render();
}

{% endhighlight %}
