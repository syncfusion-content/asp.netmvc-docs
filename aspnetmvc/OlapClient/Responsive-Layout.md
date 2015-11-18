---
layout: post
title: Responsive Layout | OLAPClient | ASP.NET MVC | Syncfusion
description: responsive layout
platform: ejmvc
control: OLAPClient
documentation: ug
---

# Responsive Layout

Responsive layout is aimed at crafting sites to provide an optimal viewing experience - easy reading. It also provides navigation with a minimum of resizing, panning, and scrolling across a wide range of devices from tablet to desktop. To get responsive layout for OLAP Client, enable IsResponsive API to true. By using this feature, you can achieve an effective view of the OLAP Client control in all devices including desktops, tablets, mobiles, etc. 



{% highlight CSHTML %}

@using Syncfusion.JavaScript;

@using Syncfusion.JavaScript.Olap;

@Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/wcf/OlapClientService.svc")).Title("OLAP Browser").ClientSideEvents(oEve => { oEve.ChartLoad("setChartProperties"); }).IsResponsive(true)

<script>

    function setChartProperties(args) {

        this.model.load = "loadTheme"

    }

</script>

{% endhighlight %}

![](Responsive-Layout_images/Responsive-Layout_img1.png)

![](Responsive-Layout_images/Responsive-Layout_img2.png)

![](Responsive-Layout_images/Responsive-Layout_img3.png)

![](Responsive-Layout_images/Responsive-Layout_img4.png)