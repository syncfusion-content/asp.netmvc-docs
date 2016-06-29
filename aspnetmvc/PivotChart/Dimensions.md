---
layout: post
title: Dimensions | PivotChart | ASP.NET MVC | Syncfusion
description: dimensions
platform: ejmvc
control: PivotChart
documentation: ug
---

#Dimensions

##Set size in percentage

You can customize the PivotChart dimension by setting the width and height of the widget in percentage.

{% highlight CSHTML %}

//Set size to Chart container
@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("~/wcf/RelationalChartService.svc")).Size(size => size.Height("80%").Width("80%"))

{% endhighlight %}

##Set size in pixels

You can customize the PivotChart dimension by setting the width and height of the widget in pixels.

{% highlight CSHTML %}

//Set size to Chart container
@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("~/wcf/RelationalChartService.svc")).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

![](Dimensions_images/Dimensions.png) 

##Responsive

PivotChart widget supports responsive rendering based on the target device (desktop & tablet) resolution. It supports resolution upto 1024x600. You can enable responsiveness in PivotChart by setting `isResponsive` property to true.

{% highlight CSHTML %}

//Enable responsiveness to change the Chart size dynamically.
@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("~/wcf/RelationalChartService.svc")).Size(size => size.Height("460px").Width("950px")).IsResponsive(true)

{% endhighlight %}

![](Dimensions_images/NormalView.png)

_Normal View_

![](Dimensions_images/ResponsiveView.png)

_ResponsiveView_