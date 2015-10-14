---
layout: post
title: Marker and Cross Hair | OLAPChart | ASP.NET MVC | Syncfusion
description: marker and cross hair 
platform: ejmvc
control: OLAPChart
documentation: ug
---

# Marker and Cross Hair 

Markers are the symbols that represent on the series of the Chart Area. Cross Hair helps you to view the value at mouse position or touch contact point.

## Real-time use of Cross Hair

You can view the information while moving the mouse pointer over the Chart Area with the help of CrossHair. For example, in a line chart you can get exact values of x and y axis while moving the mouse on Chart Area.



![](Marker-and-Cross-Hair_images/Marker-and-Cross-Hair_img1.png)



## Marker Shape Customization 

In OlapChart, you can customize the marker shape with different symbols like rectangle, circle, cross, diamond, pentagon, hexagon, star, ellipse, triangle etc.

{% highlight CSHTML %}

@Html.EJ().Olap().OlapChart("OlapChart1").Url("../wcf/OlapChartService.svc").CommonSeriesOptions(comm => 
{ comm.Type(SeriesType.Line).Tooltip(tool => { tool.Visible(true); }); }).Size(size => 
size.Height("460").Width("750")).ClientSideEvents(oEve => { oEve.SeriesRendering("onSeriesRenders"); })

{% endhighlight  %}

{% highlight CSHTML %}

<script type="text/javascript">

function onSeriesRenders(args) 
	{

	   for (var seriescount = 0; seriescount < this.model.series.length; seriescount++)

		   this.model.series[seriescount].marker.shape = "Triangle";

	}

</script>

{% endhighlight  %}



![](Marker-and-Cross-Hair_images/Marker-and-Cross-Hair_img2.png)

Marker Shape Customization
{:.caption}

## Cross Hair Customization 

In order to view the value at mouse position or touch contact point, you can use the crosshair property. You can customize the appearance using the following code example. 
{% highlight CSHTML %}

@Html.EJ().Olap().OlapChart("OlapChart1").Url("../wcf/OlapChartService.svc").PrimaryXAxis(PrimaryXAxis 
=>PrimaryXAxis.CrosshairLabel(CrosshairLabel =>CrosshairLabel.Visible(true))).PrimaryYAxis(PrimaryYAxis
=>PrimaryYAxis.CrosshairLabel(CrosshairLabel =>CrosshairLabel.Visible(true))).CrossHair(CrossHair 
=>CrossHair.Visible(true).Type(CrosshairType.Crosshair).Line(line =>line.Width(2).Color("red")).Marker(marker 
=>marker.Size(size =>size.Height(5).Width(5))))


{% endhighlight  %}

![](Marker-and-Cross-Hair_images/Marker-and-Cross-Hair_img3.png)
{:.caption}


