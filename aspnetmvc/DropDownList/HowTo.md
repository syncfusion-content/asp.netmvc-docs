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
        
        @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).HeaderTemplate("<div class='temp'><input id='check' type='checkbox' />   </div>").ShowCheckbox(true).Width("300").ClientSideEvents(clientEvent=>clientEvent.Create("create"))
        
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
            $("#check").ejCheckBox({ text: "Check All", change: "Change" });
        }
        function Change(args) {
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


## Dynamically bind the data to ejDropDownList on AJAX call

Render the DropDownList with the empty DataSource, In client event called “click” of Button control, the AJAX post is called.

{% highlight c# %}

    @Html.EJ().DropDownList("bikeList").DropDownListFields(df => df.ID("id").Text("text")).ClientSideEvents(e => e.Create("onCreate"))<br />

    @Html.EJ().Button("button").Text("click").ClientSideEvents(e => e.Click("onClick"))
    
{% endhighlight %}

{% highlight html %}

    public class DropDownController : Controller
    {
        // GET: DropDown
        public ActionResult Index()
        {
            return View();
        }
        public ActionResult Add()
        {
            return RedirectToAction("Index", "DropDown");
        }
    }

{% endhighlight %}

Once the AJAX call is success, bind the data to the dropdown list on AJAX call by using the property “dataSource”.

{% highlight javascript %}

    function onClick() {

        $.ajax({
            url: '/DropDown/Add',
            type: 'POST'
        }).success(function (result) {
            BikeList = [
                { id: "bk1", text: "Apache RTR" }, { id: "bk2", text: "CBR 150-R" }, { id: "bk3", text: "CBZ Xtreme" },
                { id: "bk4", text: "Discover" }, { id: "bk5", text: "Dazzler" }, { id: "bk6", text: "Flame" },
                { id: "bk7", text: "Fazzer" }, { id: "bk8", text: "FZ-S" }, { id: "bk9", text: "Pulsar" },
                { id: "bk10", text: "Shine" }, { id: "bk11", text: "R15" }, { id: "bk12", text: "Unicorn" }
            ];

            var data1 = $("#bikeList").data("ejDropDownList");
            data1.option("dataSource", BikeList);

        })
    }
    
{% endhighlight %}