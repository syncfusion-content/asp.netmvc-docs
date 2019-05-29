---
layout: post
title: Chart Types | PivotChart | ASP.NET MVC | Syncfusion
description: This document illustrates that how to define chart types and its customization in ASP.NET MVC PivotChart control
platform: ejmvc
control: PivotChart
documentation: ug
---

# Chart Types

Essential **PivotChart MVC** supports 18 different types of chart as follows:


* Column
* Stacking Column
* Bar
* Stacking Bar
* Pie
* Pyramid
* Funnel
* Line
* Step Line
* Spline
* Area
* Step Area
* Spline Area
* Stacking Area
* Doughnut
* Scatter
* Bubble
* WaterFall


## Column Chart


**Column Chart** is the most commonly used chart type. It uses vertical bars (called columns) to display different values of one or more items. Points from adjacent series are drawn as bars next to each other. It is used to compare the frequency, count, total or average of data in different categories. It is ideal to show the variations in the value of an item over a period of time.

{% highlight CSHTML %}


@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.Column); }).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

The following screenshot displays a **Column Chart**.



![ASP NET MVC column chart control](Chart-Types_images/Chart-Types_img1.png)



## Stacking Column Chart

**Stacking Column** Chart is similar to column charts except the Y-values. These Y-values stack on top of each other in a specified series order. This helps to visualize the relationship of parts to whole across categories.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.StackingColumn); }).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}



The following screenshot displays the **stacking Column Chart**.

![ASP NET MVC stacking column chart control](Chart-Types_images/Chart-Types_img2.png)


## Bar Chart

The **Bar Chart** displays horizontal bars for each point in the series and points from adjacent series. Bar charts are used to compare values across categories, for displaying the variations in the value of an item over time or for comparing the values of several items at a single point in time.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.Bar); }).Size(size => size.Height("460px").Width("950px"))


{% endhighlight %}


The following screenshot displays a **Bar Chart**.


![ASP NET MVC bar chart control](Chart-Types_images/Chart-Types_img3.png)



## Stacking Bar Chart

**Stacking Bar Chart** is a regular **bar** chart with the X-values stacked on top of each other in the specified series order.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.StackingBar); }).Size(size => size.Height("460px").Width("950px"))


{% endhighlight %}



The following screenshot displays the **Stacking Bar Chart**.

![ASP NET MVC stacking bar chart control](Chart-Types_images/Chart-Types_img4.png)



## Pie Chart

A **Pie chart** is used to summarize a set of categorical data or displaying different values of a given variable (e.g., percentage distribution). This type of chart is a circle divided into a series of segments. Each segment represents a particular category.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.Pie); }).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}


The following screenshot displays a **Pie Chart**.



![ASP NET MVC pie chart control](Chart-Types_images/Chart-Types_img5.png)



## Pyramid Chart

The **Pyramid Chart** type displays the data in the form of a triangle. It helps you to visualize data in a hierarchical structure without any axes.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.Pyramid); }).Size(size => size.Height("460px").Width("950px"))


{% endhighlight %}


The following screen shot displays the **Pyramid Chart**.


![ASP NET MVC pyramid chart control](Chart-Types_images/Chart-Types_img6.png)


## Funnel Chart

The **Funnel Chart**  type displays the data in the form of an inverted triangle. It helps you to visualize data in a hierarchical structure without any axes.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.Funnel); }).Size(size => size.Height("460px").Width("950px"))


{% endhighlight %}


The following screen shot displays the **Funnel Chart**.


![ASP NET MVC funnel chart control](Chart-Types_images/Chart-Types_img14.png)



## Line Chart

The **Line Chart** joins the data points on a plot using straight lines that show trends in data at equal intervals.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.Line); }).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}


The following screenshot displays the **Line Chart**.

![ASP NET MVC line chart control](Chart-Types_images/Chart-Types_img7.png)



## Step Line Chart

**Step Line Chart** uses horizontal and vertical lines to connect the data points resulting in a step like progression.

{% highlight CSHTML %}


@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.StepLine); }).Size(size => size.Height("460px").Width("950px"))


{% endhighlight %}


The following screenshot displays the **Step Line Chart**.

