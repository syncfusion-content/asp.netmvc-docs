---
layout: post
title: Grouping | ListBox | ASP.NET MVC | Syncfusion
description: Grouping
platform: ejmvc
control: ListBox
documentation: ug
---

# Grouping

ListBox items can be grouped by providing a heading (header) for each set of items. It can be done in two ways.

1. Using span tag

2. Databinding


## Using span tag

The header for each group can be defined using the “span” element”. 

{% highlight razor %}

@Html.EJ().ListBox("listbox").TargetID("countries")

<!--grouped listbox-->
<ul id="countries">
    <!--header-->
    <span>A</span>
    <li>Albania</li>
    <li>Argentina</li>
    <li>Algeria</li>
    <li>Angola</li>
    <li>Afghanistan</li>
    <!--header-->
    <span>B</span>
    <li>Brazil</li>
    <li>Bahrain</li>
    <li>Burma</li>
    <li>Barbados</li>
    <li>Botswana</li>
    <li>Belarus</li>
    <li>Bolivia</li>
</ul>


{% endhighlight %}


![](Grouping_images\Grouping_img1.png)


## Databinding

The grouped ListBox can be also created via databinding which is explained below. The data items can be categorized by using a specific field in the ListBox widget.

{% seealso %} [Data Binding](http://help.syncfusion.com/aspnetmvc/listbox/databinding). {% endseealso %}

The grouping will be defined based on the “GroupBy” Property in fields object.

In the Model page, define a Class with Text field and category field.

In the Controller, create a list of “Countries” class and add the data.

In the View page, add the ListBox helper and bind the data.

{% tabs %}        
{% highlight c# %}

//define model class with the corresponding property

public class Countries
    {
            public string Text { get; set; }
            public string Category { get; set; }        
    }
    
//specify desired datasource data by using the model class properties

public partial class ListBoxController : Controller
        {
            List<Countries> country = new List<Countries>();
            public ActionResult Index()
            {
                country.Add(new Countries { Text = "Bahrain", Category = "B" });
                country.Add(new Countries { Text = "Brazil", Category = "B" });
                country.Add(new Countries { Text = "Argentina", Category = "A" });
                country.Add(new Countries { Text = "Bangladesh", Category = "B" });
                country.Add(new Countries { Text = "Burma", Category = "B" });
                country.Add(new Countries { Text = "Afghanistan", Category = "A" });
                country.Add(new Countries { Text = "Antigua and Barbuda", Category = "A" });
                country.Add(new Countries { Text = "Barbados", Category = "B" });
                country.Add(new Countries { Text = "Botswana", Category = "B" });
                country.Add(new Countries { Text = "Albania", Category = "A" });
                country.Add(new Countries { Text = "Andorra", Category = "A" });
                country.Add(new Countries { Text = "Belarus", Category = "B" });
                country.Add(new Countries { Text = "Bolivia", Category = "B" });
                country.Add(new Countries { Text = "Algeria", Category = "A" });
                country.Add(new Countries { Text = "Angola", Category = "A" });
                ViewBag.datasource = country;
                return View();
            }
        }

{% endhighlight %}

{% highlight razor %}'

@{Html.EJ().ListBox("listbox")
      .Datasource((IEnumerable<Countries>)ViewBag.datasource)
      .ListBoxFields(fields => fields.Text("Text").GroupBy("Category"))
      .Render();}


{% endhighlight %}
{% endtabs %}


 ![](Grouping_images\Grouping_img2.png)



