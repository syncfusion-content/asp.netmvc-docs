---
layout: post
title: Ticks
description: ticks
platform: ejmvc
control: Circular Gauge
documentation: ug
---

## Ticks

Ticks are used to mark some values on the scale. Based on the tick’s value you can set the labels on the required position.

### Adding Tick Collection 

Tick collection is directly added to the scale object. Refer the following code example to add tick collection in a Gauge control.



[View]

//For circular gauge rendering

@(Html.EJ().CircularGauge("circulargauge")

.Scales(sc1 =>

{

sc1.Ticks(tc =>

{

// For setting tick

tc.Type(CircularTickTypes.Major).Color("Red").Add();

}).Add();

})

)

Execute the above code to render the following output.

{{ '![C:/Users/karthigeyan/Desktop/sa.png](Ticks_images/Ticks_img1.png)' | markdownify }}
{:.image }




### Tick Customization

* Height and width of the ticks can be applied by using the properties height and width. You can customize ticks with the properties such as angle, color, etc. angle attribute is used to display the labels in the specified angles and color attribute is used to display the labels in specified color. Ticks are two types such as major and minor.
* Major type ticks are for major interval values and minor type ticks are for minor interval values.You can position ticks with the help of two properties such as distanceFromScale and placement. distanceFromScale property defines the distance between the scale and ticks.  Placement property is used to locate the ticks with respect to scale either inside the scale or outside the scale or along the scale. It is an enumerable data type.



[View]

// For Circular Gauge rendering

@(Html.EJ().CircularGauge("circulargauge")

.Scales(sc1 =>

{

sc1.Ticks(tc =>

{

// For setting tick1

tc.Type(CircularTickTypes.Major).Color("Red").Add();

// For setting tick2

tc.Type(CircularTickTypes.Minor)

// For setting tick color

.Color("Yellow")

// For setting tick height

.Height(8)

// For setting tick placement

.Placement(TickPlacement.Near)

// For setting tick distance from scale

.DistanceFromScale(5).Add();

}).Add();

})

)


Execute the above code to render the following output.

{{ '![](Ticks_images/Ticks_img2.png)' | markdownify }}
{:.image }






