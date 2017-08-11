---
layout: post
title: Chart size |Chart  | ASP.NET MVC | Syncfusion
description: Learn how to set Chart size and make it responsive. 
platform: ejmvc
control: Chart
documentation: ug
---

# Chart Dimensions

You can set the size of the chart directly on the chart or to the container of the chart. When you do not specify the size, it takes 450px as the height and window size as its width, by default. 

## Set size for the container

You can customize the chart dimension by setting the width and height for the container element. 

{% highlight cshtml %}


 <div id="container" style="width:820px; height:500px;">
     @(Html.EJ().Chart("chartContainer")

                    // ...
      )
  </div>


{% endhighlight %}


## Set size in pixels

You can also set the chart dimension by using the **Size** property of the chart. 

{% highlight cshtml %}


    @(Html.EJ().Chart("chartContainer")

            // ...
         
           //Set size to chart container
           .Size(size=>size.Height("450").Width("600"))
    )


{% endhighlight %}

![](Chart-Dimensions_images/Chart-Dimensions_img1.png)


## Setting size relative to the container size

You can specify the chart size in percentage by using the Size property. The chart gets its dimension with respect to its container.

{% highlight cshtml %}

 <div id="container" style="width:700px; height:500px">
    @(Html.EJ().Chart("chartContainer")

           // ...
         
           //Set size to chart container
           .Size(size=>size.Height("90%").Width("80%"))
     )
  </div>


{% endhighlight %}

![](Chart-Dimensions_images/Chart-Dimensions_img2.png)


## Responsive chart

To resize the Chart when the browser or the chart container is resized, set the **IsResponsive** property to **True**, where the chart adapts to the changes in size of the container.

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...
         
     //Enable IsResponsive to change the chart size dynamically.
     .IsResponsive(true)
 )

{% endhighlight %} 
