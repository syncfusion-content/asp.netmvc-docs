---
layout: post
title: Public Methods and Events of Syncfusion Maps control for Asp.Net MVC
description: Public Methods and Events in Map control
platform: ejmvc
control: Maps
documentation: ug
---

## Methods

### navigateTo(latitude, longitude, level)

Method for navigating to specific shape based on latitude, longitude and zoom level, you can use `navigateTo` method.


{% highlight CSHTML %}
 
@(Html.EJ().Map("Map1"))

{% endhighlight %}

{% highlight js %}
 
var map = $("#Map1").data("ejMap");
map.navigateTo();
   
{% endhighlight %}


### pan(direction)

Method to perform map panning, you can use `pan` method.

{% highlight CSHTML %}
 
@(Html.EJ().Map("Map1"))

{% endhighlight %}

{% highlight js %}
 
var map = $("#Map1").data("ejMap");
map.pan();
   
{% endhighlight %}

### refresh()

Method to reload the map, you can use `refresh` method.

{% highlight CSHTML %}
 
@(Html.EJ().Map("Map1"))

{% endhighlight %}

{% highlight js %}
 
var map = $("#Map1").data("ejMap");
map.refresh();
   
{% endhighlight %}


### refreshLayers()

Method to reload the shapeLayers with updated values, you can use `refreshLayers` method.


{% highlight CSHTML %}
 
@(Html.EJ().Map("Map1"))

{% endhighlight %}

{% highlight js %}
 
var map = $("#Map1").data("ejMap");
map.refreshLayers();
   
{% endhighlight %}


### refreshNavigationControl(navigation)

Method to reload the navigation control with updated values, you can use `refreshNavigationControl` method.


{% highlight CSHTML %}
 
@(Html.EJ().Map("Map1"))

{% endhighlight %}

{% highlight js %}
 
var map = $("#Map1").data("ejMap");
map.refreshNavigationControl();
   
{% endhighlight %}


### zoom(level, isAnimate)

Method to perform map zooming, you can use `zoom` method.


{% highlight CSHTML %}
 
@(Html.EJ().Map("Map1"))

{% endhighlight %}

{% highlight js %}
 
var map = $("#Map1").data("ejMap");
map.zoom();
   
{% endhighlight %}


### addMarkers(layerIndex, sublayerIndex)

You can add markers to map dynamically based on layer and sublayer index values using the `addMarkers` method.


{% highlight CSHTML %}
 
@(Html.EJ().Map("Map1"))

{% endhighlight %}

{% highlight js %}
 
var map = $("#Map1").data("ejMap");
map.addMarkers();
   
{% endhighlight %}


### refreshLayer(layerIndex, sublayerIndex, markers)

You can reload the shape marker with updated values using the `refreshLayer` method.

{% highlight CSHTML %}
 
@(Html.EJ().Map("Map1"))

{% endhighlight %}

{% highlight js %}
 
var map = $("#Map1").data("ejMap");
map.refreshLayer();
   
{% endhighlight %}


## Events

### MarkerSelected

Triggered on selecting the map markers, you can use `MarkerSelected` event.

{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.MarkerSelected("MarkerSelected")

)

{% endhighlight %}

{% highlight js %}
 
function MarkerSelected(){
    // Do Something
}

{% endhighlight %}


### Mouseleave

Triggers while leaving the hovered map shape, you can use `Mouseleave` event.


{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.Mouseleave("MouseLeave")

)

{% endhighlight %}

{% highlight js %}
 
function MouseLeave(){
    // Do Something
}

{% endhighlight %}


### Mouseover

Triggers while hovering the map shape, you can use `mouseover` event.


{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.Mouseover("MouseOver")

)

{% endhighlight %}

{% highlight js %}
 
function MouseOver(){
    // Do Something
}

{% endhighlight %}


### OnRenderComplete

Triggers once map render completed, you can use `OnRenderComplete` event.


{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.OnRenderComplete("RenderComplete")

)

{% endhighlight %}

