---
layout: post
title: How To | ProgressBar | ASP.NET MVC | Syncfusion
description: How To section of ProgressBar widget
platform: js
control: ProgressBar
documentation: ug
---

# How To

## Render ProgressBar from code behind

ProgressBar can be rendered from the code behind by initializing the required properties in controller and passing those properties via ViewData or Model to the client side

The following code illustrates the rendering of ProgressBar using ProgressBar properties from code behind.

{% tabs %}

{% highlight razor %}
    
         @{Html.EJ().ProgressBar("progress", Model).Render();}
			
{% endhighlight %}

{% highlight c# %}
	
    public ActionResult Index()
        {
            ProgressBarProperties Obj = new ProgressBarProperties();
            Obj.Text = "Loading...";
            Obj.Value = 60;
            return View(Obj);
        }
	
{% endhighlight %}

{% endtabs %}

