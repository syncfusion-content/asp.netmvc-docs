---
layout: post
title: EnableDisable-the-Slider
description: enable-disable the slider
platform: ejmvc
control: Slider
documentation: ug
---

# Enable/Disable the Slider

Slider widget includes an option to enable/disable it. When you disable the Slider, it is displayed in a blur state and you cannot perform any operations in it.

### Enabled

Using this Enabled property you can enable/disable the Slider. Data type of this property is “Boolean”.

The following steps explains you on how to disable the Slider.

1. In an VIEW page, specify the helper elements to render the Default Slider.

{% highlight html %}

// Add this code in your view page

@(Html.EJ().Slider("defaultSlider").Value("60").Width("500").Enabled(false))

{% endhighlight %}

Execute the above code example to render the following output.


![](EnableDisable-the-Slider_images/EnableDisable-the-Slider_img1.png)



