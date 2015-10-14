---
layout: post
title: Persistence Support | Slider | ASP.NET MVC | Syncfusion
description: persistence support
platform: ejmvc
control: Slider
documentation: ug
---

# Persistence Support

This feature supports you to save current model value to browser cookies for state maintenance. When you refresh the web page, the Slider control retains the model value apply from browser cookies. The data type of EnablePersistence is Boolean type. 

The following steps explains you on how to enable the EnablePersistence property.

1. In an VIEW page, add a helper element to render it as a Slider widget.

{% highlight CSHTML %}

// Add this code in your view page

@(Html.EJ().Slider("BasicSlider").Height("20").Width("500").EnablePersistence(true))

{% endhighlight %}

After execute the code, Increase the value and reload the page. The state is maintained in the Slider control.

![](Persistence-Support_images/Persistence-Support_img1.png)



