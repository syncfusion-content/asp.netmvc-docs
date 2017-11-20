---
layout: post
title: Public Methods and Events
description: Public methods and events in Sunburst Chart.
platform: aspnetmvc
control: SunburstChart
documentation: ug
---


## Methods


### redraw()

`redraw` the entire sunburst. You can call this method whenever you update, add or remove points from the data source or whenever you want to refresh the UI.

{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1"))

{% endhighlight %}

{% highlight js %}
 
var sun = $("#SunburstChart1").data("ejSunburstChart");
sun.redraw();
   
{% endhighlight %}

### destroy ()

`destroy` the sunburst


{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1"))

{% endhighlight %}

{% highlight js %}
 
var sun = $("#SunburstChart1").data("ejSunburstChart");
sun.destroy();
   
{% endhighlight %}



## Events

### Load

Fires before loading, you can use `Load` event.



{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.Load("load")

)

{% endhighlight %}

{% highlight js %}
 
function load(){
    // Do Something
}

{% endhighlight %}




### PreRender

Fires before rendering sunburst, you can use `PreRender` event. 



{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.PreRender("prerender")

)

{% endhighlight %}

{% highlight js %}
 
function prerender(){
    // Do Something
}

{% endhighlight %}


### Loaded

Fires after rendering sunburst, you can use `Loaded` event.  


{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.Loaded("loaded")

)

{% endhighlight %}

{% highlight js %}
 
function loaded(){
    // Do Something
}

{% endhighlight %}


### DataLabelRendering

Fires before rendering the data label, you can use `DataLabelRendering` event. 


{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.DataLabelRendering("dataLabelRendering")

)

{% endhighlight %}

{% highlight js %}
 
function dataLabelRendering(){
    // Do Something
}

{% endhighlight %}

### SegmentRendering

Fires before rendering each segment, you can use `SegmentRendering` event. 


{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.SegmentRendering("segmentRendering")

)

{% endhighlight %}

{% highlight js %}
 
function segmentRendering(){
    // Do Something
}

{% endhighlight %}


### TitleRendering

Fires before rendering sunburst title, you can use `TitleRendering` event.  


{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.TitleRendering("titleRendering")

)

{% endhighlight %}

{% highlight js %}
 
function titleRendering(){
    // Do Something
}

{% endhighlight %}



### TooltipInitialize





Fires during initialization of tooltip, you can use `TooltipInitialize` event.  


{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.TooltipInitialize("tooltipInitialize")

)

{% endhighlight %}

{% highlight js %}
 
function tooltipInitialize(){
    // Do Something
}

{% endhighlight %}



### PointRegionClick

Fires after clicking the point in sunburst, you can use `PointRegionClick` event. 


{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.PointRegionClick("pointRegionClick")

)

{% endhighlight %}

{% highlight js %}
 
function pointRegionClick(){
    // Do Something
}

{% endhighlight %}


### PointRegionMouseMove

Fires while moving the mouse over sunburst points, you can use `PointRegionMouseMove` event. 


{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.PointRegionMouseMove("pointRegionMouseMove")

)

{% endhighlight %}

{% highlight js %}
 
function pointRegionMouseMove(){
    // Do Something
}

{% endhighlight %}


### DrillDownClick

Fires when clicking the point to perform drilldown, you can use `DrillDownClick` event.  


{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.DrillDownClick("drillDownClick")

)

{% endhighlight %}

{% highlight js %}
 
function drillDownClick(){
    // Do Something
}

{% endhighlight %}

### DrillDownBack

Fires when resetting drilldown points, you can use `DrillDownBack` event.  



{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.DrillDownBack("drillDownBack")

)

{% endhighlight %}

{% highlight js %}
 
function drillDownBack(){
    // Do Something
}

{% endhighlight %}


### DrillDownReset


Fires after resetting the sunburst points, you can use `DrillDownReset` event.  


{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.DrillDownReset("drillDownReset")

)

{% endhighlight %}

{% highlight js %}
 
function drillDownReset(){
    // Do Something
}

{% endhighlight %}

### LegendItemRendering


Fires before rendering the legend item, you can use `LegendItemRendering` event. 


{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.LegendItemRendering("legendItemRendering")

)

{% endhighlight %}

{% highlight js %}
 
function legendItemRendering(){
    // Do Something
}

{% endhighlight %}

### LegendItemClick


Fires when clicking the legend item, you can use `LegendItemClick` event.



{% highlight CSHTML %}
 
@(Html.EJ().SunburstChart("SunburstChart1")

.LegendItemClick("legendItemClick")

)

{% endhighlight %}

{% highlight js %}
 
function legendItemClick(){
    // Do Something
}

{% endhighlight %}



