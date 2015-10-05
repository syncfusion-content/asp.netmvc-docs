---
layout: post
title: RTL Support | Rotator | ASP.NET MVC | Syncfusion
description: rtl support
platform: ejmvc
control: Rotator
documentation: ug
---

# RTL Support

EnableRTL feature supports to change the left-to-right alignment of the Rotator to right-to-left (RTL). (I.e.) Sets the Rotator to do its actions from right to left. The EnableRTL property sets the Rotator from right to left. The value set to this property is Boolean type.

{% highlight CSHTML %}

/ / Add this code in your CSHTML page and refer local data section for binding Rotator items.

@Html.EJ().Rotator("slidercontent").Datasource((IEnumerable<Localdata>)ViewBag.datasource)
.RotatorFields(t => t.Text("Text").Url("Url"))
.SlideWidth("600px").SlideHeight("350px")
.EnableRTL(true)

{% endhighlight %}