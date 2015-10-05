---
layout: post
title: Custom labels | lineargauge | ASP.NET MVC | Syncfusion
description: custom labels
platform: ejmvc
control: lineargauge
documentation: ug
---

# Custom labels

Custom labels are the text that can paste in any location of the Linear Gauge. It is used to define the purpose of the gauge.

## Adding Custom label collection

Custom labels collection can be directly added to the scale object. Refer the following code to add custom labels collection in a Linear Gauge control.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1").EnableAnimation(false).LabelColor("Grey")

//Adding frame object

.Frame(fr=>fr.InnerWidth(8).OuterWidth(10)

.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light.png"))



//Adding scale collection

.Scales(sc => {

    sc.Width(0).Border(bor=>bor.Color("transparent").Width(0)).ShowMarkerPointers(false)

    .ShowBarPointers(true).ShowCustomLabels(true)

    .ShowBarPointers(true)



    //Adding bar pointer collection

    .BarPointers(bp =>

    {

        bp.Width(10).BarPointerBackgroundColor("#8BABFF")

        .BarPointerValue(91).BarPointerDistanceFromScale(30).Add();

    })



    //Adding marker pointer collection

    .MarkerPointers(mp => { mp.Width(10).Length(10).Value(60).Add(); })



    //Adding label collection

    .Labels(lbl => { lbl.DistanceFromScale(dc => dc.X(-25).Y(0)).Add(); })



    //Adding ticks collection

    .Ticks(tic =>

    {

        tic.Type(TickType.MajorInterval).Width(2).Color("#8c8c8c")

        .DistanceFromScale(dsc => dsc.X(-7).Y(0)).Add();

        tic.Type(TickType.MinorInterval).Color("#8c8c8c").Width(1)

        .Height(6).DistanceFromScale(dfs => dfs.X(-7).Y(0)).Add();

    })



    //Adding custom label collection

    .CustomLabels(cl => { cl.Value("Mathematics Mark").Position(pos =>

    pos.X(55).Y(97)).Add(); }).Add();

}))

{% endhighlight %}


Execute the above code to render the following output.

![](Custom-labels_images/Custom-labels_img1.png)



## Basic Customization

### Appearance

* You can customize custom labels using the properties like textAngle, color and font. The API textAngle is used to display the custom labels in the specified angles and color attribute is used to display the custom labels in specified color. You can use value attribute to set the text value in the custom labels. 
* To display the custom labels, set showCustomLabels as ‘true’. Font option is also available on the custom labels. The basic three properties of fonts such as size, family and style can be achieved by size, fontStyle and fontFamily. You can adjust the opacity of the label with the property opacity and the value of opacity lies between 0 and 1.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1").EnableAnimation(false)

.Height(500).Width(200).LabelColor("Grey")



//Adding frame object

.Frame(fr=>fr.InnerWidth(8).OuterWidth(10)

.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light.png"))



//Adding scale collection

.Scales(sc => {

    sc.Width(0).Border(bor=>bor.Color("transparent").Width(0)).ShowMarkerPointers(false)

    .ShowBarPointers(true).ShowCustomLabels(true)

    .ShowBarPointers(true)



    //Adding bar pointer collection

    .BarPointers(bp =>

    {

        bp.Width(10).BarPointerBackgroundColor("#8BABFF")

        .BarPointerValue(91).BarPointerDistanceFromScale(30).Add();

    })



    //Adding marker pointer  collection

    .MarkerPointers(mp => { mp.Width(10).Length(10).Value(60).Add(); })



    //Adding label collection

    .Labels(lbl => { lbl.DistanceFromScale(dc => dc.X(-25).Y(0)).Add(); })



    //Adding ticks collection

    .Ticks(tic =>

    {

        tic.Type(TickType.MajorInterval).Width(2).Color("#8c8c8c")

        .DistanceFromScale(dsc => dsc.X(-7).Y(0)).Add();

        tic.Type(TickType.MinorInterval).Color("#8c8c8c").Width(1)

        .Height(6).DistanceFromScale(dfs => dfs.X(-7).Y(0)).Add();

    })



    //Adding custom label collection

    .CustomLabels(cl => {

        cl.Value("Mathematics Mark")

        .TextAngle(30)

        .CustomLabelopacity(0.5)

        .Color("Red")

        .Position(pos => pos.X(55).Y(87)).Add();

    }).Add();

}))

