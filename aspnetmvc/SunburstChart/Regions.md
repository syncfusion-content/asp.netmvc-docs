---
layout: post
title: Sunburst elements 
description: Learn how to customize the sunburst segments 
platform: aspnetmvc
control: SunburstChart
documentation: ug
---
 
# Sunburst Elements

The Sunburst region represents the entire chart and all its elements. It includes all the chart elements like Legend, DataLabel, Levels etc. The major properties of the Sunburst Chart are as follows

**datasource** – Provides the data that are used to generate the chart.
**valueMemberPath**- Property based on the which the data segments are rendered in the chart 
**legend** – displays the legend of the Sunburst Chart
**levels**- displays the hierarchical levels for the chart 
**datalabel**– displays the datalabels for the Sunburst Chart

## Start and End Angle
Start and End Angle

You can change the start and end angle of Sunburst chart using **StartAngle** and **EndAngle** property as shown in below code

{% highlight js %}

@(Html.EJ().SunburstChart("chartContainer")

       .StartAngle(-90)
       .EndAngle(90)
 )

{% endhighlight %}

## Sunburst Radius

 The Radius of the Sunburst chart can be customized by using the **Radius** property. The default value of radius is 1 and its value ranges between 0 and 1 

{% highlight js %}

@(Html.EJ().SunburstChart("chartContainer")

       .Radius(0.8)
      
 )

{% endhighlight %}

![](Regions_images/Regions_img1.png);

 ## Sunburst Inner  Radius
 
 The Inner Radius of the Sunburst chart can be customized by using the **InnerRadius** property. The default value of innerRadius is 0.4 and its value ranges between 0 and 1 

{% highlight js %}


@(Html.EJ().SunburstChart("chartContainer")

       .InnerRadius(0.5)
      
 )

{% endhighlight %}

![](Regions_images/Regions_img2.png);




