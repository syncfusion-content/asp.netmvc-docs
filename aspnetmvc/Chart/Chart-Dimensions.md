---
layout: post
title: Chart Dimensions | Chart | ASP.NET MVC | Syncfusion
description: chart dimensions
platform: ejmvc
control: Chart
documentation: ug
---

# Chart Dimensions

In this section you can learn how to change the Chart dimensions. You can change the Chart height and width in terms of pixels and percentage with the Size property. When size is specified, the Chart remains to that specific size irrespective of the size of the container. You can always resize the Chart when the browser or Chart container is resized by setting CanResize property to true, where the Chart adapts to the changes in size of the container. By default, Chart height will be 450px and Chart width takes the container width as default value.

## Setting dimension in pixel values:

You can specify the width and height in pixels to change the dimension of the Chart. 

## Setting size 
{% highlight js %}

@(Html.EJ().Chart("chartcontainer")

         .Size(sz=>sz.Height("600").Width("800"))

         .CanResize(true)

         )

{% endhighlight  %}

In the above code, the width is set as 800px and height as 600px that displays the following Chart with the dimension 800*600.



![](Chart-Dimensions_images/Chart-Dimensions_img1.png)

Chart with the dimension 800*600
{:.caption}

## Setting dimension in percentage values:

You can also set the width and height of the Chart in percentage. The Chart gets its dimension with respect to its container size.

Setting size in percentage
{% highlight js %}


@(Html.EJ().Chart("chartcontainer")

         .Size(sz=>sz.Height("80%").Width("90%"))

         )

{% endhighlight  %}

![](Chart-Dimensions_images/Chart-Dimensions_img2.png)

Chart with dimension
{:.caption}
