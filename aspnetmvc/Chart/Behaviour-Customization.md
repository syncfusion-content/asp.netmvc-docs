---
layout: post
title: Behaviour Customization | Chart | ASP.NET MVC | Syncfusion
description: behaviour customization
platform: ejmvc
control: Chart
documentation: ug
---

# Behaviour Customization

JS Chart allows you to customize the Chart through events. For example, you can add custom marker for highest and lowest data point using the events.

## Select a point

You can acquire the information related to a particular data point of series by moving mouse over the point or by clicking the point using PointRegionMouseMove or PointRegionClick event. PointRegionMouseMove event gets triggered when you move the mouse over the point and the PointRegionClick event gets triggered when you click the point. The following code example illustrates that x and y values of a point gets displayed when you move the mouse over the point or click the point.

{% tabs %}

{% highlight CSHTML %}

 @(Html.EJ().Chart("chartcontainer")

       .CommonSeriesOptions(cs=>cs.Type(SeriesType.Column))

       .PointRegionMouseMove("pointDetails")                  

       .PointRegionClick("pointDetails")

       .Size(sz=>sz.Width(800).Height(600))

       ) 

{% endhighlight  %}

{% highlight js %}


  <script type="text/javascript">

    function pointDetails(sender) {

        series = sender.model.series[sender.data.region.SeriesIndex];

        var X = series.points[sender.data.region.Region.PointIndex].x;

        var Y = series.points[sender.data.region.Region.PointIndex].y;

        alert("X:" + X + "  Y:" + Y);

    }

  </script>

{% endhighlight  %}
{% endtabs %}  

![](Behaviour-Customization_images/Behaviour-Customization_img1.png)

Chart with PointRegionMouseMovement
{:.caption}

## Handle Events

### Chart Events:

### Load: function

This event is handled when the Chart gets loaded; a parameter sender is passed to the handler. Using sender.model, you can access the Chart properties except series that were passed to the chart. 

{% tabs %}

{% highlight CSHTML %}

@(Html.EJ().Chart("container")

	    // ...    

      .Load("onload")

// ...

         )


{% endhighlight  %}

{% highlight js %}




     <script type="text/javascript">

               function onload (sender) {

                     sender.model.canResize = false;

               }

      </script>         


{% endhighlight  %}
{% endtabs %}  
### PreRender: function

This event is handled before the Chart gets rendered; a parameter sender is passed to the handler. Using sender.model, you can access the Chart properties that were passed to the chart. 

{% tabs %}

{% highlight CSHTML %}

@(Html.EJ().Chart("container")

	  // ...      

   .PreRender("onprerender")

// ...

   )

{% endhighlight  %}

{% highlight js %}


     <script type="text/javascript">

         function onprerender (sender) {

             console.log(sender.model.series.length);

         }


{% endhighlight  %}
{% endtabs %}  

### TitleRendering: function

This event is handled before the Chart title gets rendered; a parameter sender is passed to the handler. Using sender.data.title, you can change the title of the Chart after the Chart is loaded.

{% tabs %}
 
{% highlight CSHTML %}

@(Html.EJ().Chart("container")

           // ...

         .TitleRendering("ontitleRendering")

           // ...

         )

{% endhighlight  %}

{% highlight js %}

     <script type="text/javascript">

         function ontitleRendering(sender) {

               sender.data.title = "Olympic";

               }

      </script>          

{% endhighlight  %}
{% endtabs %} 

### ChartAxis Events:

### AxesLabelsInitialize: function

This event is handled before the Chart axis gets rendered; a parameter sender is passed to the handler. Using sender.data.axes, you can change the axis related properties after the Chart is loaded.

{% tabs %}

{% highlight CSHTML %}

@(Html.EJ().Chart("container")

           // ...

         .AxesLabelsInitialize ("onaxesLabelsInitialize")

           // ...

         )

{% endhighlight  %}

{% highlight js %}


     <script type="text/javascript">

         function onaxesLabelsInitialize(sender) {

             sender.data.axes[0].orientation = "horizontal";

               }

      </script>             


{% endhighlight %}
{% endtabs %}  

### AxesRangeCalculate: function

