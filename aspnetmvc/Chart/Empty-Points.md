---
layout: post
title: Empty Points | Chart | ASP.NET MVC | Syncfusion
description: empty points
platform: ejmvc
control: Chart
documentation: ug
---

# Empty Points

The data that is passed to the Chart can have null or undefined values that are considered as empty points. Series type like line, spline, area, spline area, stepline, step area, column, bar, bubble, scatter, hilo, hiloopenclose, candle, range column and stacking series having empty point support. 
{% highlight CSHTML %}

@(Html.EJ().Chart("chartcontainer")

// ...

   .Series(sr =>

    {

sr.Points(pt =>

{

	  pt.X(1).Y(210).Add(); 

         pt.X(2).Y(150).Add(); 

         pt.X(3).Y(200).Add(); 

         pt.X(4).Y(null).Add(); 

         pt.X(5).Y(170).Add(); 

         pt.X(6).Y(230).Add(); 

         pt.X(7).Y(120).Add(); 

        }).Name("Course").Type(SeriesType.Column).Add();

     })

// ...

    )

{% endhighlight  %}

![](Empty-Points_images/Empty-Points_img1.png)

Chart with Empty Points
{:.caption}
