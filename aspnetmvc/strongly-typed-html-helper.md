---
layout: post
title: Getting Started | ASP.NET MVC | Syncfusion
description: Getting Started
platform: ejmvc
control: Common 
documentation: ug
keywords: Strongly-Typed HTML Helper, NumericTextBox, NumericTextBoxFor
---

# Strongly-Typed HTML Helper

The Syncfusion editor controls supports strongly typed HTML helpers represented by lambda expressions that have model or template passed into the view. The Extension method is used to get a value from the model.

The Strongly-Typed HTML helper (i.e., NumericTextBox) takes lambda as a parameter that tells the helper with element of the model to use in the typed view. 

Strongly typed views are used for rendering specific types of model objects, instead of using the general ViewData structure.

The following list of controls supports Strongly-Typed HTML Helper
•	Autocomplete.
•	Checkbox and Radio Button
•	DatePicker.
•	DateTimePicker
•	DropDownList
•	Mask Edit.
•	Numeric, Currency, and Percentage Textbox.
•	RichTextEditor
•	TimePicker

The following steps explain how to use the strongly typed helpers to create a NumericTextBox

The NumericTextBox control supports strongly typed HTML helpers which uses lambda expression to refer models or view models passed to a view template. These helpers allow you to define the value of the NumericTextBoxFor from the model. 

Add a class named “EditorValue” in the Models folder and replace the code with the following code:

{% highlight html %}

    public class EditorValue
    {
        public int number { set; get; }
        public EditorValue(int num)
        {
            number = num;
        }
        public EditorValue (){}
    }
    
{% endhighlight %}

Create an action method that renders NumericTextBox on the view page, and passes the model to be bound to the view page.