This event is handled after the Chart axis range gets calculated; a parameter sender is passed to the handler. Using sender.data.range, you can change the range calculated for the Chart axis.

{% tabs %}

{% highlight CSHTML %}


  @(Html.EJ().Chart("container")

           // ...

         .AxesRangeCalculate("onaxesRangeCalculate")

           // ...

         )

{% endhighlight  %}

{% highlight js %}

     <script type="text/javascript">

         function onaxesRangeCalculate(sender) {

             sender.data.range.min = 2;

               }

      </script>  

{% endhighlight  %}
{% endtabs %}  

### AxesTitleRendering: function

This event is handled before the Chart axis title gets rendered; a parameter sender is passed to the handler. Using sender.data.Title, you can change the axis title after the Chart is loaded.
{% tabs %}

{% highlight CSHTML %}

@(Html.EJ().Chart("container")

           // ...

         .AxesTitleRendering("onaxesTitleRendering")

           // ...

         )

{% endhighlight  %}

{% highlight js %}


     <script type="text/javascript">

         function onaxesTitleRendering(sender) {

             sender.data.title = "Countries";

               }

      </script>

{% endhighlight  %}
{% endtabs %}  

### AxesLabelRendering: function

This event is handled before the Chart axis label gets rendered; a parameter sender is passed to the handler. Using sender.data.label.Text, you can change the axis labels after the Chart is loaded.

{% tabs %}
 
{% highlight CSHTML %}

@(Html.EJ().Chart("container")

           // ...

         .AxesLabelRendering("onaxesLabelRendering")

           // ...

         )
{% endhighlight  %}

{% highlight js %}

     <script type="text/javascript">

         function onaxesLabelRendering(sender) {

             sender.data.label.Text = "Label1";

               }

      </script>
{% endhighlight  %}
{% endtabs %} 

### Series Events:

### SeriesRendering: function

This event is handled before the Chart series gets rendered; a parameter sender is passed to the handler. Using sender.data.series, you can get access to the series properties.

{% tabs %}

{% highlight CSHTML %}

 @(Html.EJ().Chart("container")

           // ...

         .SeriesRendering("onseriesRendering")

           // ...

         )

{% endhighlight  %}

{% highlight js %}

     <script type="text/javascript">

         function onseriesRendering(sender) {

             sender.data.series.name = "horizontal";

               }

      </script>         


{% endhighlight  %}
{% endtabs %}  

### SymbolRendering: function

This event is handled before the marker of each series point gets rendered; a parameter sender is passed to the handler. Using sender.data you can get access style and location of the symbol.
{% tabs %}

{% highlight CSHTML %}


  @(Html.EJ().Chart("container")

           // ...

         .SymbolRendering("onsymbolRendering")

           // ...

         )

{% endhighlight  %}

