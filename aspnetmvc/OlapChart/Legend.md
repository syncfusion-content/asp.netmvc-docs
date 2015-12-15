---
layout: post
title: Legend | OLAPChart | ASP.NET MVC | Syncfusion
description: legend
platform: ejmvc
control: OLAPChart
documentation: ug
---

#Legend

##Legend Visibility

You can enable or disable legend using the `Visible` property inside the `legend` object. By default, legend is enabled in OlapChart.

{% highlight CSHTML %}

//Legend Visibility set as true
@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px")).Legend(legend => legend.Visible(true))

{% endhighlight %}

![](Legend_images/Legend_img1.png) 

##Legend Shape
You can customize the legend `Shape` in OlapChart widget to rectangle, circle, cross, diamond, pentagon, hexagon, star, ellipse, triangle etc. Default value of legend shape is “Rectangle”.

{% highlight CSHTML %}

//Applying legend shape
@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px")).Legend(legend => legend.Visible(true).Shape(ChartShape.Star))

{% endhighlight %}

![](Legend_images/Legend_img2.png) 

##Legend Position
By using the `Position` property, you can place the legend at top, bottom, left or right of the OlapChart. Default value of legend position is “bottom”.

{% highlight CSHTML %}

//Place the legend at top of the Chart
@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px")).Legend(legend => legend.Visible(true).Shape(ChartShape.Star).Position(LegendPosition.Top))

{% endhighlight %}

![](Legend_images/Legend_img3.png) 

##Legend Title
To add the legend title, you have to specify the title text in `title.Text` property.

{% highlight CSHTML %}

//Add title to the Chart legend
@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px")).Legend(legend => legend.Visible(true).Title(title => title.Text("Countries")))

{% endhighlight %}

![](Legend_images/Legend_img4.png) 

##Legend Alignment
You can align the legend to center, far and near based on its position in the Chart area using the `Alignment` option.
 
{% highlight CSHTML %}

//Aligning the legend near to the Chart
@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px")).Legend(legend => legend.Visible(true).Shape(ChartShape.Star).Alignment(TextAlignment.Near))

{% endhighlight %}

![](Legend_images/Legend_img5.png)

##Legend Items - Size and Border
By using the legend `ItemStyle.width`, `ItemStyle.height` and `ItemStyle.border` properties, you can change the legend items - size and border.

{% highlight CSHTML %}

//Changing legend items border, height and width
@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px")).Legend(legend => legend.Visible(true).ItemStyle(ItemSize => ItemSize.Border(border => border.Color("magenta").Width(1.5)).Height(12).Width(12)))

{% endhighlight %}

![](Legend_images/Legend_img6.png)
 
##Legend Border
By using the `Border` option in legend, you can customize border color and width.

{% highlight CSHTML %}

//Setting border color and width to legend
@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px")).Legend(legend => legend.Visible(true).Border(border => border.Color("red").Width(2)))

{% endhighlight %}

![](Legend_images/Legend_img7.png)

##Legend Text
By using the `Font` option, you can customize the font family, font style, font weight and size of the legend text. 

{% highlight CSHTML %}

///Customizing the legend text @Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px")).Legend(legend => legend.Visible(true).Font(font => font.FontFamily("Segoe UI").FontWeight(ChartFontWeight.Bold).FontStyle(ChartFontStyle.Italic).Size("13px")))

{% endhighlight %}

![](Legend_images/Legend_img8.png)