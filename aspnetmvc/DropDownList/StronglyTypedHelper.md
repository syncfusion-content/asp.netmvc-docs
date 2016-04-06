---
layout: post
title: How to - DropDownList control for Syncfusion ASP.NET MVC
description: How To Section in DropDownList control for Syncfusion ASP.NET MVC
platform: js
control: DropDownList
documentation: ug
---

# Strongly Typed HTML Helper
The DropDownList control supports strongly typed HTML helpers which uses lambda expression to refer models or view models passed to a view template. These helpers allow you to define the value of the DropDownListFor from the model. The following steps explain how to use the strongly typed helpers to create DropDownListFor.
Add a class named *"*DropDownListModel" in the Models folder and replace the code with the following code:

{% tabs %}

{% highlight c# %}

    public class DropDownListModel
    {
        [Display(Name = "Drop Down")]
        public List<DropDownValue> DropData { get; set; }
    }

    public class DropDownValue
    {
        public string Text { get; set; }
        public string Value { get; set; }

    }

{% endhighlight %}

{% endtabs %}

In the controller, pass the model to the View.

{% tabs %}

{% highlight c# %}
    
    using MvcApplication.Models;
    using Syncfusion.JavaScript.Models;
        public ActionResult DropdownlistFeatures()
        {
            DropDownListModel model = new DropDownListModel();
            BindingData();
            return View(model);
         }
        public void BindingData()
        {
            List<DropDownValue> data = new List<DropDownValue>() { };
            data.Add(new DropDownValue() { Value = "item1", Text = "List Item 1" });
            data.Add(new DropDownValue() { Value = "item2", Text = "List Item 2" });
            data.Add(new DropDownValue() { Value = "item3", Text = "List Item 3" });
            data.Add(new DropDownValue() { Value = "item4", Text = "List Item 4" });
            data.Add(new DropDownValue() { Value = "item5", Text = "List Item 5" });
            DropDownListProperties ddl = new DropDownListProperties();
            ddl.DataSource = data;
            DropDownListFields ddf = new DropDownListFields();
            ddf.Text = "Text";
            ddf.Value = "Value";
            ddl.DropDownListFields = ddf;
            ViewData["properties"] = ddl;
        }

{% endhighlight %}

{% endtabs %}

In View, invoke the strongly typed DropDownListFor helper with the lambda expression to set the default value.

{% tabs %}

{% highlight razor %}
    
    @model MvcApplication.Models. DropDownListModel

    @Html.EJ().DropDownListFor(Model => Model.DropData,(Syncfusion.JavaScript.Models.DropDownListProperties)ViewData["properties"])

{% endhighlight %}

{% endtabs %}

![](StronglyTypedHelper_images/StronglyTypedHelper_img1.jpeg)
