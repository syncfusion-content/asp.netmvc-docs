---
layout: post
title: Data binding | AutoComplete | ASP.NET MVC | Syncfusion
description: Data binding
platform: aspnetmvc
control: AutoComplete
documentation: ug
---

# Data Binding

In order to render the AutoComplete control, the data needs to be bound to it in a proper way. The below sections explains about how to bind either the local or remote data to the AutoComplete widget.

## Fields

The AutoComplete widget has an `AutocompleteFields` property (object) which holds the properties to map with `Datasource` fields. For example, the field object has a `Text` property which is necessary to map with specific field in the `Datasource` to render the suggestion items in the AutoComplete widget.

The field object contains the following properties.

* Text

* Key

* GroupBy

* HtmlAttributes



## Local data

AutoComplete provides extensive data binding support to populate AutoComplete items. To achieve this, you need to map the corresponding fields with the column names in the Datasource. 


In the Model page, define the Class name as Countries with Name and Index field property.

In the Controller, create a list of “Countries” class and add the data as below.

In the View page, add the Autocomplete helper and bind the data. Here the Name and Index fields are mapped with `Text` and `Key` properties of the field object respectively.

{% tabs %}

{% highlight c# %}

//define model class with the corresponding property

public class Countries
    {
        public string Name { get; set; }
        public string Index { get; set; }
    }

//specify desired datasource data by using the model class properties

public partial class AutocompleteController : Controller
{
    public ActionResult Index()
       {
            List<Countries> countries = new List<Countries>();
            countries.Add(new Countries { Name = "Austria", Index = "C1" });
            countries.Add(new Countries { Name = "Australia", Index = "C2" });
            countries.Add(new Countries { Name = "Antarctica", Index = "C3" });
            countries.Add(new Countries { Name = "Bangladesh", Index = "C4" });
            countries.Add(new Countries { Name = "Belgium", Index = "C5" });
            countries.Add(new Countries { Name = "Brazil", Index = "C6" });
            countries.Add(new Countries { Name = "Canada", Index = "C7" });
            countries.Add(new Countries { Name = "China", Index = "C8" });
            countries.Add(new Countries { Name = "Cuba", Index = "C9" });
            countries.Add(new Countries { Name = "Denmark", Index = "C10" });
            countries.Add(new Countries { Name = "Dominica", Index = "C11" });
            countries.Add(new Countries { Name = "Europe", Index = "C12" });
            countries.Add(new Countries { Name = "Egypt", Index = "C13" });
            countries.Add(new Countries { Name = "England", Index = "C14" });
            countries.Add(new Countries { Name = "India", Index = "C15" });
            countries.Add(new Countries { Name = "Indonesia", Index = "C16" });
            ViewBag.datasource = countries;
            return View();
        }
}


{% endhighlight %}

{% highlight razor %}

// In the View page, configure Autocomplete with binding corresponding data
    
@{
        Html.EJ()
            .Autocomplete("autocomplete")
            .Datasource((IEnumerable<Countries>)ViewBag.datasource)
            .AutocompleteFields(f => f.Text("Name").Key("Index"))
            .Width("205")
            .Render();
}

{% endhighlight %}
 {% endtabs %}


![AutoComplete-LocalData](data-binding_images\data-binding_img1.png)


## Remote data

We can bind the data for the Autocomplete from any server that is located as a remote web service. By using `Query` options, you can pass the query string to filter the data that helps to avoid rendering the excessive data. 

N> Use [ejQuery](http://help.syncfusion.com/js/api/ejquery) to set the `Query` property.

Here the ContactName and SupplierID fields are mapped with Text and Key properties respectively, of the field object.


{% highlight razor %}

@{
    Html.EJ()
        .Autocomplete("autocomplete")
        .Datasource(d => d.URL("http://mvc.syncfusion.com/Services/").Offline(false))
        .Query("ej.Query().from('Suppliers').select('SupplierID', 'ContactName')")
        .AutocompleteFields(f => f.Text("ContactName").Key("SupplierID"))
        .Width("205")
        .Render();
}


{% endhighlight %}



![AutoComplete-OData](data-binding_images\data-binding_img2.png)


### Handling errors

In remote binding, the server might not return data sometimes due to various reasons. In such cases we need to handle the error properly. We can handle this using the “[ActionFailure](http://help.syncfusion.com/js/api/ejautocomplete)” event.

{% highlight razor %}

@{
    Html.EJ()
        .Autocomplete("autocomplete")
        .Datasource(d => d.URL("http://mvc.syncfusion.com/Services/").Offline(false))
        .Query("ej.Query().from('Suppliers').select('SupplierID', 'ContactName')")
        .AutocompleteFields(f => f.Text("ContactName").Key("SupplierID"))
        .Width("205")
        .ClientSideEvents(evt => evt.ActionFailure("onRequestFailure "))
        .Render();
}
    
<script>
    function onRequestFailure(args) {
        //Error handler
    }
</script>


{% endhighlight %}







