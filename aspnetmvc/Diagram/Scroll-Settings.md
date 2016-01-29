---
layout: post
title: Read the current scroll status and programmatically pan Diagrams
description: How to read/modify the scroll status of the Diagram?
platform: ejmvc
control: Diagram
documentation: ug
---

# Scroll Settings
The Diagram can be scrolled by using the vertical and horizontal scrollbars. In addition to the scrollbars, you can use mouse wheel to scroll the Diagram. 
Diagram's `ScrollSettings` enables you to read the current scroll status, view port size, current zoom, and zoom factor. It also allows you to scroll the Diagram programmatically. 

## Get current scroll status

Scroll settings allows you to read the scroll status, view port size, and current zoom factor with a set of propeties. To explore those properties, see [Scroll Settings](/aspnetmvc/api/ejDiagram#members:scrollsettings "Scroll Settings")

## Define scroll status
Diagram allows you to pan the Diagram before loading, so that any desired region of a large Diagram is made to view. You can programmatically pan the Diagram with the `HorizontalOffset` and `VerticalOffset` properties of scroll settings. The following code illustrates how to set pan the Diagram programmatically.

{% highlight c# %}

            // To Enables multiple tools
            DiagramProperties Model = new DiagramProperties();
            Model.Height = "400px";
            Model.Width = "400px";
            //Sets horizontal and vertical scroll offsets
            Model.ScrollSettings.HorizontalOffset = 100;
            Model.ScrollSettings.VerticalOffset = 50;
            Model.ScrollSettings.ZoomFactor = 0.2; 

            //Sets page settings
            Model.PageSettings.PageWidth = 500;
            Model.PageSettings.PageHeight = 500;

{% endhighlight %}

In the example given below, the vertical scroll bar is scrolled down by 50px and horizontal scroll bar is scrolled to right by 100px. 

![](/Scroll-Settings_images/Scroll-Settings_img1.png)

## Update scroll status

You can programmatically change the scroll offsets at runtime by using the client side method `update`. The following code illustrates how to change the scroll offsets and zoom factor at runtime.

{% highlight js %}

    var diagram = $("#diagram").ejDiagram("instance");
    var scrollSettings = {
        //Sets scroll status
        horizontalOffset: 200,
        verticalOffset: 200,
        //Sets zoomFactor
        zoomFactor: 0.5
    }

    //Updates scroll settings
    diagram.update({ scrollSettings: scrollSettings });

{% endhighlight %}

## AutoScroll 

Autoscroll feature automatically scrolls the Diagram whenever the node or connector is moved beyond the boundary of the Diagram. So that, it is always visible during dragging, resizing, and multiple selection operations. Autoscroll is automatically triggered when any one of the following is done towards the edges of the Diagram.

* Node dragging, resizing 
* Connection editing
* Rubber band selection
* Label dragging

## Autoscroll border

The Autoscroll border is used to specify the maximum distance between the object and Diagram edge to trigger Autoscroll. The default value is set as 15 for all sides (left, right, top, and bottom) and it can be changed by using the `AutoScrollBorder` property of page settings. The following code example illustrates how to set Autoscroll border. 

{% highlight c# %}

            // To Enables multiple tools
            DiagramProperties Model = new DiagramProperties();
            Model.Height = "400px";
            Model.Width = "400px";
            // Specifies autoscroll border
            Model.PageSettings.AutoScrollBorder.Left = 150;
            Model.PageSettings.AutoScrollBorder.Top = 15;
            Model.PageSettings.AutoScrollBorder.Right = 15;
            Model.PageSettings.AutoScrollBorder.Bottom = 15;

{% endhighlight %}

## Scroll limit

The scroll limit allows you to define the scrollable region of the Diagram. It includes the following options.

* Allows to scroll in all directions without any restriction.
* Allows to scroll within the Diagram content.
* Allows to scroll within the specified scrollable area.

`ScrollLimit` property of scroll settings helps to limit the scrolling. For the accepted values of the scrollLimit, refer to [Scroll Limit](/aspnetmvc/api/ejDiagram#scroll-limit "Scroll Limit").

The following code example illustrates how to specify the scroll limit.

{% highlight c# %}

            // To Enables multiple tools
            DiagramProperties Model = new DiagramProperties();
            Model.Height = "400px";
            Model.Width = "400px";
            //Sets the scroll limit
            Model.PageSettings.ScrollLimit = ScrollLimit.Infinity;

{% endhighlight %}

## Scrollable Area

You can restrict scrolling beyond any particular rectangular area by using the `ScrollableArea` property of scroll settings. To restrict scrolling beyond any custom region, you have to set the `ScrollLimit` as "Limited". The following code example illustrates how to customize scrollable area.

{% highlight c# %}

            // To Enables multiple tools
            DiagramProperties Model = new DiagramProperties();
            Model.Height = "400px";
            Model.Width = "400px";
            //Sets scroll limit as limited
            Model.PageSettings.ScrollLimit = ScrollLimit.Limited;
            //Sets the limited scrollable area
            Model.PageSettings.ScrollableArea.X = 0;
            Model.PageSettings.ScrollableArea.Y = 0;
            Model.PageSettings.ScrollableArea.Width = 500;
            Model.PageSettings.ScrollableArea.Height = 500;

{% endhighlight %}
