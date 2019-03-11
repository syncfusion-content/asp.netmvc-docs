---
layout: post
title: CheckBox with DropDownList widget for Syncfusion ASP.NET MVC
description: Describes about Checkbox functionalities in DropDownList control for Syncfusion ASP.NET MVC
platform: ejmvc
control: DropDownList
documentation: ug
keywords: Checkbox, dropdown, Selection Modes, Visual Mode, Delimiter

---

# Checkbox

DropDownList displays checkboxes to the left of each item when you set <b>ShowCheckbox</b> property to true. It allows you to select more than one item at a time from DropDownList. Popup list stays open until the user finishes selection. When you click on an item’s text or checkbox then the checkbox checked status get change.

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).ShowCheckbox(true)
		
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

![Checkbox](Checkbox_images/Checkbox_img1.jpeg)

> if you want to showcase the DropDownList with default checked items on data binding, specify Selected field with Boolean values.

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value").Selected("Selected")).ShowCheckbox(true).Width("300px")
		
	{% endhighlight %}
    
    {% highlight c# %}
        public ActionResult Index()
        {
            List<Data> DropDownData = new List<Data>();
            DropDownData.Add(new Data { Value = "item1", Text = "ListItem 1", Selected=true });
            DropDownData.Add(new Data { Value = "item2", Text = "ListItem 2", Selected=false });
            DropDownData.Add(new Data { Value = "item3", Text = "ListItem 3", Selected=true });
            DropDownData.Add(new Data { Value = "item4", Text = "ListItem 4", Selected=false });
            DropDownData.Add(new Data { Value = "item5", Text = "ListItem 5", Selected=false });
            ViewData["DropDownSource"] = DropDownData;
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
            public bool Selected { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}

![Checkbox](Checkbox_images/Checkbox_img2.jpeg)

## Selection Modes

The MultiSelectMode property enables you to make multiple selections in the following two ways:

* Delimiter 
* Visual Mode

I> “MultiSelectMode” property accepts **Syncfusion.JavaScript.MultiSelectModeTypes** enum value.

### Delimiter

Each checked item’s text is appended to the textbox with delimiter “,” by default. This is enabled by assigning **Syncfusion.JavaScript.MultiSelectModeTypes.Delimiter** (enum) value to MultiSelectMode property. You can customize the delimiter option by using DelimiterChar property.

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).ShowCheckbox(true).MultiSelectMode(MultiSelectModeTypes.Delimiter).DelimiterChar("-").Width("300px")
		
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

![Delimiter](Checkbox_images/Checkbox_img3.jpeg)

### Visual Mode

When you enable this option in DropDownList control, each checked item’s text is appended to the text box in a box model layout. This is enabled by assigning **Syncfusion.JavaScript.MultiSelectModeTypes.VisualMode** (enum) value to MultiSelectMode property.

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).ShowCheckbox(true).Width("300px").MultiSelectMode(MultiSelectModeTypes.VisualMode)
		
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

![Visual](Checkbox_images/Checkbox_img4.jpeg)

## Select multiple values from controller

To pass selected values from controller, pass selected items using `ViewBag`, and assign this to the `Value` property of DropDownList. Refer to the following code.

{% highlight html %}

     @model MVCApplication.Controllers.HomeController
     
     @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).Value(ViewBag.Selected).ShowCheckbox(true)

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
            ViewBag.Selected = "item1,item2";
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
        }
    
{% endhighlight %}

To pass multiple selected items from View to Controller, use ajax post to send selected items through change event of DropDownList. Refer to the following code

{% highlight html %}

     @model MVCApplication.Controllers.HomeController
     
    @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).ClientSideEvents(e=>e.Change("Changed")).ShowCheckbox(true).Value(ViewBag.Selected)

{% endhighlight %}

{% highlight js %}

   function Changed(args) {
         $.ajax({
                type: "POST",
                url: '@Url.Action("Update")',
                data: '{value: ' + JSON.stringify(args.model.value) + '}',
                dataType: "json",
                contentType: "application/json; charset=utf-8",
                success: function (e) {
                    console.log(e.result);
                },
                error: function () {
                    alert("Error while sending data");
                }
            });
    }

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
            ViewBag.Selected = "item1,item2";
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
        }

        [HttpPost]
        public ActionResult Update(string Value)
        {
            var selected = Value;
            return Json(new { result = Value, JsonRequestBehavior.AllowGet });
        }
    
{% endhighlight %}

 Refer [HowTo](https://help.syncfusion.com/aspnetmvc/dropdownlist/howto#add-check-all-option-in-popup-list) section to add check all option in popup list 