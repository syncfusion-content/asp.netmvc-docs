---
layout: post
title: How To | WaitingPopup | ASP.NET MVC | Syncfusion Server-side rendering
description: How to section of WaitingPopup widget.
platform: js
control: WaitingPopup
documentation: ug
---

# How To

## Render WaitingPopup from code behind

WaitingPopup can be rendered from the code behind by initializing the required properties in controller and passing those properties via ViewData or Model to the client side

The following code illustrates the rendering of WaitingPopup using WaitingPopup properties from code behind.

{% tabs %}

{% highlight razor %}
    
    <div id="target">
       @{Html.EJ().WaitingPopup("target", Model).Render();}
    </div>  
			
{% endhighlight %}

{% highlight c# %}
	
    public ActionResult Index()
        {
             WaitingPopupProperties Obj = new WaitingPopupProperties();
            Obj.ShowOnInit = true;
            return View(Obj);
        }
	
{% endhighlight %}

{% endtabs %}

