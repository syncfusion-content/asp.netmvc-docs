---
layout: post
title: How to - DropDownList control for Syncfusion ASP.NET MVC
description: How To Section in DropDownList control for Syncfusion ASP.NET MVC
platform: js
control: DropDownList
documentation: ug
keywords: Strongly Typed HTML Helper, DropDownList, dropdown, HTML Helper

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

Cascading operation can be performed in DropDownListFor. 

Defines the Employee class as follows

{% tabs %}

    {% highlight C# %}

        public class DropDownListModel
        {
            public List<Employee> DropData { get; set; }
            public List<DeptDetails> getDept { get; set; }
        }
        public class Employee
        {
            public string Name { get; set; }
            public string Department { get; set; }
        }
        public class DeptDetails
        {
            public string Department { get; set; }
            public string Subject { get; set; }
        }
        
    {% endhighlight %}
    
{% endtabs %}

In controller, defines Data source and properties for the both DropDownLists. The model will be passed to the view page. Here “DropDownListModel” class will be passed to the view. 

{% tabs %}

    {% highlight C# %}

        public ActionResult DropdownlistFeatures()
        {
            List<Employee> data = new List<Employee>() { };
            data.Add(new Employee() { Name = "Nancy", Department = "Computer Science" });
            data.Add(new Employee() { Name = "Angel", Department = "Mechanics" });
            data.Add(new Employee() { Name = "Prince", Department = "Electronics Communication" });
            data.Add(new Employee() { Name = "John", Department = "Information Technology" });
            data.Add(new Employee() { Name = "Daniha", Department = "Marine" });

            DropDownListModel model = new DropDownListModel();
            
            DropDownListProperties ddl = new DropDownListProperties();
            DropDownListFields ddf = new DropDownListFields();
            ddl.DataSource = data;
            ddl.CascadeTo = "getDept";
            ddf.Text = "Name";
            ddf.Value = "Department";
            ddl.DropDownListFields = ddf;
            ViewData["properties"] = ddl;

            List<DeptDetails> dept = new List<DeptDetails>() { };
            dept.Add(new DeptDetails() { Department = "Computer Science", Subject = "Software Engineering" });
            dept.Add(new DeptDetails() { Department = "Computer Science", Subject = "Software Testing" });
            dept.Add(new DeptDetails() { Department = "Computer Science", Subject = "Web Technology" });
            dept.Add(new DeptDetails() { Department = "Computer Science", Subject = "Data Ware Housing" });
            dept.Add(new DeptDetails() { Department = "Mechanics", Subject = "Thermal Engineering" });
            dept.Add(new DeptDetails() { Department = "Mechanics", Subject = "Materials Engineering, Composites." });
            dept.Add(new DeptDetails() { Department = "Mechanics", Subject = "Statics and dynamics" });
            dept.Add(new DeptDetails() { Department = "Mechanics", Subject = "Strength of materials and solid mechanics" });
            dept.Add(new DeptDetails() { Department = "Electronics Communication", Subject = "Signals & Systems" });
            dept.Add(new DeptDetails() { Department = "Electronics Communication", Subject = "Electromagnetic Engineering" });
            dept.Add(new DeptDetails() { Department = "Electronics Communication", Subject = "Electronics Communication" });
            dept.Add(new DeptDetails() { Department = "Information Technology", Subject = "Analog Electronic Circuits" });
            dept.Add(new DeptDetails() { Department = "Marine", Subject = "Effects of waves" });
            dept.Add(new DeptDetails() { Department = "Marine", Subject = "Towing and mooring" });
            dept.Add(new DeptDetails() { Department = "Marine", Subject = "Ocean structures" });

            DropDownListProperties deptProperties = new DropDownListProperties();
            DropDownListFields ddlFields = new DropDownListFields();
            deptProperties.DataSource = dept;
            deptProperties.Enabled = false;
            ddlFields.Text = "Subject";
            ddlFields.Value = "Department";
            deptProperties.DropDownListFields = ddlFields;
            ViewData["Department"] = deptProperties;

            return View(model);
         }
        
    {% endhighlight %}
    
    {% highlight C# %}
    
        @Html.EJ().DropDownListFor(Model => Model.DropData, (Syncfusion.JavaScript.Models.DropDownListProperties)ViewData["properties"])

        @Html.EJ().DropDownListFor(Model => Model.getDept, (Syncfusion.JavaScript.Models.DropDownListProperties)ViewData["Department"])
    
    {% endhighlight %}
    
{% endtabs %}

