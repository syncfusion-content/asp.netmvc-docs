---
layout: post
title: Grouping in ComboBox control for Syncfusion ASP.NET MVC
description: Grouping support to ComboBox control for Syncfusion ASP.NET MVC
platform: mvc
control: ComboBox
documentation: ug
keywords: groupBy, ComboBox, groupTemplate
---

# Grouping

The ComboBox supports wrapping nested elements into a group based on different categories. The category
of each list item can be mapped through the **groupBy** &nbsp;field in
the data table. The group header is displayed both as inline and fixed headers. The fixed group header content
is updated dynamically on scrolling the popup list with its category value.

In the following sample, vegetables are grouped according on its category using `groupBy` field.

{% tab %}

{% highlight html%}

<div class="frame">
        <div class="control">
            @{
                Html.EJ()
                    .ComboBox("groupingCountry")
                    .Datasource((IEnumerable<Countries>)ViewBag.datasource)
                    .Width("100%")
                    .ComboBoxFields(fields => fields.GroupBy("category").Text("text"))
                    .Placeholder("Select a country")
                    .Render();
            }
        </div>
    </div>

{% endhighlight%}

{% highliht c# %}

        public string text { get; set; }
        public string category { get; set; }
        public static List<Countries> GetCountries()
        {
            List<Countries> country = new List<Countries>();
            country.Add(new Countries { text = "Austria", category = "A" });
            country.Add(new Countries { text = "Australia", category = "A" });
            country.Add(new Countries { text = "Antarctica", category = "A" });
            country.Add(new Countries { text = "Bangladesh", category = "B" });
            country.Add(new Countries { text = "Brazil", category = "B" });
            country.Add(new Countries { text = "Canada", category = "C" });
            country.Add(new Countries { text = "Cuba", category = "C" });
            country.Add(new Countries { text = "Denmark", category = "D" });
            country.Add(new Countries { text = "Dominica", category = "D" });
            return country;
        }
    }
}

{% endhighlight %}

{% endtab %}

Output for grouping combobox control is as follows.


![](Combobox_grouping_images/grouping.png)


## Customization

The grouping header is also provided with customization option. This allows custom designing using the `groupTemplate` property for both inline and fixed headers as referred here:
**Group Template support to ComboBox**
