---
layout: post
title: Constraints | Diagram | ASP.NET MVC | Syncfusion
description: constraints
platform: ejmvc
control: Diagram
documentation: ug
---

# Constraints
Constraints are used to enable/disable certain behaviors of the diagram, node and connector. Constraints are provided as flagged enumerations, so that multiple behaviors can be enabled/disabled with bitwise operators (`&`, `|`, `~`, `<<`, etc.).
To know more about bitwise operators, refer to [Bitwise Operations](#bitwise-operations) 

## DiagramConstraints
Diagram constraints allow to enable or disable the following behaviors.

* Page Editing
* Line Bridging
* Zoom and Pan
* Undo Redo

For more information about Diagram contraints, refer to [Diagram Constraints](/js/api/global#diagramconstraints "Diagram Constraints").

**Example**

The following example illustrates how to disable page editing.

{% highlight razor %}

@using Syncfusion.JavaScript.DataVisualization.DiagramEnums 
@using Syncfusion.JavaScript.DataVisualization.Models.Diagram

@(Html.EJ().Diagram("Diagram")
	.Width("100%").Height("600px")
	
	@*Set Diagram in read-only mode*@
	.Constraints(DiagramConstraints.Default &~ DiagramConstraints.PageEditable)
)

{% endhighlight %}

## NodeConstraints

NodeConstraints allows to enable or disable the following behaviors of node.

* Selection
* Deletion
* Drag
* Resize
* Rotate
* Connect
* Drop shadow
* Drag label
* Define tooltip

For more information about node contraints, refer to [Node Constraints](/js/api/global#nodeconstraints "Node Constraints")

**Example**

The following code illustrates how to disable rotation.

{% highlight razor %}

@using Syncfusion.JavaScript.DataVisualization.DiagramEnums 
@using Syncfusion.JavaScript.DataVisualization.Models.Diagram

@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
	.Nodes(node => {
		@*Disables rotation*@
		node.Add(new BasicShape(){ Constraints = NodeConstraints.Default &~ NodeConstraints.Rotate });
	})
)

{% endhighlight %}

## ConnectorConstraints

ConnectorConstraints allow to enable or disable certain behaviors of Connectors. They are as follows.

* Selection
* Deletion
* Drag
* Segment editing
* Define tooltip
* Bridging
* Label dragging

For more information about connector contraints, refer to [Connector Constraints](/js/api/global#connectorconstraints "Connector Constraints")

**Example**

The following code illustrates how to disable selection.

{% highlight razor %}

@using Syncfusion.JavaScript.DataVisualization.DiagramEnums 
@using Syncfusion.JavaScript.DataVisualization.Models.Diagram

@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
	.Connectors(conn => {
		@*Disables Selection*@
		conn.Add(new Connector(){ Constraints = ConnectorConstraints.Default &~ ConnectorConstraints.Select });
	})
)
	
{% endhighlight %}

## PortConstraints

You can enable or disable certain behaviors of Port. They are as follows.

* Connect

For more information about port contraints, refer to [Port Constraints](/js/api/global#portconstraints "Port Constraints")

**Example**

The following code illustrates how to disable creating connections with a port.
	
{% highlight razor %}

@using Syncfusion.JavaScript.DataVisualization.Models.Collections
@using Syncfusion.JavaScript.DataVisualization.DiagramEnums 
@using Syncfusion.JavaScript.DataVisualization.Models.Diagram

@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
	.Nodes(node => {
		node.Add(new BasicShape(){
			Name = "Node1",
			Ports = new Collection(){new Port(){ Constraints = PortConstraints.None }}
		});
	})
)

{% endhighlight %}

## SelectorConstraints

Selector visually represents the selected elements with certain editable thumbs. The visibility of the thumbs can be controlled with selector constraints. The part of selector is categorized as follows.

* Resizer
* Rotator
* User handles

For more information about Selector contraints, refer to [Selector Constraints](/js/api/global#selectorconstraints "Selector Constraints")

**Example**

The following code illustrates how to hide rotator.

{% highlight razor %}

@using Syncfusion.JavaScript.DataVisualization.DiagramEnums 
@using Syncfusion.JavaScript.DataVisualization.Models.Diagram

@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
	@*Hides rotator*@
	.SelectedItems(new SelectedItems(){ Constraints = SelectorConstraints.All &~ SelectorConstraints.Rotator})
)

{% endhighlight %}

## SnapConstraints

Snap Constraints control the visibility of gridlines and enable/disable snapping. Snap constraints allow to set the following behaviors.

* Show only horizontal or vertical gridlines
* Show both horizontal and vertical gridlines
* Snap to either horizontal or vertical gridlines
* Snap to both horizontal and vertical gridlines

For more information about snap constraints, refer to [Snap Constraints](/js/api/global#snapconstraints "Snap Constraints")

**Example**

The following code illustrates how to show only horizontal gridlines.

{% highlight razor %}

@using Syncfusion.JavaScript.DataVisualization.DiagramEnums 
@using Syncfusion.JavaScript.DataVisualization.Models.Diagram

@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
	@*Shows horizontal gridlines*@
	.SnapSettings(e => e.SnapConstraints(SnapConstraints.ShowHorizontalLines))
)

{% endhighlight %}

## Inherit behaviors

Some of the behaviors can be defined through both the specific object(node/connector) and Diagram. When the behaviors are contradictorily defined through both, the actual behavior is set through inherit options.

The following code example illustrates how to inherit the line bridging behavior from the Diagram model.

{% highlight razor %}

@using Syncfusion.JavaScript.DataVisualization.DiagramEnums 
@using Syncfusion.JavaScript.DataVisualization.Models.Diagram

@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
	@*Enables/disables line bridging based on the Diagram constraints*@
	.Connectors(conn =>{
		conn.Add(new Connector() {
			Name = "Connector",
			SourcePoint = new DiagramPoint(100f, 100f),
			TargetPoint = new DiagramPoint(200f, 200f),
			
			@*Sets to inherit bridging from model*@
			Constraints = ConnectorConstraints.Default | ConnectorConstraints.InheritBridging
		});
	})
)

@using Syncfusion.JavaScript.DataVisualization.DiagramEnums 
@using Syncfusion.JavaScript.DataVisualization.Models.Diagram

@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")	
	@*Enables line bridging for all connectors*@
	.Constraints(DiagramConstraints.Default | DiagramConstraints.Bridging)
)

{% endhighlight %}

## Bitwise Operations

**Bitwise Operations** are used to manipulate the flagged enumerations [enum]. In this section, Bitwise Operations are illustrated by using node Constraints. The same is applicable while working with Node Constraints, Connector Constraints, or Port Constraints.

### Add Operation

You can **add** or **enable** multiple values at a time by using **Bitwise** ‘\|’ (OR) **operator**.

{% highlight c# %}

node.Constraints = NodeConstraints.Select | NodeConstraints.Rotate;

{% endhighlight %}

In the above example, you can do both the selection and rotation.

### Remove Operation

You can **remove** or **disable** values by using **Bitwise** ‘&~’ (XOR) **operator**.

{% highlight c# %}

node.Constraints = node.Constraints & ~(NodeConstraints.Rotate);

{% endhighlight %}

In the above example, **Rotation** is disabled but other constraints are enabled.

### Check Operation

You can check any value by using **Bitwise** ‘&’ (AND) **operator**.

{% highlight c# %}

if ((node.Constraints & (NodeConstraints.Rotate)) == (NodeConstraints.Rotate))

{% endhighlight %}

In the above example, you can check whether the rotate constraints are enabled in a Node. When Node constraints have rotate constraints, the expression returns a rotate constraint.