![ASP NET MVC step line chart control](Chart-Types_images/Chart-Types_img8.png)



## Spline Chart

The **Spline Chart** is similar to line charts except it connects different data points using curve lines instead of straight lines.


{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.Spline); }).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}


The following screenshot displays the **Spline Chart**.

![ASP NET MVC spline chart control](Chart-Types_images/Chart-Types_img9.png)



## Area Chart

**Area Chart** emphasizes the degree of change of values over a period of time. Instead of rendering data as discrete bars or columns, an area chart renders it in a continuous ebb-and-flow pattern as defined against the y-axis.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.Area); }).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

The following screenshot displays the **Area Chart**.

![ASP NET MVC area chart control](Chart-Types_images/Chart-Types_img10.png)



## Step Area Chart

**Step Area** chart is similar to the regular area chart except for a straight line tracing the shortest path between the data points. The values are connected by continuous vertical and horizontal lines forming a step like progression.

{% highlight CSHTML %}


@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.StepArea); }).Size(size => size.Height("460px").Width("950px"))


{% endhighlight %}


The following screenshot displays a **Step Area Chart**.

![ASP NET MVC step area chart control](Chart-Types_images/Chart-Types_img11.png)



## Spline Area Chart

**Spline Area** chart is similar to Area Chart with the difference in which the data points of a series are connected. It connects each series of points by a smooth **spline curve**.


{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType. SplineArea); }).Size(size => size.Height("460px").Width("950px"))

{% endhighlight  %}

The following Screenshot displays a **Spline Area Chart**.

![ASP NET MVC spline area chart control](Chart-Types_images/Chart-Types_img12.png)



## Stacking Area Chart

**Stacking Area** chart is similar to regular area chart except the “Y-values”. These “Y-values” stack on top of each other in the specified series order. This helps to visualize the relationship of parts to whole across categories.


{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
 comm.Type(SeriesType.StackingArea); }).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}


The following screenshot displays a **Stacking Area Chart**.

![ASP NET MVC stacking area chart control](Chart-Types_images/Chart-Types_img13.png)

## Doughnut Chart

A **Doughnut chart** is also used to summarize a set of categorical data which possesses a doughnut like structure divided into a series of segments. Each segment represents a particular category.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
 comm.Type(SeriesType.Doughnut); }).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

The following screenshot displays a **Doughnut Chart**.

![ASP NET MVC doughnut chart control](Chart-Types_images/DoughnutChart.png)

## Scatter Chart

The **Scatter Chart**  type displays the data as a collection of points corresponding to the associated values.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
 comm.Type(SeriesType.Scatter); }).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

The following screen shot displays the **Scatter Chart.**

![ASP NET MVC scatter chart control](Chart-Types_images/ScatterChart.png)

## Bubble Chart

The **Bubble Chart**  type displays the data as a collection of bubbles.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
 comm.Type(SeriesType.Bubble); }).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

The following screen shot displays the **Bubble Chart.**

![ASP NET MVC bubble chart control](Chart-Types_images/BubbleChart.png)

## WaterFall chart

The **waterfall chart** type is used to show how an initial value is increased and decreased by a series of intermediate values, leading to a final value.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
 comm.Type(SeriesType.WaterFall); }).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

The following screenshot displays the **waterfall chart:**

![ASP NET MVC waterfall chart control](Chart-Types_images/WaterFall.png)

## Combination Chart

A **combination Chart** combines two or more series types in a single Chart. But there are some limitations in the combination Chart. They are:

1. Can’t combine Column and Bar series.
2. Pie Chart can’t be used with other series types.


{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).CommonSeriesOptions(comm => {
comm.Type(SeriesType.Column); }).Size(size => size.Height("460px").Width("950px")).ClientSideEvents(
oEve => { oEve.SeriesRendering("onSeriesRenders"); })

<script>
function onSeriesRenders(args) {
    this.model.series[5].type = ej.PivotChart.ChartTypes.Line;
    this.model.series[5].marker.visible = true;
</script>

{% endhighlight %}


The following screenshot displays a **combination Chart**.

![ASP NET MVC combination of charts](Chart-Types_images/combinationalchart.png)


