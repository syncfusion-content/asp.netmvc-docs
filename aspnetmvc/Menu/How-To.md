---
layout: post
title: How To | Menu | ASP.NET MVC | Syncfusion
description: How To section of Menu widget
platform: js
control: Menu
documentation: ug
---

# How To

## Render Menu from code behind

Menu can be rendered from the code behind by initializing the required properties in controller and passing those properties via ViewData or Model to the client side

The following code illustrates the rendering of Menu using Menu properties from code behind.

{% tabs %}

{% highlight razor %}
    
         @{ 
              Html.EJ().Menu("Menu", (Syncfusion.JavaScript.Models.MenuProperties)ViewData["Menu"]).Render();
           }

{% endhighlight %}

{% highlight c# %}
	
    public ActionResult Index()
        {
            List<MenuBaseItem> obj = new List<MenuBaseItem>();
            obj.Add(new MenuBaseItem() { Text="Products"});
            obj.Add(new MenuBaseItem() { Text = "Support" });
            obj.Add(new MenuBaseItem() { Text = "Downloads" });
            obj.Add(new MenuBaseItem() { Text = "Purchase" });
            obj.Add(new MenuBaseItem() { Text = "Resources" });
            obj.Add(new MenuBaseItem() { Text = "Company" });
            MenuProperties menu = new MenuProperties();
            menu.Items = obj;
            menu.Width = "150";
            menu.Orientation = Syncfusion.JavaScript.Orientation.Vertical;
            ViewData["Menu"] = menu;
            return View();
        }
	
{% endhighlight %}

{% endtabs %}

