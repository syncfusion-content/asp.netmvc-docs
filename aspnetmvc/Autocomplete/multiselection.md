---
layout: post
title: Multiselection | AutoComplete | ASP.NET MVC | Syncfusion 
description: Multiselection
platform: aspnetmvc
control: AutoComplete
documentation: ug
---

# MultiSelection

The AutoComplete widget helps you to select multiple values from the suggestion list using the `MultiSelectMode` property. 

There are two types of multi-selection mode.

1. VisualMode – Selection values are displayed in separate box with close button.

2. Delimiter – Selection values are separated using the delimiter character which can be specified using `DelimiterChar` property.

In the Model page, define the Class name with Textfield property.

In the Controller, create a list of “Cars” class and add the data.

In the View page, add the Autocomplete helper and bind the data as shown below.

{% tabs %}
{% highlight c# %}

//define model class with the corresponding property

public class Cars 
{
    public string Text { get; set; }
}

//specify desired datasource data by using the model class properties

public partial class AutocompleteController : Controller
    {
        public ActionResult Index()
            {
                List<Cars> cars = new List<Cars>();
                cars.Add(new Cars { Text = "Audi S6" });
                cars.Add(new Cars { Text = "Austin-Healey" });
                cars.Add(new Cars { Text = "Alfa Romeo" });
                cars.Add(new Cars { Text = "Aston Martin" });
                cars.Add(new Cars { Text = "BMW 7" });
                cars.Add(new Cars { Text = "Bentley Mulsanne" });
                cars.Add(new Cars { Text = "Bugatti Veyron" });
                cars.Add(new Cars { Text = "Chevrolet Camaro" });
                cars.Add(new Cars { Text = "Cadillac" });
                cars.Add(new Cars { Text = "Duesenberg J" });
                cars.Add(new Cars { Text = "Dodge Sprinter" });
                cars.Add(new Cars { Text = "Elantra" });
                cars.Add(new Cars { Text = "Excavator" });
                cars.Add(new Cars { Text = "Ford Boss 302" });
                cars.Add(new Cars { Text = "Ferrari 360" });
                cars.Add(new Cars { Text = "Ford Thunderbird" });
                cars.Add(new Cars { Text = "GAZ Siber" });
                ViewBag.datasource = cars;
                return View();
            }
    }



{% endhighlight %}

{% highlight razor %}

// In the View page, configure Autocomplete with binding corresponding data and specify MultiSelectMode property
        
@{
    Html.EJ()
        .Autocomplete("autocomplete")
        .Datasource((IEnumerable<Cars>)ViewBag.datasource)
        .AutocompleteFields(f => f.Text("Text")
        .Width("205")
        .MultiSelectMode(MultiSelectModeTypes.VisualMode)
        .Render();
}


{% endhighlight %}
{% endtabs %}


![AutoComplete-Multiselection](multiselection_images\multiselection_img1.png)











