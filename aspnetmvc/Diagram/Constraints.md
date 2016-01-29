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

{% highlight c# %}
public ActionResult Index()
{
    DiagramProperties model = new DiagramProperties();
	//Set Diagram in read-only mode
	model.Constraints = DiagramConstraints.Default &~ DiagramConstraints.PageEditable;
	
    ViewData["diagramModel"] = model;
    return View();
}
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

{% highlight c# %}
public ActionResult Index()
{
    DiagramProperties model = new DiagramProperties();
	//Disables rotation
	BasicShape task1 = new BasicShape() {
		Constraints = NodeConstraints.Default &~ NodeConstraints.Rotate 
	};
	model.Nodes.Add(task1);
    ViewData["diagramModel"] = model;
    return View();
}
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

{% highlight c# %}
public ActionResult Index()
{
    DiagramProperties model = new DiagramProperties();
	//Disables Selection
	Connector connector1 = new Connector() {
		Constraints = ConnectorConstraints.Default &~ ConnectorConstraints.Select
	};
	model.Connectors.Add(connector1);
    ViewData["diagramModel"] = model;
    return View();
}
{% endhighlight %}

## PortConstraints

You can enable or disable certain behaviors of Port. They are as follows.

* Connect

For more information about port contraints, refer to [Port Constraints](/js/api/global#portconstraints "Port Constraints")

**Example**

The following code illustrates how to disable creating connections with a port.
	
{% highlight c# %}
public ActionResult Index()
{
    DiagramProperties model = new DiagramProperties();
	BasicShape node1 = new BasicShape(){
		Name = "Node1", 
		//Defines ports for task2
		Ports = new Collection() {
			new Port(){ Constraints = PortConstraints.None },
		}
	};
	model.Nodes.Add(node1);
    ViewData["diagramModel"] = model;
    return View();
}
{% endhighlight %}

## SelectorConstraints

Selector visually represents the selected elements with certain editable thumbs. The visibility of the thumbs can be controlled with selector constraints. The part of selector is categorized as follows.

* Resizer
* Rotator
* User handles

For more information about Selector contraints, refer to [Selector Constraints](/js/api/global#selectorconstraints "Selector Constraints")

**Example**

The following code illustrates how to hide rotator.

{% highlight c# %}
public ActionResult Index()
{
    DiagramProperties model = new DiagramProperties();
	//Hides rotator
	model.SelectedItems = new SelectedItems(){
		Constraints = SelectorConstraints.All &~ SelectorConstraints.Rotator
	}; 
    ViewData["diagramModel"] = model;
    return View();
}
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

{% highlight c# %}
public ActionResult Index()
{
    DiagramProperties model = new DiagramProperties();
	model.SnapSettings = new SnapSettings()
	{
		SnapConstraints = SnapConstraints.ShowHorizontalLines
	};
    ViewData["diagramModel"] = model;
    return View();
}
{% endhighlight %}

## Inherit behaviors

Some of the behaviors can be defined through both the specific object(node/connector) and Diagram. When the behaviors are contradictorily defined through both, the actual behavior is set through inherit options.

The following code example illustrates how to inherit the line bridging behavior from the Diagram model.

{% highlight razor %}
public ActionResult Index()
{
    DiagramProperties model = new DiagramProperties();
	Connector connector1 = new Connector() {
		Name = "Connector",
		SourcePoint = new DiagramPoint(100f, 100f),
		TargetPoint = new DiagramPoint(200f, 200f),
		
		//Sets to inherit bridging from model
		Constraints = ConnectorConstraints.Default | ConnectorConstraints.InheritBridging
	};
	model.Connectors.Add(connector1);
	
	//Enables line bridging for all connectors
	model.Constraints = DiagramConstraints.Default | DiagramConstraints.Bridging;
    ViewData["diagramModel"] = model;
    return View();
}
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