{% highlight js %}


     <script type="text/javascript">

         function onsymbolRendering(sender) {`

             console.log(sender.data.style.PointIndex);

               }

      </script>         

{% endhighlight  %}
{% endtabs %}  

### DisplayTextRendering: function

This event is handled before the dataLabel of each series points gets rendered; a parameter sender is passed to the handler. Using sender.data.text you can change the dataLabel of each point in the series.
{% tabs %}

{% highlight CSHTML %}

 @(Html.EJ().Chart("container")

           // ...

         .DisplayTextRendering("ondisplayTextRendering")

           // ...

         )


{% endhighlight  %}

{% highlight js %}

     <script type="text/javascript">

         function ondisplayTextRendering(sender) {

             sender.data.text = "34";

               }

      </script>         

{% endhighlight  %}
{% endtabs %}  

### AnimationComplete: function

This event is handled after the series animation is completed; a parameter sender is passed to the handler.  
{% tabs %}

{% highlight  CSHTML %}

@(Html.EJ().Chart("container")

           // ...

         .AnimationComplete("onanimationComplete")

           // ...

         )

{% endhighlight %}

{% highlight js %}

     <script type="text/javascript">

         function onanimationComplete(sender) {

             console.log(sender.data.series.name);

               }

      </script>         
{% endhighlight  %}
{% endtabs %}  

### Legend Events:

### LegendItemRendering: function

This event is handled before the legend of each series points gets rendered; a parameter sender is passed to the handler. Using sender.data.legendItem.Text you can change the text of each legend text.
{% tabs %}

{% highlight CSHTML %}

 @(Html.EJ().Chart("container")

           // ...

         .LegendItemRendering("onlegendItemRendering")

           // ...

         )

{% endhighlight  %}

{% highlight js %}

     <script type="text/javascript">

         function onlegendItemRendering(sender) {

             sender.data.legendItem.Text = "Series1";

         }

      </script>         

{% endhighlight  %}
{% endtabs %}  

### LegendItemClick: function

This event is handled when you click the legend item; a parameter sender is passed to the handler.  
{% tabs %}
{% highlight CSHTML %}

@(Html.EJ().Chart("container")

           // ...

         .LegendItemClick("onlegendItemClick")

           // ...

         )
{% endhighlight  %}

{% highlight js %}

     <script type="text/javascript">

         function onlegendItemClick(sender) {

             console.log("Legend Item Click");

         }

      </script>         


{% endhighlight  %}

{% endtabs %}  
### LegendItemMouseMove: function

This event is handled when you move the mouse over the legend item; a parameter sender is passed to the handler. Using sender.data.legendItem.Text you can change the text of each legend text.
{% tabs %}

{% highlight CSHTML %}

 @(Html.EJ().Chart("container")

           // ...

         .LegendItemMouseMove("onlegendItemMouseMove")

           // ...

         )
{% endhighlight  %}

{% highlight js %}


     <script type="text/javascript">

         function onlegendItemMouseMove(sender) {

             console.log("Legend Item Mouse Move");

         }

      </script>

{% endhighlight  %}
{% endtabs %}  
### LengendBoundsCalculate: function

This event is handled after the bounds for legend is calculated.  A parameter sender is passed to the handler.  Using sender.data.legendBound, you can access the bounds of the Chartlegend.

{% tabs %}

{% highlight CSHTML %}

 @(Html.EJ().Chart("container")

           // ...

         .LegendBoundsCalculate("onlegendBoundsCalculate")

           // ...

         )

{% endhighlight  %}

{% highlight js %}


     <script type="text/javascript">

         function onlegendBoundsCalculate(sender) {

             sender.data.legendBound.Height = 34;

         }

      </script>

{% endhighlight %}
{% endtabs %}  
### Tooltip Events:

#### ToolTipInitialize: function

This event is handled before the tooltip gets rendered.  A parameter sender is passed to the handler.  Using sender.data.currentText, you can change the tooltip text.
{% tabs %}

{% highlight CSHTML %}

  @(Html.EJ().Chart("container")

           // ...

         .ToolTipInitialize("ontoolTipInitialize")

           // ...

         )

{% endhighlight  %}

{% highlight js %}


     <script type="text/javascript">

         function ontoolTipInitialize(sender) {

             sender.data.currentText = "tooltip";

         }

      </script>


{% endhighlight  %}
{% endtabs %}  
### TrackAxisToolTip: function

This event is handled before the tooltip for axis gets rendered when crosshair is enabled.  A parameter sender is passed to the handler.  Using sender.data.currentTrackText, you can change the tooltip text.
{% tabs %}

{% highlight CSHTML %}


 @(Html.EJ().Chart("container")

           // ...

         .TrackAxisToolTip("ontrackAxisToolTip")

           // ...

         )


{% endhighlight  %}

{% highlight js %}

     <script type="text/javascript">

         function ontrackAxisToolTip(sender) {

             sender.data.currentTrackText = "tooltip";

         }

      </script>         

{% endhighlight %}
{% endtabs %}  
### TrackToolTip: function

This event is handled before the tooltip for trackball get rendered when trackball is enabled.  A parameter sender is passed to the handler.  Using sender.data.currentText, you can change the tooltip text.
{% tabs %}

{% highlight CSHTML %}

 @(Html.EJ().Chart("container")

           // ...

         .TrackToolTip("ontrackToolTip")

           // ...

       )


{% endhighlight %}

{% highlight js %}

     <script type="text/javascript">

         function ontrackToolTip(sender) {

             sender.data.currentText = "tooltip";

         }

      </script>          

{% endhighlight  %}
{% endtabs %}  