{% endhighlight %}

Execute the above code to render the following output.

![](Custom-labels_images/Custom-labels_img2.png)



## Locating the Custom Labels

To set the location of the custom label in Linear Gauge, position property is used. You can position the custom labels in horizontal and vertical axis using X and Y axis respectively.



{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1").EnableAnimation(false)

.Height(500).Width(200).LabelColor("Grey")



//Adding frame object

.Frame(fr=>fr.InnerWidth(8).OuterWidth(10)

.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light.png"))



//Addingscale collection

.Scales(sc => {

    sc.Width(0).Border(bor=>bor.Color("transparent").Width(0)).ShowMarkerPointers(false)

    .ShowBarPointers(true).ShowCustomLabels(true)

    .ShowBarPointers(true)



    //Adding bar pointer collection

    .BarPointers(bp =>

    {

        bp.Width(10).BarPointerBackgroundColor("#8BABFF")

        .BarPointerValue(91).BarPointerDistanceFromScale(30).Add();

    })



    //Adding marker pointer collection

    .MarkerPointers(mp => { mp.Width(10).Length(10).Value(60).Add(); })



    //Adding label collection

    .Labels(lbl => { lbl.DistanceFromScale(dc => dc.X(-25).Y(0)).Add(); })



    //Adding ticks collection

    .Ticks(tic =>

    {

        tic.Type(TickType.MajorInterval).Width(2).Color("#8c8c8c")

        .DistanceFromScale(dsc => dsc.X(-7).Y(0)).Add();

        tic.Type(TickType.MinorInterval).Color("#8c8c8c").Width(1)

        .Height(6).DistanceFromScale(dfs => dfs.X(-7).Y(0)).Add();

    })



    //Adding custom label collection

    .CustomLabels(cl => {

    cl.Value("Mathematics Mark")

    .Position(pos => pos.X(55).Y(87)).Add();

    }).Add();

}))

{% endhighlight %}

Execute the above code to render the following output.

![](Custom-labels_images/Custom-labels_img3.png)



## Multiple Custom Labels

You can set multiple custom labels in a single Linear Gauge by adding an array of custom label objects. Refer the following code example for multiple custom label functionality.


{% highlight js %}

@(Html.EJ().LinearGauge("LinearGauge1").EnableAnimation(false)

.Height(500).Width(200).LabelColor("Grey")

//Adding frame object

.Frame(fr=>fr.InnerWidth(8).OuterWidth(10)

.BackgroundImageUrl("../Content/images/gauge/Gauge_linear_light.png"))



//Adding scale collection

.Scales(sc => {

    sc.Width(0).Border(bor=>bor.Color("transparent").Width(0)).ShowMarkerPointers(false)

    .ShowBarPointers(true).ShowCustomLabels(true)

    .ShowBarPointers(true)



    //Adding bar pointers

    .BarPointers(bp =>

    {

        bp.Width(10).BarPointerBackgroundColor("#8BABFF")

        .BarPointerValue(91).BarPointerDistanceFromScale(30).Add();

    })



    //Adding marker pointers

    .MarkerPointers(mp => { mp.Width(10).Length(10).Value(60).Add(); })



    //Adding label collection

    .Labels(lbl => { lbl.DistanceFromScale(dc => dc.X(-25).Y(0)).Add(); })



    //Adding ticks collection

    .Ticks(tic =>

    {

        tic.Type(TickType.MajorInterval).Width(2).Color("#8c8c8c")

        .DistanceFromScale(dsc => dsc.X(-7).Y(0)).Add();

        tic.Type(TickType.MinorInterval).Color("#8c8c8c").Width(1)

        .Height(6).DistanceFromScale(dfs => dfs.X(-7).Y(0)).Add();

    })

    //Adding custom labels

    .CustomLabels(cl => {

        //Adding custom label1

        cl.Value("Mathematics Mark")

        .Position(pos => pos.X(55).Y(87)).Color("Red").Add();

        //Adding custom label 2

        cl.Value("Marks in %")

        .Position(pos => pos.X(15).Y(57)).Color("Red").TextAngle(90).Add();

    }).Add();

}))

{% endhighlight %}

Execute the above code to render the following output.

![](Custom-labels_images/Custom-labels_img4.png)



