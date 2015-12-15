---
layout: post
title: Responsive Layout | OLAPClient | ASP.NET MVC | Syncfusion
description: responsive layout
platform: ejmvc
control: OLAPClient
documentation: ug
---

# Responsive Layout

OlapClient widget supports responsive rendering based on the target device (desktop & tablet) resolution. It supports resolution upto 1024x600. You can enable responsiveness in OlapClient by setting `IsResponsive` property to true.


{% highlight CSHTML %}

@Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title("OLAP Browser").IsResponsive(true)

{% endhighlight %}

![](Responsive-Layout_images/responsive.png)
