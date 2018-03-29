---
layout: post
title: How To | NavigationDrawer | ASP.NET MVC | Syncfusion
description: How To
platform: ejmvc
control: NavigationDrawer
documentation: ug
---
# How To

## Render NavigationDrawer from Code behind

NavigationDrawer can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side

The following code illustrates the initialization of NavigationDrawer properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (NavigationDrawer) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class NavigationController: Controller
    {
        public ActionResult NavigationDrawer()
        {

            //Initializing the NavigationDrawer model

            NavigationDrawerProperties NavigationObj = new NavigationDrawerProperties();

            //Initializing the NavigationDrawer content template other properties

             NavigationObj.ContentTemplate = new MvcTemplate<NavigationDrawerProperties>
            {
                RazorViewTemplate = (data) =>
                {
                    return "<div id='listview'><ul><li data-ej-text='Home'></li><li data-ej-text='Profile'></li><li data-ej-text='Photos'></li><li data-ej-text='Location'></li></ul></div>";
                }
            };

            NavigationObj.Width = 300;
            NavigationObj.TargetId = "target";

            //Passing NavigationDrawer properties using the ViewData

            ViewData["NavigationModel"] = NavigationObj;

            return View();
        }
    }
}

{% endhighlight %}

Binding the NavigationDrawer properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

<div class="navigation">

    <div id="target" class="drawericon e-icon"> Drawer</div>

</div>

@{
    Html.EJ().NavigationDrawer("navigationPane", (Syncfusion.JavaScript.Models.NavigationDrawerProperties)ViewData["NavigationModel"]).Render();
}

<script>

//render listview
    $(function () {
        $("#listview").ejListView();
    });

</script>

<style>

     .drawericon {
            background-position: center center;
            background-repeat: no-repeat;
            height: 45px;
            width: 32px;
            background-size: 100% 100%;
            padding-right: 10px;
        }

        .drawer icon:before {
            content: "\e76b";
            font-size: 24px;
            height: 26px;
            line-height: 24px;
        }

         body {
        background: none repeat scroll 0 0 #ece9d8;
        }
</style>

{% endhighlight %}