---
layout: post
title: Using Essential ASP.NET MVC Chart in real-time scenario 
description: Learn how to update the chart dynamically with real-time data. 
platform: ejmvc
control: Chart
documentation: ug
---

# Real-Time Chart 

Chart can be updated dynamically with the real time data. Whenever you add a point or remove a point from the dataSource, you can call the **redraw** method to request the chart to redraw its content.    

N> You can get the chart **instance** using instance method.

{% highlight cshtml %}
     
@(Html.EJ().Chart("chartContainer")

      // ...
        //Rendering empty Chart without data
      .Series(sr =>
      {
          sr.Points(pt =>
          {
              
          }).Add();
      })
        //...
 )
 
 {% endhighlight %}
 
 
{% highlight js %}

    //Using set interval to update chart dynamically
    window.setInterval(updateChart, 200);

    //Function that updates chart dynamically
    function updateChart(){

        //Creating chart instance
        var chart =  $("#chartContainer").ejChart("instance");      
        
        if (chart.model.series[0].points.length > 10)
               chart.model.series[0].points.splice(0, 1);
        
        var point = chart.model.series[0].points;
        var xValue = point.length > 0 ? point[point.length - 1].x + 1 : 1;
        point[point.length] = { x:  xValue, y: getRandomNumber( 1000 ) }
                
        //Update Chart dynamically using redraw option
        //chart.redraw() can also be used here instead of redraw option
        $("#chartContainer").ejChart("redraw");      
       }


{% endhighlight %}

[Click](http://mvc.syncfusion.com/demos/web/chart/live) here to view the online demo sample for real-time Chart.


