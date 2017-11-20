---
layout: post
title: Marker Pointers | lineargauge | ASP.NET MVC | Syncfusion
description: marker pointers
platform: ejmvc
control: lineargauge
documentation: ug
---

# Marker Pointers

**Marker Pointer** value points out the actual value set in the **Linear Gauge**. You can set values for various pointer attributes such as `value`, `type`, `length`, `width`, `border` and `color` in pointer collection. You can also customize the pointers to improve the appearance of gauge.

## Adding marker pointer collection

You can add **Marker Pointer** collection directly to the scale object. To add pointer collection in a gauge control refer the following code example.  


{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1")

.Value(78)



//Adding Scale Collection



.Scales(scale => {

    scale.Width(0).Border(border => border.Color("transparent").Width(0))

    .ShowBarPointers(true)



    //Adding marker pointer collection

    .MarkerPointers(mp => { mp.Width(5).Length(10)

    .MarkerBackgroundColor("Grey").MarkerDistanceFromScale(17).Add(); })



    //Adding bar pointer collection

    .BarPointers(bar =>

    {

        bar.Width(5)

        .BarPointerBackgroundColor("Grey").BarPointerDistanceFromScale(15).Add();

    })



    //Adding tick collection

    .Ticks(tic =>

    {

        tic.Type(TickType.MajorInterval).Width(2).Color("#8C8C8C")

        .DistanceFromScale(distance => distance.X(7).Y(0)).Add();

        tic.Type(TickType.MinorInterval).Width(1).Color("#8C8C8C")

        .DistanceFromScale(distance => distance.X(7).Y(0)).Height(6).Add();

    }).Add();

}))

{% endhighlight %}

Execute the above code to render the following output.


![](Marker-Pointers_images/Marker-Pointers_img1.png)



## Add marker pointer value

The `value` property is the important element in the marker pointer collection which indicates the gauge value. Real purpose of the **Linear Gauge** is based on the pointer value. You can set the pointer value either directly during rendering the control or it can be achieved by public method.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1")

.EnableAnimation(false)

.Width(600).Height(150).Orientation(Orientation.Horizontal).LabelColor("Black")

//Adding Frame object

.Frame(fr=>fr.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light1.png"))



//Adding scale collection

.Scales(scale => {

    scale.Width(30).BackgroundColor("#AEC75F").Border(border => border.Color("#AEC75F").Width(30))

    .Direction(Directions.Clockwise).Type(ScaleType.RoundedRectangle)



    //Adding marker pointer collection

    .MarkerPointers(mp => { mp.Width(30).Length(30)

    .MarkerBackgroundColor("#FE5C09").MarkerDistanceFromScale(20)

    .Placement(PointerPlacement.Near).Value(67.5).Add(); })



    //Adding label collection

    .Labels(label => { label.Angle(90).DistanceFromScale(distance => distance.Y(100).X(0)).Add(); })



    //Adding tick collection

    .Ticks(tic =>

    {

        tic.Type(TickType.MajorInterval).Width(2).Color("#8C8C8C")

        .DistanceFromScale(distance => distance.X(45).Y(0)).Add();

        tic.Type(TickType.MinorInterval).Width(1).Color("#8C8C8C")

        .DistanceFromScale(distance => distance.X(45).Y(0)).Height(6).Add();

    }).Add();

}))

{% endhighlight %}

Execute the above code to render the following output.


![](Marker-Pointers_images/Marker-Pointers_img2.png)



## Pointer Styles

### Appearance

* Based on the value, the **pointer** points out the label value. You can set the pointer length and width using `length` and `width` property respectively. You can also adjust the opacity of the pointer using the opacity property which holds the value between 0 and 1. You can add the gradient effects to the pointer using gradient object. 
* The marker pointer border is modified with the border object. It contains two border property namely color and width which are used to customize the border color of the scale and border width of the marker pointer. The background color can be customized with attribute `backgroundColor`.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1")

.EnableAnimation(false)

.Width(600).Height(150).Orientation(Orientation.Horizontal).LabelColor("Black")

.EnableResize(true)

//Adding Frame object

.Frame(fr=>fr.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light1.png"))

//Adding scale collection

.Scales(scale => {

    scale.BackgroundColor("#AEC75F").Border(border => border.Color("#AEC75F").Width(30))

    .Direction(Directions.Clockwise).Type(ScaleType.RoundedRectangle)



    //Adding marker pointer collection

    .MarkerPointers(mp => { mp.Width(30).Length(30).MarkerOpacity(0.4)

    .MarkerBackgroundColor("#FCDD34").MarkerDistanceFromScale(20)

    .Placement(PointerPlacement.Near).Value(67.5).Add(); })



    //Adding label collection

    .Labels(label => { label.Angle(90).DistanceFromScale(distance => distance.Y(100).X(0)).Add(); })



    //Adding tick collection

    .Ticks(tic =>

    {

        tic.Type(TickType.MajorInterval).Width(2).Color("#8C8C8C")

        .DistanceFromScale(distance => distance.X(-1).Y(45)).Add();

        tic.Type(TickType.MinorInterval).Width(1).Color("#8C8C8C")

        .DistanceFromScale(distance => distance.X(-1).Y(45)).Height(6).Add();

    }).Add();

}))

