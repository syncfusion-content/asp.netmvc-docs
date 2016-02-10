---
layout: post
title: Grouping | AutoComplete | ASP.NET MVC | Syncfusion
description: Grouping
platform: aspnetmvc
control: AutoComplete
documentation: ug
---

# Grouping

The suggestion list items can be grouped by providing a header for each set of items. The grouping will be defined based on the `GroupBy` property in fields object.


In the Model page, define the Class name as Countries with `Text` and `Category` field property.

In the Controller page, create a List of “Countries” class and add the data.

In the View page, add the Autocomplete helper and bind the data.

{% tabs %}
{% highlight c# %}


//define model class with the corresponding property

public class Countries
    {
        public string Text { get; set; }
        public string Category { get; set; }
    }

//specify desired datasource data by using the model class properties

public partial class AutocompleteController : Controller
    {
        public ActionResult Index()
            {
                List<Countries> countries = new List<Countries>();
                countries.Add(new Countries { Text = "Austria", Category = "A" });
                countries.Add(new Countries { Text = "Australia", Category = "A" });
                countries.Add(new Countries { Text = "Bangladesh", Category = "B" });
                countries.Add(new Countries { Text = "Brazil", Category = "B" });
                countries.Add(new Countries { Text = "Canada", Category = "C" });
                countries.Add(new Countries { Text = "Cuba", Category = "C" });
                countries.Add(new Countries { Text = "Denmark", Category = "D" });
                countries.Add(new Countries { Text = "Dominica", Category = "D" });
                countries.Add(new Countries { Text = "Europe", Category = "E" });
                countries.Add(new Countries { Text = "Egypt", Category = "E" });
                countries.Add(new Countries { Text = "India", Category = "I" });
                countries.Add(new Countries { Text = "Indonesia", Category = "I" });
                countries.Add(new Countries { Text = "France", Category = "F" });
                countries.Add(new Countries { Text = "Finland", Category = "F" });
                countries.Add(new Countries { Text = "Germany", Category = "G" });
                countries.Add(new Countries { Text = "Greece", Category = "G" });
                countries.Add(new Countries { Text = "Japan", Category = "J" });
                countries.Add(new Countries { Text = "Jordan", Category = "J" });
                countries.Add(new Countries { Text = "Madagascar", Category = "M" });
                countries.Add(new Countries { Text = "Midway Islands", Category = "M" });
                countries.Add(new Countries { Text = "Nepal", Category = "N" });
                countries.Add(new Countries { Text = "Netherlands", Category = "N" });
                countries.Add(new Countries { Text = "Qatar", Category = "Q" });
                countries.Add(new Countries { Text = "Romania", Category = "R" });
                countries.Add(new Countries { Text = "Scotland", Category = "S" });
                countries.Add(new Countries { Text = "Tibet", Category = "T" });
                countries.Add(new Countries { Text = "Zambia", Category = "Z" });
                countries.Add(new Countries { Text = "Zimbabwe", Category = "Z" });
                ViewBag.datasource = countries;
                return View();
            }
        }



{% endhighlight %}

{% highlight razor %}

// In the View page, configure Autocomplete with binding corresponding data and group by the datas

@{
    Html.EJ()
        .Autocomplete("autocomplete")
        .Datasource((IEnumerable<Countries>)ViewBag.datasource)
        .AutocompleteFields(f => f.Text("Text").GroupBy("Category"))
        .FilterType(FilterOperatorType.Contains)
        .Render();
}


{% endhighlight %}
{% endtabs %}

![AutoComplete-Grouping](grouping_images\grouping_img1.png)



