---
layout: post
title: Interaction and Animation | CircularGauge | ASP.NET MVC | Syncfusion
description: interaction and animation
platform: ejmvc
control: CircularGauge
documentation: ug
---

# Interaction and Animation

## Interaction

* **Circular Gauge** control contains **Interaction** feature. You can use this interaction feature to change the pointer values manually. You can achieve this by clicking and dragging the pointer over the Gauge and you can see the value of pointer changes dynamically while dragging.
* To Enable/Disable the user interaction you can use the Boolean property called `ReadOnly`. The user interaction option is enabled when you set the value as false for the property readOnly.By default it holds the true value.That is by default it does not support interaction. 

{% highlight CSHTML %}

// For Circular Gauge rendering

@(Html.EJ().CircularGauge("circulargauge")

// For User interaction

.ReadOnly(false))

)

{% endhighlight  %}

Execute the above code to render the following output.



![](Interaction-and-Animation_images/Interaction-and-Animation_img1.png)

Circular Gauge with basic interaction property
{:.caption}

## Animations

* **Circular Gauge** contains an attractive concept called **Animation**. The animation option enables the pointer to rotate from the minimum value to the current value with animation effects. By using this animation you can change the pointer value dynamically.You can apply the animation on  pointer either by clockwise or counterclockwise based on the scale direction. 
* You can enable / disable it using the property `EnableAnimation`. Animation is enabled when you set enableAnimation as ‘true’. By default it holds the true value. You can control the speed of the pointer during animating by using the property `AnimationSpeed`. It is a numerical value that holds the time in milliseconds. That is when the value is given as 1000, it is considered as 1 second.

{% highlight CSHTML %}


// For Circular Gauge rendering

@(Html.EJ().CircularGauge("circulargauge")

// For enabling animation

.EnableAnimation(true)

// For setting animation speed

.AnimationSpeed(1000)

)

{% endhighlight  %}

Execute the above code to render the following output.



![](Interaction-and-Animation_images/Interaction-and-Animation_img2.png)

Circular Gauge with basic Animation property
{:.caption}

## Gradient

You can change the interior gradient of **Circular Gauge** by using `InteriorGradient` property. The `IsRadialGradient` property is used to check whether the gradient is circular or not.  

{% highlight CSHTML %}
@(Html.EJ().CircularGauge("circulargauge")

    .InteriorGradient(gradient=>gradient
                    .ColorInfo(info=>
                    [
                        info.ColorStop(0).Color("#FFFFFF").Add();
                        info.ColorStop(1).Color("#AAAAAA").Add();
                    ]).Add();
    )  
    .IsRadialGradient(true)
)     
    
{% endhighlight %}

## Distance From Corner

You can display the circular gauge from distance apart from the corner by specifying value for `DistanceFromCorner` property. 

{% highlight CSHTML %}

@(Html.EJ().CircularGauge("circulargauge")

    .DistanceFromCorner(25)

)

{% endhighlight %}

## Resize

Circular gauge can be responsive while resizing by specifying `EnableResize` property as true. 

{% highlight CSHTML %}

@(Html.EJ().CircularGauge("circulargauge")

    .EnableResize(true)

)

{% endhighlight %}

## Localization

The circular gauge can be localized based on name of culture specified in `Locale` property.

{% highlight CSHTML %}

@(Html.EJ().CircularGauge("circulargauge")

    .Locale("en-US")

)  

{% endhighlight %}

## Themes

**CircularGauge** `Theme` is a set of pre-defined options that are applied to the control before **CircularGauge** is instantiated. Following predefined themes are available in JavaScript **CircularGauge**.

1. flatlight
2. flatdark
3. gradientlight 
4. gradientdark 
5. azure                      
6. azuredark               
7. lime 
8. limedark
9. saffron
10. saffrondark
11. gradientazure
12. gradientazuredark
13. gradientlime
14. gradientlimedark
15. gradientsaffron
16. gradientsaffrondark

The theme for circular gauge can be specified using `Theme` property.

{% highlight CSHTML %}

@(Html.EJ().CircularGauge("circulargauge")

    .Theme("flatlight")

)   

{% endhighlight %}

## Circular Gauge Values 

The `Minimum`, `Maximum`, `Radius` and `Value` attributes of circular gauge are used to render the circular gauge with specified location. 

{% highlight CSHTML %}

@(Html.EJ().CircularGauge("circulargauge")

     .Maximum(120)
     .Minimum(10)
     .Value(30)
     .Radius(100)
)  

{% endhighlight %}


