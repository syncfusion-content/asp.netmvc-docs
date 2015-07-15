---
layout: post
title: Tools
description: tools
platform: ejmvc
control: Diagram
documentation: ug
---

## Tools

When interacting on a diagram’s surface, the Tool property decides the action to be performed. When more than one tool is applied, by using bitwise OR, the necessary tool is picked based on the interaction gesture, the value of Tool property and precedence.

_Tools_

<table>
<tr>
<td>
Precedence</td><td>
Tools</td><td>
Description</td></tr>
<tr>
<td>
1st </td><td>
ContinuesDraw</td><td>
Allows you to draw the nodes or connectors continuously. </td></tr>
<tr>
<td>
2nd </td><td>
DrawOnce</td><td>
Allows you to draw single node or connector.</td></tr>
<tr>
<td>
3rd </td><td>
ZoomPan</td><td>
Allows you to pan or zoom diagram.</td></tr>
<tr>
<td>
4th </td><td>
MultipleSelect</td><td>
Allows you to select multiple nodes and connectors</td></tr>
<tr>
<td>
5th </td><td>
SingleSelect</td><td>
Allows you to select individual nodes or connectors.</td></tr>
<tr>
<td>
6th </td><td>
None</td><td>
Disables all tools</td></tr>
</table>
 Single Tool Selection

The following code illustrates how to enable SingleSelect tool.

{% highlight c# %}

[EJMVC]

[Controller]

//Enables SingleSelection 

DiagramProperties DiagramContent = new DiagramProperties();

DiagramContent.Tool = Tool.SingleSelect;



{% endhighlight %}

Multiple Diagram Tools

Diagram provides support to enable multiple tools at a time. The following code illustrates how to enable ZoomPan and SingleSelect tool at the same time.



{% highlight c# %}

[EJMVC]

[Controller]

//Enables Multiple Selection

DiagramProperties model = new DiagramProperties();

model.Tool= Tool.SingleSelect| Tool.ZoomPan;



{% endhighlight %}

### Drawing Tools

Drawing tool allows you to draw any node during runtime by clicking and dragging the Diagram page. To draw a node by using drawing tool, the required node is assigned to the drawType property.

Rectangle Tool

The following code example illustrates how to draw the rectangle shape at run time. When drawing tool is defined and activated, you can click and drag the page to draw the defined node.

{% highlight html %}

[JS]



<script type="text/Javascript">



var diagram = $("#diagram").ejDiagram("instance");



//Defines the node to be drawn by using drawing tool

diagram.model.drawType = { 

	type: ej.datavisualization.Diagram.Shapes.Basic, 

shape: "rectangle",

fillColor:"#fcbc7c",

borderColor:"#f89b4c",

labels: [{ "text": "Rectangle",fontColor:"white" }]

};



//Activates the drawing tool

diagram.update({ 

tool: ej.datavisualization.Diagram.Tool.DrawOnce 

})



</script>



{% endhighlight %}



{ ![](Tools_images/Tools_img1.png) | markdownify }
{:.image }


Similarly, you can draw any node by using drawing tool, by assigning the required node to diagram.model.drawType property.

Connector Tool:

To draw a connector, the required connector type is assigned to the drawType property.

StraightLine:

The following code example illustrates how to draw a straight connector at runtime.

{% highlight html %}

[JS]



<script type="text/Javascript">



var diagram = $("#diagram").ejDiagram("instance");



//Defines the connector to be drawn by using drawing tool

diagram.model.drawType = { 

	type:"straightLine", 

};



//Activates the drawing tool

diagram.update({ 

tool: ej.datavisualization.Diagram.Tool.DrawOnce 

})



</script>



{% endhighlight %}



{ ![http://help.syncfusion.com/ug/js/ImagesExt/image682_23.jpg](Tools_images/Tools_img2.jpeg) | markdownify }
{:.image }


