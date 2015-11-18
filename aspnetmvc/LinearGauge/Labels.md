---
layout: post
title: Labels | lineargauge | ASP.NET MVC | Syncfusion
description: labels
platform: ejmvc
control: lineargauge
documentation: ug
---

# Labels

Labels are units that are used to display the values in the scales. You can customize Labels with the properties like angle, color, font, opacity, etc.

## Adding label collection 

Label collection can be directly added to the scale object. Refer the following code example to add label collection in a gauge.

{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1").EnableAnimation(false)

.Value(40)

//Adding frame object

.Frame(fr=>fr.InnerWidth(8).OuterWidth(10)

.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_dark1.png"))



//Adding scale collection

.Scales(sc => {

    sc.Width(0).Border(bor => bor.Color("transparent").Width(0))

    .ShowBarPointers(true).ShowMarkerPointers(false).ShowCustomLabels(true)



    //Adding bar pointer collection

    .BarPointers(bp =>

    {

        bp.Width(10).BarPointerDistanceFromScale(13).Add();

    })



    //Adding label collection

    .Labels(lbl => { lbl.TextColor("White").Add(); })



    //Adding tick collection

    .Ticks(tic =>

    {

        tic.Type(TickType.MajorInterval).Width(2).Color("#8C8C8C")

        .DistanceFromScale(ds => ds.X(7).Y(0)).Add();

        tic.Type(TickType.MinorInterval).Width(1).Color("#8C8C8C")

        .DistanceFromScale(ds => ds.X(7).Y(0)).Height(6).Add();

    }).Add();

}))

{% endhighlight %}

Execute the above code to render the following output.

![](Labels_images/Labels_img1.png)



## Label Customization

### Appearance

* Theattribute angle is used to display the labels in the specified angles and color attribute is used to display the labels in specified color. You can adjust the opacity of the label with the property opacity and the values of it lies between 0 and 1.The includeFirstValue is a special property by enabling this property, the first value of the label is not rendered.
* Font option is also available on the labels. The basic three properties of fonts such as size, family and style can be achieved by size, fontStyle and fontFamily. Labels are two types such as major and minor.Major type labels are for major interval values and minor type labels are for minor interval values.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1").EnableAnimation(false)

.Value(40)



//Adding frame object

.Frame(fr=>fr.InnerWidth(8).OuterWidth(10)

.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light.png"))



//Adding scale collection

.Scales(sc => {

sc.Width(0).Border(bor => bor.Color("transparent").Width(0))

.ShowBarPointers(true).ShowMarkerPointers(false).ShowCustomLabels(true)



//Adding bar pointer collection

.BarPointers(bp =>

{

bp.Width(10).BarPointerDistanceFromScale(13).Add();

})



//Adding label collection

.Labels(lbl => { lbl.TextColor("Red").Angle(10).Opacity(0.5)

.Font(fon=>fon.Size("12px").FontStyle("Arial").FontFamily("Bold"))

.IncludeFirstValue(false).Add(); })



//Adding tick collection

.Ticks(tic =>

{

tic.Type(TickType.MajorInterval).Width(2).Color("#8C8C8C")

.DistanceFromScale(ds => ds.X(7).Y(0)).Add();

tic.Type(TickType.MinorInterval).Width(1).Color("#8C8C8C")

.DistanceFromScale(ds => ds.X(7).Y(0)).Height(6).Add();

}).Add();

}))

{% endhighlight %}

Execute the above code to render the following output.


![](Labels_images/Labels_img2.png)



## Unit text and Positioning

* The unitText property is used to add some text along with the labels. For example, in speedometer, you need to mention the units in kmph. You can also add the unit text in front of the labels. To achieve this use the enumerable property unitTextPosition. 
* Labels can be positioned with the help of two properties such as distanceFromScale and placement. distanceFromScale property defines the distance between the scale and labels. Placement property is used to locate the labels with respect to scale either inside the scale or outside the scale or along the scale. It is an enumerable data type.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1").EnableAnimation(false)

.Value(31).Width(600).Height(250).Theme(Themes.FlatLight).Orientation(Orientation.Horizontal)

.LabelColor("Black").EnableResize(true)

//Adding frame object

.Frame(fr=>fr.InnerWidth(8).OuterWidth(10)

.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light1.png"))



//Adding scale collection

.Scales(sc => {

    sc.Width(5).Border(bor => bor.Color("#AEC75F").Width(2)).BackgroundColor("White")

    .MajorIntervalValue(25).MinorIntervalValue(5)

    .Type(ScaleType.RoundedRectangle).Direction(Directions.Clockwise)

    .ShowBarPointers(true).ShowMarkerPointers(false).ShowCustomLabels(true)



    //Adding bar pointer collection

    .BarPointers(bp =>

    {

        bp.Width(4).BarPointerBackgroundColor("Red").Add();

    })



    //Adding label collection

    .Labels(lbl => { lbl.Angle(90).DistanceFromScale(dc =>

    dc.X(0).Y(60)).UnitText("%").Add(); })



    //Adding tick collection

    .Ticks(tic =>

    {

        tic.Type(TickType.MajorInterval).Width(2).Color("#8C8C8C")

        .DistanceFromScale(ds => ds.X(25).Y(0)).Add();

        tic.Type(TickType.MinorInterval).Width(1).Color("#8C8C8C")

        .DistanceFromScale(ds => ds.X(25).Y(0)).Height(6).Add();

    })



    //Adding custom label collection

    .CustomLabels(cl => { cl.Value("Download in Progress")

    .Position(pos => pos.X(53).Y(20)).Add(); }).Add();

}))

{% endhighlight %}

Execute the above code to render the following output.


![](Labels_images/Labels_img3.png)



