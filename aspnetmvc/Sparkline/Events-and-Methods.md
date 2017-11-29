---
layout: post
title: Events and Methods
description: Learn how to add Events and Methods in Sparkline.
platform: ejmvc
control: Sparkline
documentation: ug
---

# Methods and Events

## Methods

### redraw()

This methods redraws the entire sparkline. You can call `redraw()` whenever you update, add or remove points from the data source or whenever you want to refresh the UI.

{% highlight cshtml %}

@(Html.EJ().Sparkline("container"))

{% endhighlight %}

{% highlight js %}

// redraw method for sparkline
$("#container").ejSparkline("redraw");

{% endhighlight %}

## Events

### Load

The `Load` event is fired before loading the sparkline.

{% highlight cshtml %}

@(Html.EJ().Sparkline("container")

    .Load("onLoad");

)

{% endhighlight %}

{% highlight js %}

 <script type="text/javascript">
    function onLoad(sender) {
                //Do something
    }
</script>

{% endhighlight %}

### Loaded

The `Loaded` event is fired after loaded the sparkline.

{% highlight cshtml %}

@(Html.EJ().Sparkline("container")

    .Loaded("onLoaded");

)

{% endhighlight %}

{% highlight js %}

 <script type="text/javascript">
    function onLoaded(sender) {
                //Do something
    }
</script>

{% endhighlight %}

### TooltipInitialize

Fires before rendering trackball tooltip. You can use `TooltipInitialize` event to customize the text displayed in trackball tooltip.

{% highlight cshtml %}

@(Html.EJ().Sparkline("container")

    .TooltipInitialize("onTooltipInitialize")

)

{% endhighlight %}

{% highlight js %}

 <script type="text/javascript">
    function onTooltipInitialize(sender) {
                //Do something
    }
</script>

{% endhighlight %}

### SeriesRendering

Fires before rendering a series. The `SeriesRendering` event is fired for each series in Sparkline.

{% highlight cshtml %}

@(Html.EJ().Sparkline("container")

    .SeriesRendering("onSeriesRender")

)

{% endhighlight %}

{% highlight js %}

 <script type="text/javascript">
    function onSeriesRender(sender) {
                //Do something
    }
</script>

{% endhighlight %}

### PointRegionMouseMove

The `PointRegionMouseMove` event is fired when mouse is moved over a point.

{% highlight cshtml %}

@(Html.EJ().Sparkline("container")

    .PointRegionMouseMove("onPointMouseMove")

)

{% endhighlight %}

{% highlight js %}

 <script type="text/javascript">
    function onPointMouseMove(sender) {
                //Do something
    }
</script>

{% endhighlight %}

### PointRegionMouseClick

The `PointRegionMouseClick` event is fired on clicking a point in sparkline. You can use this event to handle clicks made on points.

{% highlight cshtml %}

@(Html.EJ().Sparkline("container")

    .PointRegionMouseClick("onPointMouseClick")

)

{% endhighlight %}

{% highlight js %}

 <script type="text/javascript">
    function onPointMouseClick(sender) {
                //Do something
    }
</script>

{% endhighlight %}

### SparklineMouseMove

The `SparklineMouseMove` is fired on moving mouse over the sparkline.

{% highlight cshtml %}

@(Html.EJ().Sparkline("container")

    .SparklineMouseMove("onSparklineMouseMove")

)

{% endhighlight %}

{% highlight js %}

 <script type="text/javascript">
    function onSparklineMouseMove(sender) {
                //Do something
    }
</script>

{% endhighlight %}

### SparklineMouseLeave

The `SparklineMouseLeave` event is fired on moving mouse outside the sparkline.

{% highlight cshtml %}

@(Html.EJ().Sparkline("container")

    .SparklineMouseLeave("onSparklineMouseLeave")

)

{% endhighlight %}

{% highlight js %}

 <script type="text/javascript">
    function onSparklineMouseLeave(sender) {
                //Do something
    }
</script>

{% endhighlight %}