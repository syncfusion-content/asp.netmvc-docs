---
layout: post
title: Public Methods and Events | lineargauge | ASP.NET MVC | Syncfusion
description: Public Methods and Events
platform: ejmvc
control: lineargauge
documentation: ug
---

##Events


### DrawBarPointers

Triggers while the bar pointer are being drawn on the gauge, you can use `DrawBarPointers` event.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.DrawBarPointers("drawBarPointer")

)

function drawBarPointer(){
    // Do Something
}

{% endhighlight %}

### DrawCustomLabel

Triggers while the customLabel are being drawn on the gauge, you can use `DrawCustomLabel` event.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.DrawCustomLabel("drawCustomLabel")

)

function drawCustomLabel(){
    // Do Something
}

{% endhighlight %}







### DrawIndicators

Triggers while the Indicator are being drawn on the gauge, you can use `DrawIndicators` event.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.DrawIndicators("drawIndicators")

)

function drawIndicators(){
    // Do Something
}

{% endhighlight %}






### DrawLabels

Triggers while the label are being drawn on the gauge, you can use `DrawLabels` event.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.DrawLabels("drawLabels")

)

function drawLabels(){
    // Do Something
}

{% endhighlight %}




### DrawMarkerPointers

Triggers while the marker are being drawn on the gauge, you can use `DrawMarkerPointers` event.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.DrawMarkerPointers("drawMarkerPointer")

)

function drawMarkerPointer(){
    // Do Something
}

{% endhighlight %}




### DrawRange

Triggers while the range are being drawn on the gauge, you can use `DrawRange` event.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.DrawRange("drawRange")

)

function drawRange(){
    // Do Something
}

{% endhighlight %}






### DrawTicks

Triggers while the ticks are being drawn on the gauge, you can use `DrawTicks` event.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.DrawTicks("drawTicks")

)

function drawTicks(){
    // Do Something
}

{% endhighlight %}






### Init

Triggers when the gauge is initialized, you can use `Init` event.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.Init("init")

)

function init(){
    // Do Something
}

{% endhighlight %}




### Load

Triggers while the gauge start to Load, you can use `Load` event.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.Load("load")

)

function load(){
    // Do Something
}

{% endhighlight %}





### MouseClick

Triggers when the left mouse button is clicked, you can use `MouseClick` event.




{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.MouseClick("MouseClick")

)

function MouseClick(){
    // Do Something
}

{% endhighlight %}







### MouseClickMove

Triggers when clicking and dragging the mouse pointer over the gauge pointer, you can use `MouseClickMove` event.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.MouseClickMove("MouseClickMove")

)

function MouseClickMove(){
    // Do Something
}

{% endhighlight %}






### MouseClickUp


Triggers when the mouse click is released, you can use `MouseClickUp` event.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.MouseClickUp("MouseClickUp")

)

function MouseClickUp(){
    // Do Something
}

{% endhighlight %}






### RenderComplete

Triggers while the rendering of the gauge completed, you can use `RenderComplete` event.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("container")

.RenderComplete("RenderComplete")

)

function RenderComplete(){
    // Do Something
}

{% endhighlight %}


## Methods


### destroy()

`Destroy` the linear gauge all events bound using this._on will be unbind automatically and bring the control to pre-init state.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.destroy();

{% endhighlight %}


### getBarDistanceFromScale()

To get bar distance from scale in number, you can use `getBarDistanceFromScale` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getBarDistanceFromScale();

{% endhighlight %}


### getBarPointerValue()

To get Bar Pointer Value in number, you can use `getBarPointerValue`method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getBarPointerValue();

{% endhighlight %}

### getBarWidth()

To get Bar Width in number, you can use `getBarWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getBarWidth();

{% endhighlight %}



### getCustomLabelAngle()

To get CustomLabel Angle in number, you can use `getCustomLabelAngle` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getCustomLabelAngle();

{% endhighlight %}



### getCustomLabelValue()

To get CustomLabel Value in string, you can use `getCustomLabelValue` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getCustomLabelValue();

{% endhighlight %}



### getLabelAngle()

To get Label Angle in number, you can use `getLabelAngle` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getLabelAngle();

{% endhighlight %}




### getLabelPlacement()

To get LabelPlacement in number, you can use `getLabelPlacement` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getLabelPlacement();

{% endhighlight %}


### getLabelStyle()

To get LabelStyle in number, you can use `getLabelStyle` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getLabelStyle();

{% endhighlight %}




### getLabelXDistanceFromScale()

To get Label XDistance From Scale in number, you can use `getLabelXDistanceFromScale` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getLabelXDistanceFromScale();

{% endhighlight %}




### getLabelYDistanceFromScale()
To get PointerValue in number, you can use `getLabelXDistanceFromScale` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getLabelYDistanceFromScale();

{% endhighlight %}






### getMajorIntervalValue()

To get Major Interval Value in number, you can use `getMajorIntervalValue` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getMajorIntervalValue();

{% endhighlight %}


### getMarkerStyle()

To get MarkerStyle in number, you can use `getMarkerStyle` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getMarkerStyle();

{% endhighlight %}



### getMaximumValue()

To get Maximum Value in number, you can use `getMaximumValue` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getMaximumValue();

{% endhighlight %}



### getMinimumValue()

To get PointerValue in number, you can use `getMinimumValue` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getMinimumValue();

{% endhighlight %}

### getMinorIntervalValue()

To get Minor Interval Value in number, you can use `getMinorIntervalValue` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getMinorIntervalValue();

{% endhighlight %}


### getPointerDistanceFromScale()

To get Pointer Distance From Scale in number, you can use `getPointerDistanceFromScale` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getPointerDistanceFromScale();

{% endhighlight %}

### getPointerHeight()

To get PointerHeight in number, you can use `getPointerHeight` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getPointerHeight();

{% endhighlight %}


### getPointerPlacement()

To get Pointer Placement in String, you can use `getPointerPlacement` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getPointerPlacement();

{% endhighlight %}

### getPointerValue()

To get PointerValue in number, you can use `getPointerValue` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getPointerValue();

{% endhighlight %}



### getPointerWidth()

To get PointerWidth in number, you can use `getPointerWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getPointerWidth();

