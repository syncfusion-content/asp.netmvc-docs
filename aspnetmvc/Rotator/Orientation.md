---
layout: post
title: Orientation | Rotator | ASP.NET MVC | Syncfusion
description: orientation
platform: ejmvc
control: Rotator
documentation: ug
---

# Orientation

The Rotator control supports both vertical and horizontal orientations allowing it to fit into any scenario. The Orientation property defines the Orientation where the control is rendered. The value set to this property is enum or string type. It accepts the following values.

* ej.Orientation.Horizontal or “Horizontal”
* ej.Orientation.Vertical  or “Vertical”

The following steps explain you how to set Orientation for the Rotator.

## Horizontal

This property sets the Rotator in HorizontalOrientation. You can refer the following steps to set Horizontal Orientation for Rotator control. In Rotator control, the Default value of Orientation is Horizontal. 

1. In View, create ul-li list of Rotator items and invoke the Rotator helper.
2. Add the following script in your CSHTML page.

{% highlight CSHTML %}

// Add this code in your CSHTML page and refer local data section for binding Rotator items.

@Html.EJ().Rotator("slidercontent").Datasource((IEnumerable<Localdata>)ViewBag.datasource)
.RotatorFields(t => t.Text("Text").Url("Url"))
.SlideWidth("600px")
.SlideHeight("350px")
.Orientation(Syncfusion.JavaScript.Orientation.Horizontal)

{% endhighlight %}

## Vertical

This property sets the Rotator in vertical orientation. You can refer the following steps to set VerticalOrientation for Rotator control.

1. Create ul-li list of Rotator items and invoke the Rotator helper.
2. Add the following script in your CSHTML page.


{% highlight CSHTML %}

// Add this code in your CSHTML page and refer local data section for binding Rotator items.

@Html.EJ().Rotator("slidercontent").Datasource((IEnumerable<Localdata>)ViewBag.datasource)
.RotatorFields(t => t.Text("Text").Url("Url"))
.SlideWidth("600px").SlideHeight("350px")
.Orientation(Syncfusion.JavaScript.Orientation.Vertical)

{% endhighlight %}