---
layout: post
title: Custom Label | PivotGauge | ASP.NET MVC | Syncfusion
description: This document illustrates that how to enable custom labels and its functionalities in ASP.NET MVC  PivotGauge control
platform: ejmvc
control: PivotGauge
documentation: ug
---

# Custom labels

## Adding Custom Label Collection

You can apply custom custom label Collection by using `CustomLabels` which can be directly added to the scales option within the PivotGauge control.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").Scales(scales => {
        scales.CustomLabels(customLabels => { customLabels.Position(position => position.X(180).Y(290)).Add(); }).Add();
    })

{% endhighlight  %}

## Appearance Customization

The appearance of the custom labels can be customized through the following properties.

* **Position** – used to set the position of the labels.
* **Font** – sets the font size, font style and font family of the label text.
* **Color** – sets the color of the label text.
* **TextAngle** – rotates the label to a specified angle. By default, the value is 0.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").Scales(scales => {
        scales.CustomLabels(customLabels =>
        {
            customLabels.Position(position => position.X(180).Y(320)).Font(font => font.Size("12px").FontFamily("Segoe UI").FontStyle("Normal")).Color("blue").TextAngle(20).Add();
        }).Add();
    })

{% endhighlight  %}

![Custom label customization in ASP NET MVC pivot gauge control](Custom-Label_images/AppearanceCustomization.png) 

## Multiple Custom Labels

Multiple ranges can be added in `CustomLabels` to the scales option within the PivotGauge control.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").Scales(scales => {
        scales.CustomLabels(customLabels =>
        {
            customLabels.Position(position => position.X(180).Y(150)).Font(font => font.Size("12px").FontFamily("Segoe UI").FontStyle("Normal")).Color("red").Add();
            customLabels.Position(position => position.X(180).Y(320)).Font(font => font.Size("10px").FontFamily("Segoe UI").FontStyle("Normal")).Color("green").Add();
            customLabels.Position(position => position.X(180).Y(290)).Font(font => font.Size("10px").FontFamily("Segoe UI").FontStyle("Normal")).Color("blue").Add();
        }).Add();
    })

{% endhighlight  %}

![Multiple custom labels in ASP NET MVC pivot gauge control](Custom-Label_images/MultipleCustomLabels.png) 