{% endhighlight %}

Execute the above code to render the following output.

![](Marker-Pointers_images/Marker-Pointers_img3.png)



## Positioning the pointer

* You can position the Pointer with two properties, **distanceFromScale** and **placement**. The `distanceFromScale` property defines the distance between the scale and pointer. 
* The `Placement` property is used to locate the pointer with respect to scale either inside or outside the scale or along the scale. It is an enumerable data type.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1")

.EnableAnimation(false)

.Width(600).Height(150).Orientation(Orientation.Horizontal).LabelColor("Black")



//Adding frame object

.Frame(fr=>fr.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light1.png"))



//Adding scale collection

.Scales(scale => {

    scale.Width(30).BackgroundColor("#AEC75F").Border(border => border.Color("#AEC75F").Width(30))

    .Direction(Directions.Clockwise).Type(ScaleType.RoundedRectangle)



    //Adding marker pointer collection

    .MarkerPointers(mp => { mp.Width(30).Length(30).MarkerOpacity(0.4)

    .MarkerBackgroundColor("#01A357").MarkerDistanceFromScale(60)

    .Placement(PointerPlacement.Near).Value(55.5).Add(); })



    //Adding label collection

    .Labels(label => { label.Angle(90).DistanceFromScale(distance => distance.Y(100).X(0)).Add(); })



    //Adding ticks collection

    .Ticks(tic =>

    {

        tic.Type(TickType.MajorInterval).Width(2).Color("#8C8C8C")

        .DistanceFromScale(distance => distance.X(-1).Y(45)).Add();

        tic.Type(TickType.MinorInterval).Width(1).Color("#8C8C8C")

        .DistanceFromScale(distance => distance.X(-1).Y(45)).Height(6).Add();

    }).Add();

}))

{% endhighlight %}

Execute the above code to render the following output.

![](Marker-Pointers_images/Marker-Pointers_img4.png)



## Types

It is possible to change the dimension of the marker pointer. Dimensions available for marker pointer are,

* Rectangle
* Triangle
* Ellipse
* Diamond
* Pentagon
* Circle
* Slider
* Pointer
* Wedge
* Trapezoid
* Rounded Rectangle



### Multiple Marker Pointers

**Linear Gauge** can contain multiple pointers on it. You can use any combination and any number of pointers in a gauge. That is, a gauge can contain any number of marker pointer and any number of bar pointers. Refer the following code example containing multiple marker pointers.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1")

.EnableAnimation(false).LabelColor("Black").EnableResize(true)

.Width(600).Theme(Themes.FlatLight).Height(250)

.Orientation(Orientation.Horizontal).LabelColor("Black")



//Adding frame object

.Frame(fr=>fr.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light1.png"))



//Adding scale collection

.Scales(scale => {

    scale.Width(30).BackgroundColor("#AEC75F")

    .Border(border => border.Color("#AEC75F").Width(30))

    .Direction(Directions.Clockwise)

    .Type(ScaleType.RoundedRectangle).ShowCustomLabels(true)



    //Adding marker pointer collection

    .MarkerPointers(mp =>

    {

        //Adding marker pointer 1

        mp.Width(30).Length(30)

        .MarkerBackgroundColor("#01A357").MarkerDistanceFromScale(60)

        .Placement(PointerPlacement.Near).Value(32.2).Add();



        //Adding marker pointer 2

        mp.Width(10).Length(30)

        .MarkerBackgroundColor("#90DAFB").MarkerDistanceFromScale(60)

        .Placement(PointerPlacement.Near).Value(23.7).Type(MarkerType.Circle).Add();



        //Adding marker pointer 3

        mp.Width(3).Length(30)

        .MarkerBackgroundColor("#90DAFB").MarkerDistanceFromScale(60)

        .Placement(PointerPlacement.Near).Value(23.7).Type(MarkerType.Star).Add();

    })



    //Adding label collection

    .Labels(label => { label.Angle(90).DistanceFromScale(distance => distance.Y(100).X(0)).Add(); })



    //Adding tick collection

    .Ticks(tic =>

    {

        tic.Type(TickType.MajorInterval).Width(2).Color("#8C8C8C")

        .DistanceFromScale(distance => distance.X(45).Y(0)).Add();

        tic.Type(TickType.MinorInterval).Width(1).Color("#8C8C8C")

        .DistanceFromScale(distance => distance.X(45).Y(0)).Height(6).Add();

    })



    //Adding custom label collection

    .CustomLabels(cl => { cl.Value("Weather Condition in California")

    .Position(position => position.X(52).Y(20)).Add();

    })

    .Add();

}))

{% endhighlight %}

Execute the above code to render the following output.



![](Marker-Pointers_images/Marker-Pointers_img5.png)



