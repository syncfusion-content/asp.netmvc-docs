---
layout: post
title: How-to
description: How-to section - The frequently used options with GroupButton 
platform: ejmvc
control: GroupButton
documentation: ug
---
# How to?

## Render GroupButton from Code behind

GroupButton can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of GroupButton properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (GroupButton) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class GroupButtonController : Controller
    {
        public class Groupbutton
        {
            public string text { get; set; }
            public string id { get; set; }
        }

        public List<Groupbutton> model = new List<Groupbutton>();

        // GET: GroupButton
        public ActionResult GroupButtonFeatures()
        {
            model.Add(new Groupbutton { text = "Item1" });
            model.Add(new Groupbutton { text = "Item2" });
            model.Add(new Groupbutton { text = "Item3" });

            //Initializing the GroupButton model

            GroupButtonProperties BtnObj = new GroupButtonProperties();

            //Initializing the datasource and other properties
            
            BtnObj.ShowRoundedCorner=true;
            BtnObj.DataSource = model;
            BtnObj.GroupButtonFields.Text = "text";

            //Passing GroupButton properties using the ViewData
            ViewData["BtnModel"] = BtnObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the GroupButton properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().GroupButton("searchCustomer",(Syncfusion.JavaScript.Models.GroupButtonProperties)ViewData["BtnModel"]).Render();
}

{% endhighlight %}
