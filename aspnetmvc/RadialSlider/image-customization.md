---
layout: post
title: Image-Customization | RadialSlider | ASP.NET MVC | Syncfusion
description: Image-Customization
platform: ejmvc
control: RadialSlider
documentation: ug
---
# Image customization

## Customizing inner circle 

### Using Class

The **RadialSlider** property **InnerCircleImageClass** allow to set image for the inner circle of the  **RadialSlider**.  By default, the **Radial Slider** innerCircleImageClass is set as "null". Refer to the following code example.

{% tabs %}
{% highlight CSHTML %}

    @Html.EJ().RadialSlider("slider").InnerCircleImageClass("custom-circle")
{% endhighlight %}
{% highlight css %}
    <style>
        .e-custom-circle {
            background-image: url("../images/radialslider/diagram.png");
        }
    </style>

{% endhighlight %}
{% endtabs %}

The following screenshot illustrates the output of above code.

![](image-customization_images\image-customization_img1.png)


### Using image URL 

The **RadialSlider** property **InnerCircleImageUrl** allow to set URL image to the inner circle of the **RadialSlider**.  By default, the **Radial Slider** InnerCircleImageUrl  is set as "null". Refer to the following code example.

{% highlight CSHTML %}

    @Html.EJ().RadialSlider("slider").InnerCircleImageUrl("../images/radialslider/chevron-right.png")

{% endhighlight %}

The following screenshot illustrates the output of above code.

![](image-customization_images\image-customization_img2.png)