{% endhighlight %}


### getRangeBorderWidth()

To get Range Border Width in number, you can use `getRangeBorderWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getRangeBorderWidth();

{% endhighlight %}



### getRangeDistanceFromScale()

To get Range Distance From Scale in number, you can use `getRangeDistanceFromScale` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getRangeDistanceFromScale();

{% endhighlight %}


### getRangeEndValue()

To get Range End Value in number, you can use `getRangeEndValue` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getRangeEndValue();

{% endhighlight %}



### getRangeEndWidth()

To get Range End Width in number, you can use `getRangeEndWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getRangeEndWidth();

{% endhighlight %}




### getRangePosition()

To get Range Position in number, you can use `getRangePosition` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getRangePosition();

{% endhighlight %}



### getRangeStartValue()

To get Range Start Value in number, you can use `getRangeStartValue` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getRangeStartValue();

{% endhighlight %}







### getRangeStartWidth()

To get Range Start Width in number, you can use `getRangeStartWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getRangeStartWidth();

{% endhighlight %}



### getScaleBarLength()

To get ScaleBarLength in number, you can use `getScaleBarLength` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getScaleBarLength();

{% endhighlight %}


### getScaleBarSize()

To get Scale Bar Size in number, you can use `getScaleBarSize` method.




{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getScaleBarSize();

{% endhighlight %}


### getScaleBorderWidth()

To get Scale Border Width in number, you can use `getScaleBorderWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getScaleBorderWidth();

{% endhighlight %}

### getScaleDirection()

To get Scale Direction in number, you can use `getScaleDirection` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getScaleDirection();

{% endhighlight %}



### getScaleLocation()

To get Scale Location in object, you can use `getScaleLocation` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getScaleLocation();

{% endhighlight %}




### getScaleStyle()

To get Scale Style in string, you can use `getScaleStyle` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getScaleStyle();

{% endhighlight %}



### getTickAngle()

To get Tick Angle in number, you can use `getTickAngle` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getTickAngle();

{% endhighlight %}



### getTickHeight()

To get Tick Height in number, you can use `getTickHeight` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getTickHeight();

{% endhighlight %}


### getTickPlacement()

To get getTickPlacement in number, you can use `getTickPlacement` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getTickPlacement();

{% endhighlight %}


### getTickStyle()

To get Tick Style in string, you can use `getTickStyle` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getTickStyle();

{% endhighlight %}


### getTickWidth()

To get Tick Width in number, you can use `getTickWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getBarDistanceFromScale();

{% endhighlight %}

### getTickXDistanceFromScale()

To get get Tick XDistance From Scale in number, you can use `getTickXDistanceFromScale` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getTickWidth();

{% endhighlight %}



### getTickYDistanceFromScale()

To get Tick YDistance From Scale in number, you can use `getTickYDistanceFromScale` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.getTickYDistanceFromScale();

{% endhighlight %}



### scales()

Specifies the scales, you can use `scales` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.scales();

{% endhighlight %}


### setBarDistanceFromScale()

To set setBarDistanceFromScale, you can use `setBarDistanceFromScale` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setBarDistanceFromScale();

{% endhighlight %}

### setBarPointerValue()

To set setBarPointerValue, you can use `setBarPointerValue` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setBarPointerValue();

{% endhighlight %}


### setBarWidth()

To set setBarWidth, you can use `setBarWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setBarWidth();

{% endhighlight %}


### setCustomLabelAngle()

To set setCustomLabelAngle, you can use `setCustomLabelAngle` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setCustomLabelAngle();

{% endhighlight %}


### setCustomLabelValue()

To set setCustomLabelValue, you can use `setCustomLabelValue` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setCustomLabelValue();

{% endhighlight %}



### setLabelAngle()

To set setLabelAngle, you can use `setLabelAngle` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setLabelAngle();

{% endhighlight %}



### setLabelPlacement()

