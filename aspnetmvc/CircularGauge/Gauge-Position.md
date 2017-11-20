---
layout: post
title: Gauge Position | CircularGauge | ASP.NET MVC | Syncfusion
description: gauge position
platform: ejmvc
control: CircularGauge
documentation: ug
---

# Gauge Position

**Semi-circular Gauge** can be positioned within the canvas element which provides better appearance for the gauge in the canvas.

## Positioning

* Semi-circular Gauge can be positioned with the help of the attribute called `GaugePosition`. It is an enumerable value. You can position the gauge away from the corner with the help of the `DistanceFromCorner` attribute. 
* The possible enum values for the gaugePosition are as follows:
	1. TopLeft
	2. TopCenter
	3. TopRight
	4. MiddleLeft
	5. Center
	6. MiddleRight
	7. BottomLeft
	8. BottomCenter
	9. BottomRight


{% tabs %}

{% highlight CSHTML %}

@(Html.EJ().CircularGauge("SemiCircularGauge").BackgroundColor("transparent")

// To set dimension of the canvas.
.Width(500).Height(500).Radius(100).Value(60)

// To set gauge position.
.GaugePosition(GaugePosition.TopLeft)

// To set gauge distance from corner.
.DistanceFromCorner(25)

// To set frame settings.
.Frame(fr=>fr.FrameType(Frame.HalfCircle)

// To set frame start angle.
.HalfCircleFrameStartAngle(270)

// To set frame end angle.
.HalfCircleFrameEndAngle(90))

// To set basic scale settings.
.Scales(SC =>{SC.Radius(100)
				.Maximum(120)
				.MajorIntervalValue(20)
				.MinorIntervalValue(10)
				.ShowScaleBar(true)
				.Size(1)
				.Border(border => border.Width(0.5))
				.StartAngle(270)
				.SweepAngle(180).Add();}))
{% endhighlight %}
{% highlight c# %}

public partial class CircularGaugeController : Controller
{
     //        // GET: /ToolTip/        
	 public ActionResult Semicircular()
	 {           
		return View();
     }
}

{% endhighlight %}
{% endtabs %}  
Execute the above code to render the following output.

![](Gauge-Position_images/Gauge-Position_img1.png)

Semi-circular Gauge with default top left position
{:.caption}

