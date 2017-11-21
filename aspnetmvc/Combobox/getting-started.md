---
layout: post
title: Getting started in ComboBox control for Syncfusion ASP.NET MVC
description: Getting started
platform: mvc
control: ComboBox
documentation: ug
keywords: allowCustom, ComboBox, dataSource, popupHeight, popupWidth
---

# Getting Started

This section explains how to create a simple **ComboBox** component and configure its available functionalities.

1.Create an MVC Project and add necessary assemblies, scripts and CSS files given in [MVC-Getting Started](http://help.syncfusion.com/aspnetmvc/getting-started#manual-integration-of-syncfusion-mvc-components-into-newexisting-mvc-applications) Documentation.

2.Add ComboBox control using the helper from EJ namespace.



## Initialize the ComboBox

The ComboBox can be initialized as

{%tabs%}

{% highlight html %}

    <div class="frame">
        <div class="control">
            @{
                Html.EJ()
                    .ComboBox("select")
                    .Width("100%")
                    .Datasource((IEnumerable<Flowers>)ViewBag.datasource)
                    .ComboBoxFields(f=>f.Text("text"))
                    .Placeholder("Select")
                    .Render();
            }
        </div>
    </div>

{% endhighlight %}

{% highlight c# %}

public class Flowers
    {
        public string text { get; set; }
        public static List<Flowers> GetFlowers()
        {
            List<Flowers> flower = new List<Flowers>();
            flower.Add(new Flowers { text = "Anemone Galilee" });
            flower.Add(new Flowers { text = "Allium drumstick" });
            flower.Add(new Flowers { text = "Artichoke thistle" });
            flower.Add(new Flowers { text = "Boronia" });
            flower.Add(new Flowers { text = "Bouvardia" });
            flower.Add(new Flowers { text = "Blue lace flower" });
            flower.Add(new Flowers { text = "Bird of paradise" });
            flower.Add(new Flowers { text = "Cone flower" });
            flower.Add(new Flowers { text = "Cosmos" });
            flower.Add(new Flowers { text = "Calla lily white" });
            flower.Add(new Flowers { text = "Common Yarrow" });
            return flower;
        }
        public ActionResult Default()
        {
            ViewBag.datasource = GetFlowers();
            return View();
        }
    }

{% endhighlight %}

{%endtabs%}

## Binding data source

After initializing, populate the ComboBox with data using the **dataSource** property.
Here, an array of string values is passed to the ComboBox component.


{% highlight html %}

    <div class="frame">
        <div class="control">
            @{
                string[] datasource = new string[] { "Badminton", "Cricket", "Football", "Golf", "Tennis" };
                Html.EJ()
                    .ComboBox("select")
                    .Width("100%")
                    .Datasource(datasource)
                    .Placeholder("Select a game")
                    .Render();
            }
        </div>
    </div>

{% endhighlight %}


## Custom values

The ComboBox allows the user to give input as custom value which is not required to present in predefined
set of values. By default, this support is enabled by **allowCustom**
 property. In this case, both text field and value field considered as same.
The custom value will be sent to post back handler when a form is about to be submitted.

{% tabs %}

{% highlight html %}

    <div class="frame">
        <div class="control">
            @{
                Html.EJ()
                    .ComboBox("select")
                    .Width("100%")
                    .Datasource((IEnumerable<Flowers>)ViewBag.datasource)
                    .AllowCustom(true)
                    .ComboBoxFields(f=>f.Text("text").Value("id"))
                    .Placeholder("Select")
                    .Render();
            }
        </div>
    </div>

{% endhighlight %}

{% highlight c# %}

public class Flowers
    {
        public string text { get; set; }
        public int id { get; set; }
        public static List<Flowers> GetFlowers()
        {
            List<Flowers> flower = new List<Flowers>();
            flower.Add(new Flowers { text = "Anemone Galilee", id=0 });
            flower.Add(new Flowers { text = "Allium drumstick", id=1 });
            flower.Add(new Flowers { text = "Artichoke thistle" id=2 });
            flower.Add(new Flowers { text = "Boronia" id=3 });
            flower.Add(new Flowers { text = "Bouvardia" id=4 });
            flower.Add(new Flowers { text = "Blue lace flower" id=5 });
            flower.Add(new Flowers { text = "Bird of paradise" id=6 });
            flower.Add(new Flowers { text = "Cone flower" id=7 });
            flower.Add(new Flowers { text = "Cosmos" id=8 });
            flower.Add(new Flowers { text = "Calla lily white" id=9 });
            flower.Add(new Flowers { text = "Common Yarrow" id=10 });
            return flower;
        }
        public ActionResult Default()
        {
            ViewBag.datasource = GetFlowers();
            return View();
        }
    }

{% endhighlight %}

{%endtabs%}

Output for allowCustom combobox control is as follows.


![](Combobox_getting_started_images/Combobox_data_binding_img1.png) 


## Configure the popup list

By default, the width of the popup list automatically adjusts according to the ComboBox input element's width, and the height of the popup list has '300px'.

The height and width of the popup list can also be customized using the
**popupHeight**
&nbsp;and **popupWidth** properties
respectively.

In the following sample, popup list's width and height are configured.

{% tabs  %}

{% highlight html %}

    <div class="frame">
        <div class="control">
            @{
                Html.EJ()
                    .ComboBox("select")
                    .Width("100%")
                    .Datasource((IEnumerable<Flowers>)ViewBag.datasource)
                    .PopupHeight("200px")
                    .PopupWidth("200px")
                    .Placeholder("Select")
                    .Render();
            }
        </div>
    </div>

{% endhighlight %}

{% highlight c# %}

public class Flowers
    {
        public string text { get; set; }
        public static List<Flowers> GetFlowers()
        {
            List<Flowers> flower = new List<Flowers>();
            flower.Add(new Flowers { text = "Anemone Galilee" });
            flower.Add(new Flowers { text = "Allium drumstick" });
            flower.Add(new Flowers { text = "Artichoke thistle" });
            flower.Add(new Flowers { text = "Boronia" });
            flower.Add(new Flowers { text = "Bouvardia" });
            flower.Add(new Flowers { text = "Blue lace flower" });
            flower.Add(new Flowers { text = "Bird of paradise" });
            flower.Add(new Flowers { text = "Cone flower" });
            flower.Add(new Flowers { text = "Cosmos" });
            flower.Add(new Flowers { text = "Calla lily white" });
            flower.Add(new Flowers { text = "Common Yarrow" });
            return flower;
        }
        public ActionResult Default()
        {
            ViewBag.datasource = GetFlowers();
            return View();
        }
    }

{% endhighlight %}


{% endtabs %}