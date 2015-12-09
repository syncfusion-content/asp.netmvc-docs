---
layout: post
title: Title | OLAPChart | ASP.NET MVC | Syncfusion
description: title
platform: ejmvc
control: OLAPChart
documentation: ug
---

#Title

##Title Text

By using the `title.Text` property, you can add the title text for OlapChart.

{% highlight CSHTML %}

//Adding Chart title
@Html.EJ().Olap().OlapChart("OlapChart1").Title(title => title.Text("OlapChart in Essential Studio")).Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

![](/js/OlapChart/Title_images/Title_img1.png)

##Title Alignment
By using the `title.TextAlignment` property, you can align the OlapChart controls title text to center, far or near.

{% highlight CSHTML %}

//Change title text alignment
@Html.EJ().Olap().OlapChart("OlapChart1").Title(title => title.Text("OlapChart in Essential Studio").TextAlignment(TextAlignment.Near)
).Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

![](/js/OlapChart/Title_images/Title_img2.png)

##Title Customization

By using the `Title` property, you can add the title text for X-axis and Y-axis. Also title text can be customized by using the `Text` and `Font` properties. On setting `EnableTrim` to true, title text could be trimmed based on its length.

{% highlight CSHTML %}

//Customizing axis title
@Html.EJ().Olap().OlapChart("OlapChart1").PrimaryXAxis(primaryX => primaryX.Title(title => title.Text("Fiscal Year").Font(font=> font.Size("16px").FontWeight(ChartFontWeight.Bold).FontStyle(ChartFontStyle.Italic).Color("grey")))).Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

![](/js/OlapChart/Title_images/Title_img3.png) 