To set setLabelPlacement, you can use `setLabelPlacement` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setLabelPlacement();

{% endhighlight %}


### setLabelStyle()

To set setLabelStyle, you can use `setLabelStyle` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setLabelStyle();

{% endhighlight %}



### setLabelXDistanceFromScale()

To set setLabelXDistanceFromScale, you can use `setLabelXDistanceFromScale` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setLabelXDistanceFromScale();

{% endhighlight %}



### setLabelYDistanceFromScale()

To set setLabelYDistanceFromScale, you can use `setLabelYDistanceFromScale` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setLabelYDistanceFromScale();

{% endhighlight %}


### setMajorIntervalValue()

To set setMajorIntervalValue, you can use `setMajorIntervalValue` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setMajorIntervalValue();

{% endhighlight %}




### setMarkerStyle()

To set setMarkerStyle, you can use `setMarkerStyle` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setMarkerStyle();

{% endhighlight %}




### setMaximumValue()

To set setMaximumValue, you can use `setMaximumValue` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setMaximumValue();

{% endhighlight %}


### setMinimumValue()

To set setMinimumValue, you can use `setMinimumValue` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setMinimumValue();

{% endhighlight %}



### setMinorIntervalValue()

To set setMinorIntervalValue, you can use `setMinorIntervalValue` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setMinorIntervalValue();

{% endhighlight %}


### setPointerDistanceFromScale()

To set setPointerDistanceFromScale, you can use `setPointerDistanceFromScale` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setPointerDistanceFromScale();

{% endhighlight %}




### setPointerHeight()

To set PointerHeight, you can use `setPointerHeight` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setPointerHeight();

{% endhighlight %}




### setPointerPlacement()

To set setPointerPlacement, you can use `setPointerPlacement` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setPointerPlacement();

{% endhighlight %}




### setPointerValue()

To set PointerValue, you can use `setPointerValue` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setPointerValue();

{% endhighlight %}





### setPointerWidth()

To set PointerWidth, you can use `setPointerWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setPointerWidth();

{% endhighlight %}




### setRangeBorderWidth()

To set setRangeBorderWidth, you can use `setRangeBorderWidth` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setRangeBorderWidth();

{% endhighlight %}




### setRangeDistanceFromScale()

To set setRangeDistanceFromScale, you can use `setRangeDistanceFromScale` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setRangeDistanceFromScale();

{% endhighlight %}




### setRangeEndValue()

To set setRangeEndValue, you can use `setRangeEndValue` method.



{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setRangeEndValue();

{% endhighlight %}




### setRangeEndWidth()

To set setRangeEndWidth, you can use `setRangeEndWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setRangeEndWidth();

{% endhighlight %}




### setRangePosition()

To set setRangePosition, you can use `setRangePosition` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setRangePosition();

{% endhighlight %}



### setRangeStartValue()

To set setRangeStartValue, you can use `setRangeStartValue` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setRangeStartValue();

{% endhighlight %}




### setRangeStartWidth()

To set setRangeStartWidth, you can use `setRangeStartWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setRangeStartWidth();

{% endhighlight %}





### setScaleBarLength()

To set setScaleBarLength, you can use `setScaleBarLength` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setScaleBarLength();

{% endhighlight %}



### setScaleBarSize()

To set setScaleBarSize, you can use `setScaleBarSize` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setScaleBarSize();

{% endhighlight %}




### setScaleBorderWidth()

To set setScaleBorderWidth, you can use `setScaleBorderWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setScaleBorderWidth();

{% endhighlight %}




### setScaleDirection()

To set setScaleDirection, you can use `setScaleDirection` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setScaleDirection();

{% endhighlight %}



### setScaleLocation()

To set setScaleLocation, you can use `setScaleLocation` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setScaleLocation();

{% endhighlight %}





### setScaleStyle()

To set setScaleStyle, you can use `setScaleStyle` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setScaleStyle();

{% endhighlight %}


### setTickAngle()

To set setTickAngle, you can use `setTickAngle` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setTickAngle();

{% endhighlight %}


### setTickHeight()

To set setTickHeight, you can use `setTickHeight` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setTickHeight();

{% endhighlight %}



### setTickPlacement()

To set setTickPlacement, you can use `setTickPlacement` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setTickPlacement();

{% endhighlight %}

### setTickStyle()

To set setTickStyle, you can use `setTickStyle` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setTickStyle();

{% endhighlight %}




### setTickWidth()

To set setTickWidth, you can use `setTickWidth` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setTickWidth();

{% endhighlight %}



### setTickXDistanceFromScale()

To set setTickXDistanceFromScale, you can use `setTickXDistanceFromScale` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setTickXDistanceFromScale();

{% endhighlight %}


### setTickYDistanceFromScale()

To set setTickYDistanceFromScale, you can use `setTickYDistanceFromScale` method.


{% highlight CSHTML %}
 
@(Html.EJ().LinearGauge("LinearGauge1"))

var linear = $("#LinearGauge1").data("ejLinearGauge");
linear.setTickYDistanceFromScale();

{% endhighlight %}




