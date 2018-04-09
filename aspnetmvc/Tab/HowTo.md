---
layout: post
title: How to - Tab control for Syncfusion ASP.NET MVC
description: How To Section in tab control for Syncfusion ASP.NET MVC
platform: js
control: Tab
documentation: ug
---

# How To

## Add a tab item dynamically based on condition

To add tab item dynamically based on condition, we can use the conditional operators to check and add the items within the items property. Refer to the following code.

{% tabs %}

    {% highlight html %}

        @{Html.EJ().Tab("defaultTabs").Items(data =>
        {
            data.Add().ID("reviews").Text("Reviews").ContentTemplate(@<div>@{ Html.RenderPartial("_ReviewList"); }</div>);
            if (user == "admin") { // check the condition to load the item in tab
                    data.Add().ID("calendar").Text("Calendar").ContentTemplate(@<div> @{ Html.RenderPartial("_Calendar"); }</div>);
            }
        }).ShowRoundedCorner(true).Render();}
       
    {% endhighlight %}

{% endtabs %}

In the above code, based on the “user” the second tab will be displayed.

[Sample](http://www.syncfusion.com/downloads/support/directtrac/162785/ze/DropdownCascading_(5)696317518)

## Render Tab from code behind

Tab can be rendered from the code behind by initializing the required properties in controller and passing those properties via ViewData or Model to the client side

The following code illustrates the rendering of Tab using Tab properties from code behind.

{% tabs %}

{% highlight razor %}
      
     @{ 
           Html.EJ().Tab("Tab", (Syncfusion.JavaScript.Models.TabProperties)ViewData["tab"]).Render();
      }
			
{% endhighlight %}

{% highlight c# %}
	
    public ActionResult Index()
        {
            TabProperties tab = new TabProperties();
            tab.Items.Add(new TabBaseItem() { ID = "javaScript", Text = "JavaScript", ContentTemplate = new MvcTemplate<TabBaseItem> { RazorViewTemplate = (data) => { return "JavaScript (JS) is an interpreted computer programming language"; } } });
            tab.Items.Add(new TabBaseItem() { ID = "cSharp", Text = "C Sharp", ContentTemplate = new MvcTemplate<TabBaseItem> { RazorViewTemplate = (data) => { return " C# is intended to be a simple, modern, general-purpose, object-oriented programming language."; } } });
            tab.Items.Add(new TabBaseItem() { ID = "vb", Text = "VB.Net", ContentTemplate = new MvcTemplate<TabBaseItem> { RazorViewTemplate = (data) => { return "  The command-line compiler, VBC.EXE, is installed as part of the Freeware .NET Framework SDK."; } } });
            ViewData["tab"] = tab;
            return View();
        }
	
{% endhighlight %}

{% endtabs %}



