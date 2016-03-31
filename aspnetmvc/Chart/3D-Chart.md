---
layout: post
title: 3D Chart | Chart | ASP.NET MVC | Syncfusion
description: 3d chart
platform: ejmvc
control: Chart
documentation: ug
---

# 3D Chart

Essential 3D Chart for ASP.NET MVC allows you to view 8 chart types in 3D view such as Bar, StackingBar, StackingBar100, Column, Stacked Column, 100% Stacked Column, Pie, Doughnut.


## 3D Column Chart

For rendering a 3D Column Chart, specify the series **Type** as **Column** in the chart series and set **Enable3D** option as **True** in the chart.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

       .Series(sr => { sr.Type(SeriesType.Column).Add(); })
    
       // Enable 3D Chart
       .Enable3D(true)
        // ...
    )


{% endhighlight %}

![](3D-Chart_images/3D-Chart_img1.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/column3d) here to view the Column 3DChart online demo sample.


## 3D Bar Chart

You can create a 3D Bar Chart by setting the series **Type** as **Bar** in the chart series and enable Enable3D option in the chart.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

       .Series(sr => { sr.Type(SeriesType.Bar).Add(); })
    
       // Enable 3D Chart
       .Enable3D(true)
        // ...
    )


{% endhighlight %}

![](3D-Chart_images/3D-Chart_img2.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/bar3d) here to view the Bar 3DChart online demo sample.


## 3D Stacked Column Chart

You can create a 3D Stacked Column Chart by setting the series **Type** as **StackingColumn** in the chart series and enable Enable3D option in the chart.

{% highlight cshtml %}

  @(Html.EJ().Chart("chartContainer")

    .Series(sr => { 
        //Add First Series
        sr.Type(SeriesType.StackingColumn).Add();
        //Add Second Series
        sr.Type(SeriesType.StackingColumn).Add();})
    // Enable 3D Chart
    .Enable3D(true)
    // ...
    )


{% endhighlight %}

![](3D-Chart_images/3D-Chart_img3.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/stackingcolumn3d) here to view the Stacked Column 3DChart online demo sample.

## 3D 100% Stacked Column Chart


100% Stacking Column 3DChart is rendered by specifying the series **Type** as **StackingColumn100** in the chart series and enable Enable3D option in the chart.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

    .Series(sr => { 
        //Add First Series
        sr.Type(SeriesType.StackingColumn100).Add();
        //Add Second Series
        sr.Type(SeriesType.StackingColumn100).Add();})
    // Enable 3D Chart
    .Enable3D(true)
    // ...
    )


{% endhighlight %}

![](3D-Chart_images/3D-Chart_img4.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/stackingcolumn1003d) here to view the 100% Stacked Column 3DChart online demo sample.


## 3D Stacked Bar Chart

To create Stacking Bar 3DChart, set the series **Type** as **StackingBar** in the chart series and enable Eenable3D option in the chart.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

    .Series(sr => { 
        //Add First Series
        sr.Type(SeriesType.StackingBar).Add();
        //Add Second Series
        sr.Type(SeriesType.StackingBar).Add();})
    // Enable 3D Chart
    .Enable3D(true)
    // ...
    )


{% endhighlight %}

![](3D-Chart_images/3D-Chart_img5.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/stackingbar3d) here to view the Stacked Bar 3DChart online demo sample.


## 3D 100% Stacked Bar Chart

You can create 100% Stacking Bar 3DChart by setting the series **Type** as **StackingBar100** in the chart series and enable Eenable3D option in chart.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

    .Series(sr => { 
        //Add First Series
        sr.Type(SeriesType.StackingBar100).Add();
        //Add Second Series
        sr.Type(SeriesType.StackingBar100).Add();})
    // Enable 3D Chart
    .Enable3D(true)
    // ...
    )


{% endhighlight %}

![](3D-Chart_images/3D-Chart_img6.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/stackingbar1003d) here to view the 100% Stacked Bar 3DChart online demo sample.


## 3D Pie Chart

To render the Pie Chart in 3D view, enable the **Enbel3D** option in the chart and set the series **Type** as **Pie** in the chart series.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

    .Series(sr => { 
        //Set chart type to series
        sr.Type(SeriesType.Pie).Add();})
    // Enable 3D Chart
    .Enable3D(true)
    // ...
    )


{% endhighlight %}

![](3D-Chart_images/3D-Chart_img7.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/pie3d) here to view the Pie 3DChart online demo sample.


## 3D Doughnut Chart

To render the Doughnut Chart in 3D view, enable the **Enbel3D** option in the chart and set the series **Type** as **Doughnut** in the chart series.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

    .Series(sr => { 
        //Set chart type to series
        sr.Type(SeriesType.Doughnut).Add();})
    // Enable 3D Chart
    .Enable3D(true)
    // ...
    )


{% endhighlight %}

![](3D-Chart_images/3D-Chart_img8.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/doughnut3d) here to view the Doughnut 3DChart online demo sample.


## Configure 3D Chart

### 3D View

To render the EjChart in 3D view, set the **Enable3D** option as **True** in the chart.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

    // Enable 3D Chart
    .Enable3D(true)
    // ...
    )


{% endhighlight %}


![](3D-Chart_images/3D-Chart_img9.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/column3d) here to view the 3DChart online demo sample.


### Placing Bar / Column kind of series side-by-side
 
 The **SideBySideSeriesPlacement** defines the appearance of the different sets of data on the 3D Chart. When this property is enabled, the data is displayed side by side, otherwise it is displayed along the depth of the axis.
 
 {% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

    // ...             
     //Enable SideBySideSeriesPlacement for 3DChart
     .SideBySideSeriesPlacement(true)
    // ...
    )


{% endhighlight %}


![](3D-Chart_images/3D-Chart_img10.png)


### Setting Axis Wall Size

In 3DChart, Cartesian axes lines are represented as walls and it defines the width of the 3D wall. 3D Pie and Doughnut Chart does not support **WallSize** because they don’t have axes.  

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

    // ...             
     //Change 3DChart axis wall size
     .WallSize(10)
    // ...
    )


{% endhighlight %}


![](3D-Chart_images/3D-Chart_img11.png)


### 3D Depth

By using the **Depth** property, you can view the 3D Chart from the front view of the series to the background wall.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

    // ...             
     //Change 3DChart depth value
     .Depth(120)
    // ...
    )


{% endhighlight %}


![](3D-Chart_images/3D-Chart_img12.png)


### Rotating and Tilting 3D Chart

To spin the 3D Chart on mouse dragging, enable **EnableRotation** option in the chart. The **Tilt** property specifies the angle of the slope of the 3D Chart. The positive and negative values are declared to the side where the slope is present. The **Rotation** option is used to rotate the 3D chart towards left or right side of the chart. The direction of the chart depends upon the positive and negative values of the angle.  

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

    // ...             
     //Change 3DChart tilt value
     .Tilt(10)
     //Enable 3DChart  rotation  on mouse dragging 
     .EnableRotation(true)
     //Change 3DChart rotation on chart load 
     .Rotation(40)
    // ...
    )


{% endhighlight %}


![](3D-Chart_images/3D-Chart_img13.png)


### PerspectiveAngle	

The **PerspectiveAngle** specifies the appearance of the height, width, depth and wall of the 3D Chart. When the PerspectiveAngle is decreased, the 3D object appears very close to the viewer. But when it is increased, the 3D object appears far away from the viewer. 

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

    // ...             
     //Change 3DChart perspective angle
     .PerspectiveAngle(150)
    // ...
  )


{% endhighlight %}


![](3D-Chart_images/3D-Chart_img14.png)
