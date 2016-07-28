---
layout: post
title: Data binding in DropDownList control for Syncfusion ASP.NET MVC
description: Describes about the data binding in DropDownList control for Syncfusion ASP.NET MVC
platform: MVC
control: DropDownList
documentation: ug
---

# Validations

DropDownList value can be validated in following ways,
1. Using jQuery Validator
2. Client side Validation
3. Server side validation

## Using jQuery Validator
You can validate the DropDownList value on form submission using jQuery Validations, by applying “ValidationRules” and “ValidationMessage” to the DropDownList. 

N> [jquery.validate.min](http://cdn.syncfusion.com/js/assets/external/jquery.validate.min.js) script file should be referred for validation, for more details, refer [here](http://jqueryvalidation.org/documentation).

### Validation Rules

The validation rules help you to verify the selected text by adding validation attributes to the input element. This can be set by using ValidationRules property.

### Validation Messages 

You can set your own custom error message by using ValidationMessage property. To display the error message, specify the corresponding annotation attribute followed by the message to display.

N> jQuery predefined error messages to that annotation attribute will be shown when this property is not defined. The below given example explain this behavior of ‘required’ attribute,

When the DropDownList control is rendered, it creates an input hidden element which is used to store the selected items value. Hence, the validation is performed based on the value stored in this hidden element.

Required field and min value validation is demonstrated in the below given example.

{% tabs %}

{% highlight html %}

     @model MVCApplication.Controllers.HomeController
    <form id="form1">   

        @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).ValidationMessage(vm => vm.AddMessage("required", "* Required").AddMessage("min","Select > 30")).ValidationRules(vr => vr.AddRule("required", true).AddRule("min",30))

        <br /><input type="submit" value="Submit" />

    </form>
                
{% endhighlight %}

{% highlight javascript %}

        $.validator.setDefaults({
            ignore: [],
            errorClass: 'e-validation-error', // to get the error message on jquery validation
            errorPlacement: function (error, element) {
                $(error).insertAfter(element.closest(".e-widget"));
            }
            // any other default options and/or rules
        });
        //If necessary, we can create custom rules as below. here method defined for min
        $.validator.addMethod("min",
            function (value, element, params) {
                if (!/Invalid|NaN/.test(value)) {
                    return parseInt(value) > params;
                }
            }, 'Must be greater than 30.');
				
{% endhighlight %}

{% highlight c# %}
	
    public ActionResult Index()
        {
            List<Data> DropdownData = new List<Data>();
            DropdownData.Add(new Data { Value = "10", Text = "10" });
            DropdownData.Add(new Data { Value = "20", Text = "20" });
            DropdownData.Add(new Data { Value = "30", Text = "30" });
            DropdownData.Add(new Data { Value = "40", Text = "40" });
            DropdownData.Add(new Data { Value = "50", Text = "50" });
            ViewData["DropDownSource"] = DropdownData;
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
        }
	
{% endhighlight %}

{% endtabs %}

![](Functionalities_images/Functionalities_img10.jpeg)

## Client Side Validation

When you are developing the MVC application in Visual Studio then the client-side becomes enabled by default, but you can easily enable or disable the writing of the following app setting code snippet in the web.config file.

{% tabs %}

{% highlight xml %}

    <appSettings>
    
        <add key="ClientValidationEnabled" value="true" />
        <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    </appSettings>

{% endhighlight %}

{% endtabs %}

After setting the value as **true,** refer to the jQuery validation script file in the **_Layout page** as shown in the following code example.

{% tabs %}

{% highlight html %}

    <script src="@Url.Content("~/Scripts/jquery.validate.js")"></script>

{% endhighlight %}

{% endtabs %}

The jQuery validation plug-in takes advantage of the Data Annotation attributes defined in the model. Let's create a Sample model that has a single property with Data annotation attributes.

{% tabs %}

{% highlight c# %}

    using System.ComponentModel.DataAnnotations;
    public class DropDownListModel
    {
        [Required(ErrorMessage = "DropDownList value is Required")]
        public List<DropDownValue> DropData { get; set; }
    }

    public class DropDownValue
    {
        public string Text { get; set; }
        public string Value { get; set; }

    }

{% endhighlight %}

{% endtabs %}

After that you need to create the controller's action methods. These render views on the UI and bind a model with the view. So let's create a controller as follows.
The view is created as in the following code snippet:

{% tabs %}

{% highlight razor %}
    
    @model MvcApplication.Models.DropDownListModel

    @using (Html.BeginForm())
    {
        @Html.ValidationSummary(true)

        @Html.EJ().DropDownListFor(Model => Model. DropData,(Syncfusion.JavaScript.Models.DropDownListProperties)ViewData["properties"])
        <br />
        @Html.EJ().Button("btn").Size(ButtonSize.Small).Text("Post").Type(ButtonType.Submit)
    }

{% endhighlight %}

{% highlight c# %}
    
    using MvcApplication.Models;
    using Syncfusion.JavaScript.Models;
        public ActionResult DropdownlistFeatures()
        {
            BindingData();
            return View();
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
        [HttpPost]
        public ActionResult DropdownlistFeatures(DropDownListModel model)
        {
            BindingData();
            return View(model);
        }


{% endhighlight %}

{% endtabs %}

## Server side Validation

The ASP.NET MVC Framework validates any data passed to the controller action that is executing.
For DropDownList, we have to create a sample using Data Annotation API to validate the model data for it.
1. Create a model named DropDownListModel (DropDownListModel*.cs*) under the *Models* folder and applies Data Annotation attributes on the properties of the DropDownListModel class that is the Text property of the DropDownList.
2. Now, create an action method in the controller that returns a view with a model after the post request.

    {% tabs %}

    {% highlight c# %}
        
        using System.ComponentModel.DataAnnotations;
        public class DropDownListModel
        {
            public List<DropDownValue> DropData { get; set; }
        }

        public class DropDownValue
        {
            public string Text { get; set; }
            public string Value { get; set; }

        }

    {% endhighlight %}

    {% highlight c# %}
        
        using MvcApplication.Models;
        using Syncfusion.JavaScript.Models;
            public ActionResult DropdownlistFeatures()
            {
                BindingData();
                return View();
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
            [HttpPost]
            public ActionResult DropdownlistFeatures(DropDownListModel model)
            {
                if(ModelState.IsValid)
                    BindingData();
                return View(model);
            }

    {% endhighlight %}

    {% endtabs %}

3. After that, created a view to get value and show an error message if the value of the DropDownList is not given.
    
    {% tabs %}

    {% highlight razor %}

        @using (Html.BeginForm())
        {
            @Html.ValidationSummary(true)

            @Html.EJ().DropDownListFor(Model => Model.DropData,(Syncfusion.JavaScript.Models.DropDownListProperties)ViewData["properties"])

            <br />
            @Html.EJ().Button("btn").Size(ButtonSize.Small).Text("Post").Type(ButtonType.Submit)
        }

    {% endhighlight %}

    {% endtabs %}

