---
layout: post
title: Behavior Customization | RangeNavigator | ASP.NET MVC | Syncfusion
description: behavior customization
platform: ejmvc
control: RangeNavigator
documentation: ug
---

# Behavior Customization

**RangeNavigator** allows you to customize the control using events. You can change the range for selected data of the **RangeNavigator** using events.

## Deferred update

If you set `EnableDeferredUpdate` to true, the `RangeChanged` event gets fired after dragging and dropping the slider. By default the `EnableDeferredUpdate` is true. If `EnableDeferredUpdate` is false then the `RangeChanged` event gets fired while dragging the slider.

{% highlight CSHTML %}
 [
@(Html.EJ().RangeNavigator("container")

. EnableDeferredUpdate (true)

)
{% endhighlight  %}

![](Behavior-Customization_images/Behavior-Customization_img1.png)

Deferred update
{:.caption}

## Use of Destroy method 

`_destroy`: function

This method is used to destroy the **RangeNavigator** widget. 

{% highlight CSHTML %}
 
@(Html.EJ().RangeNavigator("container")
   
)
<script type="text/javascript">  
    
	var obj = $("#container").data("ejRangeNavigator");
    obj.destroy(); // destroy the range navigator

</script>

{% endhighlight  %}

## Handle Events

### `Load`: function

This event is fired when **RangeNavigator** is loading. A parameter **sender** is passed to the handler. Using **sender.model**, you can access the RangeNavigator properties. 

{% highlight CSHTML %}

@(Html.EJ().RangeNavigator("container")

.Load("loadingData")
   
)

<script type="text/javascript">

	function loadingData(sender) 
	{

		 sender.model.allowSnapping = false;

	}

</script>

{% endhighlight %}

### `Loaded`: function

This event is handled when the **RangeNavigator** gets loaded. A parameter **sender** is passed to the handler. Using **sender.model**, you can access the RangeNavigator properties. 

{% highlight CSHTML %}
 
@(Html.EJ().RangeNavigator("container")

.Loaded("loadingData")

   
)

<script type="text/javascript">

	function loadingData(sender) 
	{

		 sender.model.isResponsive = false;

	}

</script>         

{% endhighlight  %}

### `RangeChanged`: function

This event gets fired whenever the selected range changes in **RangeNavigator**. A parameter **sender** is passed to the handler. Using **sender.selectedRangeSettings**, you can access the start and end value of range for the selected region. 
{% highlight CSHTML %}

@(Html.EJ().RangeNavigator("container")

    
.RangeChanged("loadingData")

)

<script type="text/javascript">

   function loadingData(sender) 
   {

		 console.log(sender.selectedRangeSettings.start);

   }

</script> 

{% endhighlight %}

### `SelectedRangeStart` : function

This event is fired when starting to change the slider position in **RangeNavigator**. A parameter **sender** is passed to the handler. Using **sender.selectedRangeSettings**, you can access the start value of range for the selected region. 

{% highlight CSHTML %}

@(Html.EJ().RangeNavigator("container")
    
.SelectedRangeStart("loadingData")

)

<script type="text/javascript">

   function loadingData(sender) 
   {

		 console.log(sender.selectedRangeSettings.start);

   }

</script>   

{% endhighlight %}

### `SelectedRangeEnd` : function

This event is fired when selection ends in **RangeNavigator**. A parameter **sender** is passed to the handler. Using sender.selectedRangeSettings, you can access the end value of range for the selected region. 

{% highlight CSHTML %}

@(Html.EJ().RangeNavigator("container")
    
.SelectedRangeEnd("loadingData")

)

<script type="text/javascript">

   function loadingData(sender) 
   {

		 console.log(sender.selectedRangeSettings.end);

   }

</script>   

{% endhighlight %}

### `ScrollStart` : function

This event is fired when starting to change the scrollbar position of **RangeNavigator**. A parameter **sender** is passed to the handler. Using sender.data startRange and sender.data endRange, you can access the scrollbar position starting and ending range value on changed scrollbar. 

{% highlight javascript %}

@(Html.EJ().RangeNavigator("container")
    
.ScrollStart(loadingData)

)
<script type="text/javascript">

   function loadingData(sender) 
   {
	   	console.log(sender.type);
   }

</script>  

{% endhighlight %}

### `ScrollEnd` : function

This event is fired while ending the change in scrollbar position of **RangeNavigator**. A parameter **sender** is passed to the handler. Using data oldRange and data newRange, you can access the scrollbar position old and new range values on changing scrollbar. 

{% highlight javascript %}

@(Html.EJ().RangeNavigator("container")
    
.ScrollEnd(loadingData)

)
<script type="text/javascript">

   function loadingData(sender) 
   {
	   	console.log(sender.type);
   }

</script>  

{% endhighlight %}

### `ScrollChanged` : function

This event is fired when changing the scrollbar position of **RangeNavigator**. A parameter **sender** is passed to the handler. Using data oldRange and data newRange, you can access the old and new range values of changed scrollbar position. 

{% highlight javascript %}

@(Html.EJ().RangeNavigator("container")
    
.ScrollChanged(loadingData)

)
<script type="text/javascript">

   function loadingData(sender) 
   {
	   	console.log(sender.type);
   }

</script>  

{% endhighlight %}

## Use of ZoomCoordinates

**RangeNavigator** is used along with the controls like chart and grid to view the selected data. To update chart/grid, whenever the selected range changes in **RangeNavigator**, you can use `RangeChanged` event of RangeNavigator and then update the chart/grid with the selected data in this event. 

You can easily update the data for chart by assigning the `ZoomFactor` and `ZoomPosition` of the RangeNavigator to the chart axis. 
{% highlight CSHTML %}
 

@(Html.EJ().RangeNavigator("container")

.RangeChanged("loadingData")

)

<script type="text/javascript">

	// setting zoom factor and position for chart axis in rangeChanged event.

	function loadingData(sender) 
	{

	 var chart = $("#container").data("ejChart");

	 if (chart != null) 
	 {

		 chart.model.axes[0].zoomPosition = sender. zoomPosition;                                                               

		 chart.model.axes[0].zoomFactor = sender. zoomFactor;

		}

		$("#container").ejChart("redraw");

	}

</script>         
{% endhighlight  %}


![](Behavior-Customization_images/Behavior-Customization_img2.png)



## Thumb Template

You can customize Thumb template by using `LeftThumbTemplate` and `RightThumbTemplate` property. You can add the required template as a “div” element with an “id” to the web page and assign the id or assign the HTML string to this property under `NavigatorStyleSettings`. 
{% highlight CSHTML %}


<script type="text/x-jsrender" id="left" >

           <svg height="24" width="32" style="fill:#DD4A4A;stroke:black;">

                <path d="M2 2 L2 22 L22 22 L32 12 L22 2 Z" />

           </svg>

</script>

<script type="text/x-jsrender" id="right">

           <svg height="24" width="32" style="fill:#DD4A4A;stroke:black; ">

               <path d="M2 12 L12 22 L32 22 L32 2 L12 2 Z" />

           </svg>

</script>


@(Html.EJ().RangeNavigator("container")

	            // ...              

      .NavigatorStyleSettings(navigator=>navigator.LeftThumbTemplate("left")

                 .RightThumbTemplate("right"))

                 // ... 

)

{% endhighlight %}

The following screenshot displays the **RangeNavigator** using thumb template.

![](Behavior-Customization_images/Behavior-Customization_img3.png)

## Value Axis Settings

You can customize the line, `Font` `Size`, gridline, tickline, range, `RangePadding` and visibility of **RangeNavigator** axis.

To enable the visibility of axis line, you need to set `Visible` property of `AxisLine` in `ValueAxisSettings`. 

You can customize the axis range by specifying `Min`, `Max` and `Interval` for `Range` property.

The `MajorGridLines` can be enabled by specifying `Visible` property. The `Size`, `Width` and `Visible` property of `MajorTickLines` is used to customize the axis tick lines.

The visibility of `ValueAxisSettings` is enabled by setting `Visible` property as true. 

{% highlight CSHTML %}

@(Html.EJ().RangeNavigator("container")

	            // ...             
                .ValueAxisSettings(value=>value                        
							.AxisLine(axis=>axis.Visible(true))
							.Font(f=>f.Size('12px'))
							.MajorGridLines(grid=>grid.Visible(true))
							.MajorTickLines(tick=>tick.Size(3).Visible(false).Width(3))
							.Range(range=>range.Min(0).Max(100).Interval(10))
							.RangePadding(RangePadding.Normal),
							.Visible(true)
				)
                   // ...             
             )

{% endhighlight %}

## Selected Range Settings

The start and end range values of selected range can be customized using `Start` and `End` property of `SelectedRangeSettings`.

{% highlight CSHTML %}

@(Html.EJ().RangeNavigator("container")

	            // ...              
                .SelectedRangeSettings(range=>range.Start("01/05/1992").End("01/05/1993"))                      
                   // ...             
             )

{% endhighlight %}


