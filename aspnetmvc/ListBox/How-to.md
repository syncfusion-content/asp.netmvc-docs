---
layout: post
title: How to
description: How to
platform: ejmvc
control: ListBox
documentation: ug
---
# How to

## Render ListBox from Code behind

ListBox can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of ListBox properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (Listbox) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class ListBoxController: Controller
    {

        public ActionResult ListBoxFeatures()
        {

             // initialize data
            List<Bikes> bike = new List<Bikes>();
            bike.Add(new Bikes { id = "bk1", text = "Aachen RTR" });
            bike.Add(new Bikes { id = "bk2", text = "CBR 150-R" });
            bike.Add(new Bikes { id = "bk3", text = "CBZ Xtreme" });
            bike.Add(new Bikes { id = "bk4", text = "Discover" });
            bike.Add(new Bikes { id = "bk5", text = "Dazzler" });
            bike.Add(new Bikes { id = "bk6", text = "Flame" });
            bike.Add(new Bikes { id = "bk7", text = "Faze" });
            bike.Add(new Bikes { id = "bk8", text = "FZ-S" });
            bike.Add(new Bikes { id = "bk9", text = "Pulsar" });
            bike.Add(new Bikes { id = "bk10", text = "Shine" });
            bike.Add(new Bikes { id = "bk11", text = "R15" });
            bike.Add(new Bikes { id = "bk12", text = "Unicorn" });

            //Initializing the Listbox model

            ListBoxProperties ListObj = new ListBoxProperties();

            //Initializing the datasource and other properties

            ListObj.DataSource = bike;
            ListObj.ListBoxFields.Text = "text";
            ListObj.ListBoxFields.Value = "id";
            ListObj.AllowMultiSelection = true;

            //Passing Listbox properties using the ViewData

            ViewData["ListModel"] = ListObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the ListBox properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().ListBox("bikeList", (Syncfusion.JavaScript.Models. ListBoxProperties)ViewData["ListModel"]).Render();
}

{% endhighlight %}