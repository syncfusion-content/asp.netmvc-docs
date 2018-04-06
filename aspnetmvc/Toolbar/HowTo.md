---
layout: post
title: How To | Toolbar | ASP.NET MVC | Syncfusion
description: How to section of Toolbar
platform: js
control: Toolbar
documentation: ug
---
# How To

## Render Toolbar from code behind

Toolbar can be rendered from the code behind by initializing the required properties in controller and passing those properties via ViewData or Model to the client side

The following code illustrates the rendering of Toolbar using Toolbar properties from code behind.

{% tabs %}

{% highlight razor %}
      
      @{ 
         Html.EJ().Toolbar("toolbar", (Syncfusion.JavaScript.Models.ToolbarProperties)ViewData["toolbar"]).Render();
       }
			
{% endhighlight %}

{% highlight c# %}
	
    public ActionResult Index()
        {
            List<ToolbarBaseItem> obj = new List<ToolbarBaseItem>();
            obj.Add(new ToolbarBaseItem() { SpriteCssClass= "e-icon e-cut" ,TooltipText="cut"});
            obj.Add(new ToolbarBaseItem() { SpriteCssClass = "e-icon e-copy", TooltipText = "copy" });
            obj.Add(new ToolbarBaseItem() { SpriteCssClass = "e-icon e-paste", TooltipText = "paste" });
            ToolbarProperties toolbarobj = new ToolbarProperties();
            toolbarobj.Items = obj;
            ViewData["toolbar"] = toolbarobj;
            return View();
        }
	
{% endhighlight %}

{% endtabs %}