{% highlight js %}
 
function RenderComplete(){
    // Do Something
}

{% endhighlight %}


### Panned

Triggers when map panning ends, you can use `Panned` event.


{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.Panned("Panned")

)

{% endhighlight %}

{% highlight js %}
 
function Panned(){
    // Do Something
}

{% endhighlight %}


### ShapeSelected

Triggered on selecting the map shapes, you can use `ShapeSelected` event.


{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.ShapeSelected("ShapeSelected")

)

{% endhighlight %}

{% highlight js %}
 
function ShapeSelected(){
    // Do Something
}

{% endhighlight %}


### ZoomedIn

Triggered when map is zoomed-in, you can use `ZoomedIn` event.



{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.ZoomedIn("ZoomedIn")

)

{% endhighlight %}

{% highlight js %}
 
function ZoomedIn(){
    // Do Something
}

{% endhighlight %}


### ZoomedOut

Triggers when map is zoomed out, you can use `ZoomedOut` event.



{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.ZoomedOut("ZoomedOut")

)

{% endhighlight %}

{% highlight js %}
 
function ZoomedOut(){
    // Do Something
}

{% endhighlight %}

### ShapeRendering

The `ShapeRendering` event is triggered while rendering each shape in the map.

{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.ShapeRendering("shape")

)

{% endhighlight %}

{% highlight js %}
 
function shape(){
    // Do Something
}

{% endhighlight %}


### BubbleRendering

The `BubbleRendering` event is triggered while rendering each bubble in the map.

{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.BubbleRendering("bubble")

)

{% endhighlight %}

{% highlight js %}
 
function bubble(){
    // Do Something
}

{% endhighlight %}


### LegendItemRendering

The `LegendItemRendering` event is triggered before rendering each legend in the map.

{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.LegendItemRendering("legend")

)

{% endhighlight %}

{% highlight js %}
 
function legend(){
    // Do Something
}

{% endhighlight %}


### Click

Triggers while clicking on the layers of the map, you can use `Click` event.



{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.Click("click")

)

{% endhighlight %}

{% highlight js %}
 
function click(){
    // Do Something
}

{% endhighlight %}

### DoubleClick

Triggers while double clicking on the layers of the map, you can use `DoubleClick` event.



{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.DoubleClick("doubleClick")

)

{% endhighlight %}

{% highlight js %}
 
function doubleClick(){
    // Do Something
}

{% endhighlight %}

### RightClick

Triggers while right clicking on the layers of the map, you can use `RightClick` event.



{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.RightClick("rightClick")

)

{% endhighlight %}

{% highlight js %}
 
function rightClick(){
    // Do Something
}

{% endhighlight %}

### Load

Triggers before loading the map, you can use `Load` event.

{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.Load("load")

)

{% endhighlight %}

{% highlight js %}
 
function load(){
    // Do Something
}

{% endhighlight %}


### Legend Item Click

The `LegendItemClick` event is triggered when the legend item is clicked.

{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.LegendItemClick("legendItemClick")

)

{% endhighlight %}

{% highlight js %}
 
function legendItemClick(){
    // Do Something
}

{% endhighlight %}


### MarkerEnter

The `MarkerEnter` event is triggered when the mouse enters into the marker shape.

{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.MarkerEnter("markerEnter")

)

{% endhighlight %}

{% highlight js %}
 
function markerEnter(){
    // Do Something
}

{% endhighlight %}

### MarkerLeave

The `MarkerLeave` event is triggered when mouse leaves from the marker shape.

{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.MarkerLeave("markerLeave")

)

{% endhighlight %}

{% highlight js %}
 
function markerLeave(){
    // Do Something
}

{% endhighlight %}

### Refreshed

The `Refreshed` event is triggered after refreshing the map items.

{% highlight CSHTML %}
 
@(Html.EJ().Map("container")

.Refreshed("refreshed")

)

{% endhighlight %}

{% highlight js %}
 
function refreshed(){
    // Do Something
}

{% endhighlight %}




