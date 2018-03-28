---
layout: post
title: How to
description: How to
platform: ejmvc
control: Autocomplete
documentation: ug
---
# How to

## Render Autocomplete from Code behind

Autocomplete can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of Autocomplete properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (Autocomplete) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class AutocompleteController : Controller
    {
        // GET: Autocomplete
        public ActionResult AutocompleteFeatures()
        {
            //Initializing the Autocomplete model

            AutocompleteProperties AutoObj = new AutocompleteProperties();

            //Initializing the datasource and other properties

            AutoObj.DataSource = "http://js.syncfusion.com/ejServices/wcf/NorthWind.svc/";
            AutoObj.Query = "ej.Query().from('Suppliers').select('SupplierID', 'ContactName')";
            AutoObj.AutocompleteFields.Text = "ContactName";
            AutoObj.AutocompleteFields.Key = "SupplierID";
            AutoObj.Width = "500px";
            AutoObj.ShowPopupButton = true;
            AutoObj.ShowLoadingIcon = true;

            //Passing Autocomplete properties using the ViewData
            ViewData["AutoModel"] = AutoObj;
            return View();
        }
    }
}

{% endhighlight %}

Binding the Autocomplete properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().Autocomplete("searchCustomer",(Syncfusion.JavaScript.Models.AutocompleteProperties)ViewData["AutoModel"]).Render();
}

{% endhighlight %}