---
layout: post
title: Templates | AutoComplete | ASP.NET MVC | Syncfusion
description: Templates
platform: aspnetmvc
control: AutoComplete
documentation: ug
---

# Templates

The suggestion list can be customized based on different needs using templates. The desired templates can be defined using the `Template` property.

In the Model page, define the Class name as Mobiles with Name and Quantity field property.

In the Controller page, to create a List of Mobiles class and add the data.

In the View page, add Autocomplete helper and map the Local data list to corresponding `DataSource`.

{% tabs %}
{% highlight c# %}


//define model class with the corresponding property

public class Mobiles
    {
        public string Name { get; set; }
        public int Quantity { get; set; }
    }

//specify desired datasource data by using the model class properties

public partial class AutocompleteController : Controller
    {
        public ActionResult Index()
            {
                List<Mobiles> mobiles = new List<Mobiles>();
                mobiles.Add(new Mobiles { Name = "Galaxy Grand 2", Quantity = 3 });
                mobiles.Add(new Mobiles { Name = "Galaxy S6", Quantity = 5 });
                mobiles.Add(new Mobiles { Name = "IPhone 6S", Quantity = 8 });
                mobiles.Add(new Mobiles { Name = "Ipod Mini", Quantity = 3 });
                ViewBag.datasource = mobiles;
                return View();
            }
    }



{% endhighlight %}

{% highlight razor %}

// In the View page, configure Autocomplete with binding corresponding data and specify template option

@{
    Html.EJ()
        .Autocomplete("autocomplete")
        .Datasource((IEnumerable<Mobiles>)ViewBag.datasource)
        .AutocompleteFields(f => f.Text("Name"))
        .Template("<div><div class='product-text'>${Name}</div> <span class='product-quantity' style='font-size:10px'> Quantity : ${Quantity}</span></div>")
        .Render();
}


{% endhighlight %}
 {% endtabs %}

![AutoComplete-Template](templates_images\templates_img1.png)





