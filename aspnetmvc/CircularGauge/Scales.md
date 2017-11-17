---
layout: post
title: Scales | CircularGauge | ASP.NET MVC | Syncfusion
description: scales
platform: ejmvc
control: CircularGauge
documentation: ug
---

# Scales

**Scales** are the basic functional block of the **Circular Gauge**. By customizing the `Scales`, the appearance of the **Gauge** can be improved. The functional blocks of Circular Gauge are 

* Pointers
* Labels
* CustomLabels
* Indicators
* Ticks
* Ranges
* Sub gauges.

## Adding Scale Collection


**Scale collection** is directly added to the Gauge object. Refer the following code example to add scale collection in **Gauge** control.

{% highlight CSHTML %}

//For circular gauge rendering

@(Html.EJ().CircularGauge("circulargauge")

.Scales(SC =>

{

SC.Radius(130).Add();

}))

{% endhighlight  %}

Execute the above code to render the following output.

![](Scales_images/Scales_img1.png)

Circular Gauge with scale radius.
{:.caption}


## Scale Customization

### Colors and Border

* The Scale border is modified with the object called `Border`. It has two border property namely `Color` and `Width` which are used to customize the border color of the scale and border width of the scale. 
* Setting the background color improves the look and feel of the **Circular Gauge**. You can customize the background color of the scale using `BackgroundColor`. 
* The scale bar of circular gauge can be enabled by setting `ShowScaleBar` property as true.

{% highlight CSHTML %}

//For circular gauge rendering

@(Html.EJ().CircularGauge("circulargauge")

.Scales(SC =>

{

SC.Radius(130)

.BackgroundColor("Red")

.ShowScaleBar(true)

.Border(b =>{

//For scale border width

b.Width(3)

//For scale border color

.Color("Blue");

})

.Pointers(pointer =>

{

pointer.Length(80).Add();

}).Add();

})

)
{% endhighlight  %}


Execute the above code to render the following output.



![](Scales_images/Scales_img2.png)

Circular Gauge with customized scale border
{:.caption}

### Pointer Cap

* **Pointer cap** is a circular shape element that is located at the center of the **Circular Gauge**. The pointer cap is one of the cynosure of the Circular Gauge. By customizing the pointer cap, Gauge style is improved. The pointer cap is modified with the object `PointerCap`. 
* It contains `Radius`, `BorderColor`, `BorderWidth`, `InteriorGradient` and `BackgroundColor` properties. The property `radius` is used to set the radius for the pointer cap. `InteriorGradient` is used to provide the gradient effects to the pointer cap.

{% highlight CSHTML %}


//For circular gauge rendering

@(Html.EJ().CircularGauge("circulargauge")

.Scales(SC =>

{

SC.PointerCap(cap =>

{

//For setting pointer cap radius

cap.Radius(10)

// For setting pointer cap border width

.BorderWidth(4)

// For setting pointer cap border color

.BorderColor("Blue")

// For setting pointer cap background

.BackgroundColor("Red");

}).Add();

}))


{% endhighlight %}

Execute the above code to render the following output.

![](Scales_images/Scales_img3.png)

Circular Gauge with customized pointer cap
{:.caption}

### Appearance

* Circular Gauge contains two types of scale direction such as clockwise and counter clockwise. You can set them by enumerable property called `Direction`. And you can set the minimum and maximum values for the scale with the properties `Minimum` and `Maximum`. The two properties `MinorIntervalValue` and `MajorIntervalValue` are the values used to set interval value for the ticks and labels. 
* The `Radius` property is used to set the radius value for the circular scale and the `Size` property is used to set the scale bar width. You can also adjust the Opacity of the scale with the property `Opacity`. The value for opacity lies between 0 and 1. You can also give some shadow effects for the scale by using the property `ShadowOffset`. The property `StartAngle` is used to set starting position of the scale at certain angle and `SweepAngle` is used to shrink or expand the scale to certain angle. 

{% highlight CSHTML %}

// For Circular Gauge rendering

@(Html.EJ().CircularGauge("circulargauge")

.Scales(scale =>

{

// For setting scale bar size

scale.Size(30)

// For setting scale minimum value

.Minimum(20)

// For setting scale maximum value

.Maximum(120)

// For setting scale major interval value

.MajorIntervalValue(20)

// For setting scale minor interval

.MinorIntervalValue(5)

// For setting scale background color

.BackgroundColor("Red")

// For setting scale bar opacity

.Opacity(0.5)

// For setting scale bar shadow offset

.ShadowOffset(20)

// For setting scale direction

.Direction(Directions.CounterClockwise).Add();

})

)

{% endhighlight  %}

Execute the above code to render the following output.

![](Scales_images/Scales_img4.png)

Circular Gauge with customized scale values
{:.caption}

### Enable/Disable properties

You can enable / disable properties in Circular Gauge using some properties in scale collection. The `ShowIndicators` property is used to enable/disable the indicators. `ShowLabels`, `ShowTicks`, `ShowRanges`, `ShowPointers` ans `ShowScaleBar` are used to enable/ disable labels, ticks, ranges, pointers and scale bar respectively. 



## Multiple Scales

You can set **Multiple scales** for a single **Circular Gauge** control by using an array of scale objects. Each scale object is independent of each other. The following code example refers to two scale objects in a Gauge.

{% highlight CSHTML %}


// For Circular Gauge rendering

@(Html.EJ().CircularGauge("circulargauge")

.Scales(scale =>

{

// For setting  first scale

scale.ShowScaleBar(true)

.Size(10)

.Radius(150)

.Minimum(20)

.Maximum(120)

.MajorIntervalValue(20)

.MinorIntervalValue(5)

.Pointers(p => { p.Length(120).Value(50).Add(); })

.Direction(Directions.Clockwise)

.ShadowOffset(20).Add();

// For setting second scale

scale.Size(10)

.ShowScaleBar(false)

.Radius(80)

.MajorIntervalValue(10)

.Labels(lb =>lb.DistanceFromScale(-40).Color("Red").Add())

.Ticks(t =>t.Color("Red").Add())

.Pointers(p => { p.Length(50).Value(40).DistanceFromScale(-30).Add();  })

.Direction(Directions.CounterClockwise)

.Opacity(0.5)

.ShadowOffset(5).Add();

})

)



{% endhighlight  %}

Execute the above code to render the following output.

![](Scales_images/Scales_img5.png)

Circular Gauge with multiples scales
{:.caption}


