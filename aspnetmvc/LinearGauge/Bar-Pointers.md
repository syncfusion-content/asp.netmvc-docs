---
layout: post
title: Bar Pointers | lineargauge | ASP.NET MVC | Syncfusion
description: bar pointers
platform: ejmvc
control: lineargauge
documentation: ug
---

# Bar Pointers

Bar Pointer value points out the actual value set in the Linear Gauge as marker pointer. You can set the values of the various bar pointer attributes such as value, width, border and color in bar pointer collection.  You can also customize the pointers to improve the appearance of gauge.

## Adding bar pointer collection

You can add Bar Pointer collection directly to the scale object. Refer the following code example.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1").EnableAnimation(false)



//Adding frame object

.Frame(fr=>fr.InnerWidth(8).OuterWidth(10)

.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light.png"))

.Value(78)



//Adding scale collection

.Scales(scale => {

    scale.Width(0).Border(border => border.Color("transparent").Width(0))

    .ShowBarPointers(true).ShowMarkerPointers(false)



    //Adding bar pointer collection

    .BarPointers(bar => {

        bar.Width(5).BarPointerDistanceFromScale(15)

        .BarPointerBackgroundColor("Grey").Add();

    })



    //Adding ticks collection

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


![](Bar-Pointers_images/Bar-Pointers_img1.png)

Linear Gauge with bar pointer
{:.caption}

## Adding bar pointer value

Bar pointer value is also important element in the Linear Gauge as it indicates the gauge value. Real purpose of the Linear Gauge is based on the pointer value. You can set the bar pointer value either directly during rendering the control or it can be achieved by public method.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1").EnableAnimation(false)

//Adding frame object

.Frame(fr=>fr.InnerWidth(8).OuterWidth(10)

.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light.png"))



//Adding scale object

.Scales(scale => {

    scale.Width(0).Border(border => border.Color("transparent").Width(0))

    .ShowBarPointers(true).ShowMarkerPointers(false)



    //Adding bar pointer collection

    .BarPointers(bar => {

        bar.Width(5).BarPointerDistanceFromScale(15)

        .BarPointerBackgroundColor("Grey").BarPointerValue(91).Add();

    })



    //Adding ticks collection

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

![](Bar-Pointers_images/Bar-Pointers_img2.png)



## Pointer Styles

### Appearance

* Based on the value, the bar pointer points out the label value. You can set the bar pointer width using width property and you can also adjust the opacity of the pointer using opacity property that holds the value between 0 and 1. You can add the gradient effects to the pointer using gradient object. 
* The marker pointer border is modified with the object border. It has two border property, color and width which are used to customize the border color of the scale and border width of the marker pointer. The background color can be customized with attribute backgroundColor.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1").EnableAnimation(false)



//Adding frame object

.Frame(fr=>fr.InnerWidth(8).OuterWidth(10)

.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light.png"))



//Adding scale collection

.Scales(scale => {

    scale.Width(0).Border(border => border.Color("transparent").Width(0))

    .ShowBarPointers(true).ShowMarkerPointers(false)



    //Adding bar pointer collection

    .BarPointers(bar => {

        bar.Width(10).BarPointerDistanceFromScale(15).BarPointerOpacity(0.7)

        .BarPointerBackgroundColor("Red").BarPointerValue(91).Add();

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

![](Bar-Pointers_images/Bar-Pointers_img3.png)



## Positioning the pointer

* Bar pointer can be positioned with two properties such as distanceFromScale and placement. The distanceFromScale property defines the distance between the scale and pointer element. 
* The placement property is used to locate the pointer with respect to scale either inside or outside the scale or along the scale. It is an enumerable data type.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1").EnableAnimation(false)



//Adding frame object

.Frame(fr=>fr.InnerWidth(8).OuterWidth(10)

.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light.png"))

//Adding scale collection

.Scales(scale => {

    scale.Width(0).Border(border => border.Color("transparent").Width(0))

    .ShowBarPointers(true).ShowMarkerPointers(false)



    //Adding bar pointer collection

    .BarPointers(bar => {

        bar.Width(10).BarPointerDistanceFromScale(40)

        .BarPointerBackgroundColor("#8BABFF").BarPointerValue(91).Add();

    })



    //Adding ticks collection

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

![](Bar-Pointers_images/Bar-Pointers_img4.png)



## Multiple Bar Pointers

Linear Gauge can contain multiple bar pointers on it. You can use any combination and any number of pointers in a gauge. That is, a Gauge can contain any number of marker pointer and any number of bar pointers. Refer the following code example containing multiple bar pointers.


{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1").EnableAnimation(false)

.Height(500).Width(300).LabelColor("Grey")



//Adding frame object

.Frame(fr=>fr.InnerWidth(8).OuterWidth(10)

.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_dark1.png"))



//Adding scale collection

.Scales(scale => {

    scale.Width(0).Border(border => border.Color("transparent").Width(0))

    .ShowBarPointers(true).ShowMarkerPointers(false).ShowCustomLabels(true)



    //Adding bar pointer collection

    .BarPointers(bar =>

    {

        //Adding bar pointer 1

        bar.Width(10).BarPointerDistanceFromScale(60)

        .BarPointerBackgroundColor("#8BABFF").BarPointerValue(91).Add();

        //Adding bar pointer 2

        bar.Width(10).BarPointerDistanceFromScale(20)

        .BarPointerBackgroundColor("#FDB761").BarPointerValue(51).Add();

        //Adding bar pointer 3

        bar.Width(10).BarPointerDistanceFromScale(100)

        .BarPointerBackgroundColor("Red").BarPointerValue(88).Add();

    })



    //Adding tick collection

    .Ticks(tic =>

    {

        tic.Type(TickType.MajorInterval).Width(2).Color("#8C8C8C")

        .DistanceFromScale(distance => distance.X(7).Y(0)).Add();

        tic.Type(TickType.MinorInterval).Width(1).Color("#8C8C8C")

        .DistanceFromScale(distance => distance.X(7).Y(0)).Height(6).Add();

    })



    //Adding custom label collection

    .CustomLabels(cl => {

        cl.Value("Mathematics Mark Comparison").Position(position => position.X(55).Y(97)).Add();

        cl.Value("Half yearly").Position(position => position.X(72).Y(87)).TextAngle(90).Add();

        cl.Value("Quarterly").Position(position => position.X(56).Y(87)).TextAngle(90).Add();

        cl.Value("Annual").Position(position => position.X(87).Y(87)).TextAngle(90).Add();

    }).Add();

}))

{% endhighlight %}

Execute the above code to render the following output.



![](Bar-Pointers_images/Bar-Pointers_img5.png)



