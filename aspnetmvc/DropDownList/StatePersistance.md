---
layout: post
title: State Persistance with DropDownList control for Syncfusion ASP.NET MVC
description: State Persistence support to DropDownList control for Syncfusion ASP.NET MVC
platform: MVC
control: DropDownList
documentation: ug
---

# State Persistence

DropDownList stores its model is local storage by defining the property EnablePersistence).
You can sustain the below given functionalities in DropDownList by enabling persistence property,

* Selected items value in the textbox 
* Item’s selection state in the popup list 

Control model will be stored in local storage / cookies of browser before page refreshes and reinitialized with the restored model after refresh.
The following properties are not included while maintaining DropDownList’s state in local storage to keep localStorage compact.

* Fields
* Data source
* Query 

{% tabs %}

	{% highlight html %}
       
        @model MVCApplication.Controllers.HomeController
        <form id="form1">
            @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).ShowCheckbox(true).Width("300px").EnablePersistence(true)
            <input type="submit" value="Get Value" />
        </form> 
		
	{% endhighlight %}
    
    {% highlight c# %}
        public ActionResult Index()
        {
            List<Data> DropDownData = new List<Data>();
            DropDownData.Add(new Data { Value = "item1", Text = "ListItem 1" });
            DropDownData.Add(new Data { Value = "item2", Text = "ListItem 2" });
            DropDownData.Add(new Data { Value = "item3", Text = "ListItem 3" });
            DropDownData.Add(new Data { Value = "item4", Text = "ListItem 4" });
            DropDownData.Add(new Data { Value = "item5", Text = "ListItem 5" });
            ViewData["DropDownSource"] = DropDownData;
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}

## Accessing currently stored state

Persisted state can be accessed through local storage using corresponding key name. Key name formation would be in below order. It is combination of plugin name and control id.

{% highlight js %}

	// DropDownList state as string
	var dropdownlistStateString = window.localStorage.ejDropDownListdropdown;

	//DropDownList state as object
	var dropdownlistStateObject = JSON.parse(window.localStorage.ejDropDownListdropdown);

{% endhighlight %}

N> In the above example, ‘ejDropDownList’ is plugin name and ‘dropdown’ is control id.           
