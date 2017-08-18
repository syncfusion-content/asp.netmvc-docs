---
layout: post
title: Appearance and Styling | Rotator | ASP.NET MVC | Syncfusion
description: appearance and styling
platform: ejmvc
control: Rotator
documentation: ug
---

# Appearance and Styling

## Adjusting rotator item size

### SlideWidth

This property sets the Width of a Rotator Item. The value set to this property is string or number.

{% highlight CSHTML %}

@Html.EJ().Rotator("sliderContent").Datasource((IEnumerable<Localdata>)ViewBag.datasource)
.RotatorFields(t => t.Text("Text").Url("Url"))
.SlideWidth("600px").SlideHeight("350px")

{% endhighlight %}

### SlideHeight

This property sets the Height of a Rotator Item. The value set to this property is string or number.

{% highlight CSHTML %}

@Html.EJ().Rotator("sliderContent").Datasource((IEnumerable<Localdata>)ViewBag.datasource)
.RotatorFields(t => t.Text("Text").Url("Url"))
.SlideWidth("600px").SlideHeight("350px")

{% endhighlight %}