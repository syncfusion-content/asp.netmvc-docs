---
layout: post
title: How To | Rating | ASP.NET MVC | Syncfusion
description: How To section of Rating widget
platform: js
control: Rating
documentation: ug
---

# How To

## Render Rating from code behind

Rating can be rendered from the code behind by initializing the required properties in controller and passing those properties via ViewData or Model to the client side

The following code illustrates the rendering of Rating using Rating properties from code behind.

{% tabs %}

{% highlight razor %}
    
         @{Html.EJ().Rating("univRating", Model).Render();}
			
{% endhighlight %}

{% highlight c# %}
	
    public ActionResult Index()
        {
            RatingProperties Obj = new RatingProperties();
            Obj.Value = 4;
            Obj.Orientation = Syncfusion.JavaScript.Orientation.Vertical;
            return View(Obj);
        }
	
{% endhighlight %}

{% endtabs %}

