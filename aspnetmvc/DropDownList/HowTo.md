---
layout: post
title: How to - DropDownList control for Syncfusion ASP.NET MVC
description: How To Section in DropDownList control for Syncfusion ASP.NET MVC
platform: js
control: DropDownList
documentation: ug
---

# How To

## Add check all option in popup list?

You can use HeaderTemplate property to add any HTML element. Code snippet to add check all option is given below,

{% tabs %}

    {% highlight html %}

        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).HeaderTemplate("<div class='temp'><input id='check' type='checkbox' />   </div>").ShowCheckbox(true).Width("300").ClientSideEvents(ce=>ce.Create("create"))
        
    {% endhighlight %}

    {% highlight css %}

            .temp {
                height: 30px;
                display: block;
                padding-left: 13px;
                padding-top: 5px;
                border-bottom: 1px solid #c8c8c8;
            }
            .e-chkbox-wrap .e-text {
                font-size: 14px;
                padding-left: 10px;
            }

        
    {% endhighlight %}

    {% highlight js %}

        function create(args) {
            $("#check").ejCheckBox({ text: "Check All", change: "onallChange" });
        }
        function onallChange(args) {
            window.flag = true;
            var obj = $("#DropDownList1").ejDropDownList("instance");
            if (args.isChecked) obj.checkAll();
            else obj.uncheckAll();
            window.flag = false;
        }
        
    {% endhighlight %}

    {% highlight c# %}
            
            public ActionResult Index()
            {
                List<Data> DropdownData = new List<Data>();
                DropdownData.Add(new Data { Value = "item1", Text = "List Item 1" });
                DropdownData.Add(new Data { Value = "item2", Text = "List Item 2" });
                DropdownData.Add(new Data { Value = "item3", Text = "List Item 3" });
                DropdownData.Add(new Data { Value = "item4", Text = "List Item 4" });
                DropdownData.Add(new Data { Value = "item5", Text = "List Item 5" });
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

The following screenshot exhibits the output of the above code,

![](HowTo_images/HowTo_img2.jpeg)

## Render the DropDownList in Partial View using normal mode

Create a Partial View and define as follows

{% highlight razor %}

    @using DropdownList.Models

    @Html.EJ().DropDownList("DropDown").Datasource((List<DropDownValue>)ViewData["DataSrc"]).DropDownListFields(df=>df.Text("Text").Value("Value"))
    @Html.EJ().ScriptManager()

{% endhighlight %}

***Note: While rendering a control in the partial view, we need to specify @Html.EJ().ScriptManager() in the partial view page after the initializing the control.***

Render the partial view into parental view

{% highlight razor %}
    
    @Html.Partial("PartialView1")

{% endhighlight %}

Define DataSource and other required properties for rendering a simple DropDownList

{% highlight c# %}
   
    public ActionResult MainView()
        {
            List<DropDownValue> data = new List<DropDownValue>() { };
            data.Add(new DropDownValue() { Value = "item1", Text = "List Item 1" });
            data.Add(new DropDownValue() { Value = "item2", Text = "List Item 2" });
            data.Add(new DropDownValue() { Value = "item3", Text = "List Item 3" });
            data.Add(new DropDownValue() { Value = "item4", Text = "List Item 4" });
            data.Add(new DropDownValue() { Value = "item5", Text = "List Item 5" });
            ViewData["DataSrc"] = data;
            return View();
         }
         
{% endhighlight %}

## Render the DropDownList in Partial View using Unobtrusive mode

When you enable the **unobtrusive** in your application, refer to the **ej.unobtrusive.min.js** file in the application.
You have to set the value of **UnobtrusiveJavaScriptEnabled** to **true** in Root directory **web.config** file as shown in the following code example.
{% highlight xml %}

    <appSettings>
        <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    </appSettings>

{% endhighlight %}

After setting the value as **true,** refer to the unobtrusive script file in the **_Layout page** as shown in the following code example.

{% tabs %}

{% highlight razor %}
    
    <head>
    <script src="@Url.Content("~/Scripts/ej/ej.unobtrusive.min.js")"></script>
    </head>

{% endhighlight %}

{% endtabs %}

Create a Partial View and define as follows

{% highlight razor %}

    @using DropdownList.Models

    @Html.EJ().DropDownList("DropDown").Datasource((List<DropDownValue>)ViewData["DataSrc"]).DropDownListFields(df=>df.Text("Text").Value("Value"))


{% endhighlight %}

Render the partial view into parental view.

{% highlight razor %}
    
    @Html.Partial("PartialView1")

{% endhighlight %}

Define DataSource and other required properties for rendering a simple DropDownList

{% highlight c# %}
    
    public ActionResult MainView()
        {
            List<DropDownValue> data = new List<DropDownValue>() { };
            data.Add(new DropDownValue() { Value = "item1", Text = "List Item 1" });
            data.Add(new DropDownValue() { Value = "item2", Text = "List Item 2" });
            data.Add(new DropDownValue() { Value = "item3", Text = "List Item 3" });
            data.Add(new DropDownValue() { Value = "item4", Text = "List Item 4" });
            data.Add(new DropDownValue() { Value = "item5", Text = "List Item 5" });
            ViewData["DataSrc"] = data;
            return View();
         }
{% endhighlight %}