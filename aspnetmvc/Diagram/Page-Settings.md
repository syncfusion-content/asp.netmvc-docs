---
layout: post
title: Page-Settings
description: page settings
platform: ejmvc
control: Diagram
documentation: ug
---

# Page Settings

Page settings enable you to customize the width and height of the Diagram page. The properties of Pagesetting are listed as follows.

_Page settings_

<table>
<tr>
<th>
Properties</th><th>
Data Type</th><th>
Description</th></tr>
<tr>
<td>
PageWidth</td><td>
Int</td><td>
Gets or sets the width of the page</td></tr>
<tr>
<td>
PageHeight</td><td>
Int</td><td>
Gets or sets the height of the page</td></tr>
<tr>
<td>
MultiplePage</td><td>
Boolean</td><td>
Gets or sets whether  multiple page option is enabled or not</td></tr>
<tr>
<td>
PageBorderWidth</td><td>
Int</td><td>
Gets or sets the border width of the page</td></tr>
<tr>
<td>
PageBackgroundColor</td><td>
String</td><td>
Gets or sets the background color of the page</td></tr>
<tr>
<td>
PageBorderColor</td><td>
String</td><td>
Gets or sets the border color of the page</td></tr>
<tr>
<td>
PageMargin</td><td>
Int</td><td>
Gets or sets the  margin of the page</td></tr>
<tr>
<td>
ShowPageBreak</td><td>
Boolean</td><td>
Gets or sets whether  page break option is enabled or not</td></tr>
<tr>
<td>
PageOrientation</td><td>
PageOrientation</td><td>
Gets or sets the orientation of the page</td></tr>
</table>


The following code illustrates how to customize Page Settings

{% highlight c# %}





//Sets page setting properties

model.PageSettings.PageHeight = 300;

model.PageSettings.PageWidth = 450;

model.PageSettings.PageBorderWidth = 4;

model.PageSettings.PageBackgroundColor = "lightBlue";

model.PageSettings.PageBorderColor = "black";

model.PageSettings.PageMargin = 35;

model.PageSettings.ShowPageBreaks = true;

model.PageSettings.MultiplePage = true;

model.PageSettings.PageOrientation = PageOrientation.Portrait;



{% endhighlight %}



![](Page-Settings_images/Page-Settings_img1.png)



## MultiplePage and PageBreaks

When MultiplePage is enabled, the size of the page dynamically increases or decreases in multiples of page width and height and completely fits diagram within the page boundaries. PageBreaks is used as a visual guide to see how pages are split into multiple pages.

![](Page-Settings_images/Page-Settings_img2.png)



## AutoScroll

Autoscroll feature automatically scrolls the Diagram whenever the node or connector is beyond the boundary of the Diagram so that it is always visible during dragging, resizing and multiple selection operations.

Autoscroll is automatically triggered when any one of the following is dragged towards edges of the Diagram.

* Node dragging
* Nodes control points: resizer, rotator
* Connectors control points: end point, segment
* Rubber band selection
* Dropping item from palette

_Properties table_

<table>
<tr>
<th>
Properties</th><th>
Data Type</th><th>
Description</th></tr>
<tr>
<td>
ScrollLimit</td><td>
String</td><td>
Gets or sets the scroll limit of the page</td></tr>
<tr>
<td>
ScrollableArea</td><td>
Object</td><td>
Gets or sets the scrollable region of the page</td></tr>
<tr>
<td>
AutoScrollBorder</td><td>
Object</td><td>
Gets or sets the auto scroll starting point </td></tr>
</table>


## Autoscroll border

The Autoscroll border is used to specify the distance from where the autoscroll is to be enabled when moving the node or connector. The default value is set to 15 for all sides (left, right, top, and bottom).

The following code example illustrates how to set autoscroll border.

{% highlight c# %}



    // Specifies autoscroll border

    model.PageSettings.AutoScrollBorder.Left = 150;

    model.PageSettings.AutoScrollBorder.Right = 15;

    model.PageSettings.AutoScrollBorder.Top = 15;

    model.PageSettings.AutoScrollBorder.Bottom = 15;



{% endhighlight %}

## Scroll limit

The scroll limit allows you to scroll the Diagram page along X and Y axes based on the options specified. 

* By default, the value is set as infinity to scroll in all directions, without any restriction. 
* When scroll limit is set as diagram, you are restricted to scroll the page beyond the Diagram content. 
* By specifying the value as limited, you can set the limit of the scrollable area through scrollable area property. 
 


> Note: Refer to the scrollable area for more details.

The following code example illustrates how to specify scroll limit. 

{% highlight c# %}



//Scrolllimit for Diagram by default

model.PageSettings.ScrollLimit = ScrollLimit.Inifinity;



{% endhighlight %}

## Scrollable Area

You can restrict scrolling beyond a particular rectangular area and the rectangular area is specified by using scrollableArea property. This is applicable only when the scroll limit for the Diagram is specified as limited. 

The following code example illustrates how to customize scrollable area of Diagram.

{% highlight c# %}



//Scrolllimit for diagram as limited

model.PageSettings.ScrollLimit= ScrollLimit.Limited;

  //Sets limit of the scrollable area

  model.PageSettings.ScrollableArea.X = 0;

  model.PageSettings.ScrollableArea.Y = 0;

  model.PageSettings.ScrollableArea.Width = 5000;

  model.PageSettings.ScrollableArea.Height = 5000;



{% endhighlight %}



![](Page-Settings_images/Page-Settings_img4.png)



