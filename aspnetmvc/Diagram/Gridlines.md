---
layout: post
title: Gridlines | Diagram | ASP.NET MVC | Syncfusion
description: gridlines
platform: ejmvc
control: Diagram
documentation: ug
---

# Gridlines

**Gridlines** are the pattern of lines drawn behind the Diagram elements. It provides a visual guidance while dragging or arranging the objects on the Diagram surface.

## Customize the gridlines visibility

The `SnapSettings.SnapConstraints` enables you to show/hide the gridlines. The following code example illustrates how to show or hide gridlines.

{% highlight razor %}

@using Syncfusion.JavaScript.DataVisualization.DiagramEnums

@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
	@*Shows both horizontal and vertical gridlines*@
	.SnapSettings(e => e.SnapConstraints(SnapConstraints.ShowLines))
)

{% endhighlight %}

![](Gridlines_images/Gridlines_img1.png)

To show only horizontal/vertical gridlines or to hide gridlines, refer to [Constraints](/js/Diagram/Constraints#snapconstraints "Constraints")

## Appearance

You can customize the appearance of the gridlines by using a set of predefined properties. To explore those properties, refer to [Gridlines](/js/api/ejDiagram#snapsettings:horizontalgridlines "Gridlines")
The `HorizontalGridLines` and `VerticalGridLines` properties allow to customize the appearance of the gridlines. The following code example illustrates how to customize the appearance of gridlines.

{% highlight razor %}
@using Syncfusion.JavaScript.DataVisualization.DiagramEnums

@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
	.SnapSettings(e => {
		@*Shows both horizontal and vertical gridlines*@
		e.SnapConstraints(SnapConstraints.ShowLines)

		@*Customizes the line color and line style to the gridlines.*@
		.VerticalGridlines(s => {
			s.LineColor("blue")
			.LineDashArray("2 2")
		})
		.HorizontalGridlines(s => {
			s.LineColor("blue")
			.LineDashArray("2 2")
		});
	})
)
{% endhighlight %}

![](Gridlines_images/Gridlines_img4.png)

### Line Intervals

Thickness and the space between gridlines can be customized by using `LinesInterval` property. In the linesInterval collections, values at the odd places are refered as the thickness of lines and the values at the even places are referred as the space between gridlines.

The following code example illustrates how to customize the thickness of lines and the line intervals.

{% highlight razor %}
@using Syncfusion.JavaScript.DataVisualization.DiagramEnums

@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
	.SnapSettings(e => {
		@*Shows both horizontal and vertical gridlines*@
		e.SnapConstraints(SnapConstraints.ShowLines)

		@*Customizes the line color and line style to the gridlines.*@
		.VerticalGridlines(s => {
			s.LineColor("blue")
			.LineDashArray("2 2")
			@*Defines the thickness and intervals for a pattern of lines*@
			.LinesInterval(new List<decimal>(){1.25m, 14, 0.25m, 15, 0.25m, 15, 0.25m, 15, 0.25m, 15});
		})
		.HorizontalGridlines(s => {
			s.LineColor("blue")
			.LineDashArray("2 2")
			@*Defines the thickness and intervals for a pattern of lines*@
			.LinesInterval(new List<decimal>(){1.25m, 14, 0.25m, 15, 0.25m, 15, 0.25m, 15, 0.25m, 15});
		});
	})
)
{% endhighlight %}

![](Gridlines_images/Gridlines_img2.png)

# Snapping

## Snap To Lines

This feature allows the Diagram objects to snap to the nearest intersection of gridlines while being dragged or resized. This feature enables easier alignment during layout or design.

Snapping to gridlines can be enabled/disabled with the `SnapSettings.SnapConstraints`. The following code example illustrates how to enable/disable the snapping to gridlines.

{% highlight razor %}

@using Syncfusion.JavaScript.DataVisualization.DiagramEnums 
@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
	@*Enables snapping to both the horizontal and vertical lines.*@
	.SnapSettings(e => e.SnapConstraints(SnapConstraints.SnapToLines))
)

{% endhighlight %}

To enable/disable snapping to horizontal/vertical lines, refer to [Constraints] (/js/Diagram/Constraints#SnapConstraints "Constraints")

## Customization of Snap Intervals

By default, the objects are snapped towards the nearest gridline. The gridline or position towards where the diagram object snaps can be customized with the property, `snapInterval`. The following code example illustrates how to customize the snap intervals.

{% highlight razor %}
@using Syncfusion.JavaScript.DataVisualization.DiagramEnums 
@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
	.SnapSettings(e => {
		@*Shows both horizontal and vertical gridlines*@
		e.SnapConstraints(SnapConstraints.All)

		@*Defines a set of intervals where the object is snapped.*@
		@*In this example, the object is snapped to every 10px.*@
		.VerticalGridlines(s => s.LinesInterval(new List<decimal>(){10}))
		.HorizontalGridlines(s => s.LinesInterval(new List<decimal>(){10});
	})
)
{% endhighlight %}

## Snap To Objects

The snap-to-object provides visual cues to assist with aligning and spacing Diagram elements. A node can be snapped with its neighbouring objects based on certain alignments. Such alignments are visually represented as smart guides.

The `EnableSnapToObject` property allows you to enable/disable smart guides. The following code example illustrates how to enable/disable the smart guides.

{% highlight razor %}
	
@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
	@*Enables smart guides*@
	.SnapSettings(e => e.EnableSnapToObject(true))
)

{% endhighlight %}

![](Gridlines_images/Gridlines_img4.png)