---
layout: post
title: Render Tab control for Syncfusion ASP.NET MVC from controller
description: Render Tab control for Syncfusion ASP.NET MVC from controller
platform: ejmvc
control: Tab
documentation: ug
---

# Render Tab from code behind

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