{% highlight C# %}

    using Syncfusion.JavaScript.Models;
    using MVCSampleBrowser.Models;
    public ActionResult EditorFor()
    {
        //Editor For
        EditorProperties editor = new EditorProperties();
        editor.EnableStrictMode = true;
        ViewData["editmodel"] = editor;
        return View(new EditorValue(66));
    }
    
{% endhighlight %}

In View, invoke the strongly typed NumericTextBoxFor helper with the lambda expression to set the default value.

{% highlight Razor %}

    @model MVCSampleBrowser.Models.EditorValue
    @using (Html.BeginForm())
    {
        @Html.EJ().NumericTextBoxFor(model => model.number, (Syncfusion.JavaScript.Models.EditorProperties)ViewData["editmodel"])
        @Html.EJ().Button("btn").Size(ButtonSize.Small).Text("PayBill").Type(ButtonType.Submit)
    }

{% endhighlight %}

![](stronlyTyped_images/img1.jpg)

The following steps explain how to get the values by using the Scaffolding methods in Post back.

1. Create an action method, FormPost that handles the Post request and processes the data. 
In the action method, you can pass the model as the parameter. That model has the NumericTexBox’s value.

{% highlight C# %}

    [HttpPost]
    public ActionResult EditorFor(EditorValue model)
    {
        //Editor For
        EditorProperties editor = new EditorProperties();
        editor.EnableStrictMode = true;
        ViewData["editmodel"] = editor;
        return View(model);
    }

{% endhighlight %}

Upon clicking to the button the Post method will be triggered. In that, the selected value will be obtained as follows.

![](stronlyTyped_images/img2.jpg)

## Client Side Validation

With the client-side validation, the input data is checked as soon as they are submitted, so there is no postback to the server and there is no page refresh.

By default, client-side validation becomes enabled. But it’s can easily enable or disable by the writing of the following app setting code snippet in the web.config file.

{% highlight html %}

    <appSettings>
        <add key="ClientValidationEnabled" value="true" />
        <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    </appSettings>

{% endhighlight %}


N> Can enable client side validation for specific view only by adding Html.EnableClientValidation(true) at the top in view page.

After setting the value as true, refer to the jQuery validation script file in the _Layout page as shown in the following code example.

{% highlight html %}

    <script src="~/Scripts/jquery.validate.min.js"></script>
    <script src="~/Scripts/jquery.validate.unobtrusive.js"></script>
    <script src="~/Scripts/ej/ej.unobtrusive.min.js"></script>

{% endhighlight %}

The jQuery validation plug-in takes advantage of the Data Annotation attributes defined in the model. 

Step 1: Add the below namespace to “EditorValue” model.

{% highlight html %}

    using System.ComponentModel.DataAnnotations;
    
{% endhighlight %}

Data Annotations allow us to decorate model classes with metadata. This metadata describes a set of rules that are used to validate a property. 

We’ll use the following Data Annotation attributes for the Numeric Textbox.
Required – Indicates that the property is a required field.

Step 2: Next, Update the number property of the “EditorValue” class as “Required Field” by adding the following line

{% highlight C# %}

    using System.ComponentModel.DataAnnotations;
    public class EditorValue
    {
        [Required(ErrorMessage = "Numeric Textbox is Required")]
        public int number { set; get; }
        
        public EditorValue(int num)
        {
            number = num;
        }
    }

{% endhighlight %}

Step 3: Modify the view page as follows

{% highlight Razor %}

    @model ComplexBinding.Models.EditorValue       
    @using (Html.BeginForm())
    {
        @Html.ValidationSummary(true)
        @Html.EJ().NumericTextBoxFor(model => model.number, (Syncfusion.JavaScript.Models.EditorProperties)ViewData["editmodel"])
        @Html.ValidationMessageFor(model => model.number)
        @Html.EJ().Button("btn").Size(ButtonSize.Small).Text("PayBill").Type(ButtonType.Submit)
    }
    
{% endhighlight %}

![](stronlyTyped_images/img3.jpg)

## Server Side Validation

In the server-side validation, the page must be submitted via a postback to be validated on the server and if the model data is not valid, then the server sends a response back to the client.

The best way to validate a model by using Data Annotations which has a set of attributes and classes defined in the System.ComponentModel.DataAnnotations assembly.

Step 1: Add the below namespace to “EditorValue” model.

{% highlight html %}

    using System.ComponentModel.DataAnnotations;
    
{% endhighlight %}

Data Annotations allow us to decorate model classes with metadata. This metadata describes a set of rules that are used to validate a property. 

We’ll use the following Data Annotation attributes for the Numeric Textbox.
Required – Indicates that the property is a required field.

Step 2: Next, Update the number property of the “EditorValue” class as “Required Field” by adding the following line

{% highlight C# %}

    using System.ComponentModel.DataAnnotations;
    public class EditorValue
    {
        [Required(ErrorMessage = "Numeric Textbox is Required")]
        public int number { set; get; }
        
        public EditorValue(int num)
        {
            number = num;
        }
    }

{% endhighlight %}

Step 3: Modify the view page as follows

{% highlight Razor %}

    @model ComplexBinding.Models.EditorValue       
    @using (Html.BeginForm())
    {
        @Html.ValidationSummary(true)
        @Html.EJ().NumericTextBoxFor(model => model.number, (Syncfusion.JavaScript.Models.EditorProperties)ViewData["editmodel"])
        @Html.ValidationMessageFor(model => model.number)
        @Html.EJ().Button("btn").Size(ButtonSize.Small).Text("PayBill").Type(ButtonType.Submit)
    }
    
{% endhighlight %}

When you press the “PayBill” button on this page then it will post the data to the server and the code written with in EditorFor action will validate the NumericTextBox value by checking ModelState.IsValid property. If NumericTextBox value is not selected, then ModelState.IsValid will return false and display error message.

![](stronlyTyped_images/img3.jpg)

## Complex Model Binding

The lambda expressions are quite powerful, allowing you to build quite complex edit models and have model binding put everything back together again. A complex view model type such as:

{% highlight C# %}

    public class Person
    {
        public string Name { get; set; }
        public BillingInfo BillingInfo { get; set; }
        public Person(BillingInfo info){
            BillingInfo = info;
        }
        public Person() { }
    }

    public class BillingInfo
    {
        public int BillingNo { get; set; }
        public BillingInfo(int no)
        {
            BillingNo = no;
        }
        public BillingInfo() { }
    }
    
{% endhighlight %}

Create an action method that renders NumericTextbox on the view page, and passes the model to be bound to the view page.

{% highlight C# %}

    using ComplexBinding.Models;
    using Syncfusion.JavaScript.Models;
    public ActionResult Complex()
    {
        //Editor For
        EditorProperties editor = new EditorProperties();
        editor.EnableStrictMode = true;
        ViewData["editmodel"] = editor;
        return View(new Person(new BillingInfo(1121)));
    }        

{% endhighlight %}

In View, invoke the strongly typed NumericTextBoxFor helper with the lambda expression to set the default value.

{% highlight Razor %}

    @model ComplexBinding.Models.Person
    @using (Html.BeginForm())
    {
        @Html.EJ().NumericTextBoxFor(x => x.BillingInfo.BillingNo, (Syncfusion.JavaScript.Models.EditorProperties)ViewData["editmodel"])
        @Html.EJ().Button("btn").Size(ButtonSize.Small).Text("PayBill").Type(ButtonType.Submit)
    }

{% endhighlight %}

![](stronlyTyped_images/img4.jpg)

When the form is submitted, it will perform an Http Post request to the controller. The action with the HttpPost attribute will handle the request.

{% highlight C# %}

    [HttpPost]
    public ActionResult Complex(Person model)
    {
        //Editor For
        EditorProperties editor = new EditorProperties();
        editor.EnableStrictMode = true;
        ViewData["editmodel"] = editor;
        return View(model);
    }

{% endhighlight %}

In code behind, the selected value of NumericTextBox will be obtained as follows

![](stronlyTyped_images/img5.jpg)
