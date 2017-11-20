---
layout: post
title: Sub Gauges | CircularGauge | ASP.NET MVC | Syncfusion
description: sub gauges
platform: ejmvc
control: CircularGauge
documentation: ug
---

# Sub Gauges

A **Circular Gauge** containing another circular gauge is said to be `SubGauges`. In order to make  a sample like watch that has second gauge, minute gauge and hour gauge, sub gauges are used.

## Adding SubGauges

Sub gauge collection is directly added to the scale object. Refer the following code example to add custom sub gauge collection in a **Gauge** control

{% highlight CSHTML %}

@(Html.EJ().CircularGauge("circulargauge")

.Value(50)

.Scales(scale =>

{

scale.Radius(190)

//For setting sub gauge

.SubGauges(gauge =>

{

gauge.ControlID("Subgauge1")

.Height(200)

.Width(200)

.Position(p =>p.X(100).Y(120)).Add();

}).Add();

})

)

@(Html.EJ().CircularGauge("Subgauge1")

.BackgroundColor("Blue")

.Value(50)

.Scales(scale=>{scale.Radius(150).Add();})

)
{% endhighlight  %}

### Basic Customization

Basic attributes such as `Height` and `Width` property are used to set height and width of the sub gauge. You can easily position the gauge in another gauge using the `Position` object and by giving the `X` and `Y` Coordinates value. **ControlID** attribute is used to specify the sub gauge ID.

{% highlight CSHTML %}


@(Html.EJ().CircularGauge("Subgauge1")

.BackgroundColor("Blue")

.Value(50)

.Radius(110)

.Scales(scale=>{scale.Radius(110).Add();})

)


@(Html.EJ().CircularGauge("circulargauge")

.Height(500)

.Width(500)

.Value(50)

.Scales(scale =>

{

scale.Radius(190)

.SubGauges(gauge =>

{

//For setting sub gauge control ID

gauge.ControlID("Subgauge1")

//For setting sub gauge Height

.Height(250)

//For setting sub gauge width

.Width(250)

//For setting sub gauge position

.Position(p =>p.X(150).Y(100)).Add();

}).Add();

})

)

{% endhighlight  %}

Execute the above code to render the following output.

![](Sub-Gauges_images/Sub-Gauges_img1.png)

Circular Gauge with sub gauge
{:.caption}


## Multiple SubGauges

You can set multiple sub gauges in a single **Circular Gauge** by adding an array of sub gauge objects. Refer the following code example for multiple sub gauges functionality.

{% highlight CSHTML %}


@(Html.EJ().CircularGauge("Subgauge1")

.BackgroundColor("#f5b43f")

.Scales(scale => { scale.Radius(150).Add(); })

)

@(Html.EJ().CircularGauge("Subgauge2")

.BackgroundColor("#f5b43f")

.Scales(scale => { scale.Radius(150).Add(); })

)

@(Html.EJ().CircularGauge("circulargauge")

.Height(500)

.Width(500)

.Scales(scale =>

{

scale.Radius(250)

.SubGauges(gauge =>

{

//Sub gauge1

gauge.ControlID("Subgauge1")

.Height(200)

.Width(200)

.Position(p =>p.X(200).Y(150)).Add();

//Sub gauge2

gauge.ControlID("Subgauge2")

.Height(200)

.Width(200)

.Position(p =>p.X(50).Y(200)).Add();

}).Add();

})

)


{% endhighlight %}


Execute the above code to render the following output.

![](Sub-Gauges_images/Sub-Gauges_img2.png)

Circular Gauge with multiple sub gauges
{:.caption}


