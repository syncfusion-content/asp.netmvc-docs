---
layout: post
title: Orientation
description: orientation
platform: ejmvc
control: Slider
documentation: ug
---

## Orientation

This property is used to set the Slider in either horizontal or vertical direction. By default, Slider renders in horizontal direction. Data type of this property is “Enum”.

Possible Slider orientations are as follows,

_Property Table for MVC_

<table>
<tr>
<td>
Property</td><td>
Allowed values</td><td>
Description</td></tr>
<tr>
<td rowspan = "2">
Orientation</td><td>
Vertical</td><td>
Displays the Slider in vertical direction</td></tr>
<tr>
<td>
Horizontal (default value)</td><td>
Displays the Slider in horizontal direction</td></tr>
</table>


The following steps explains you on how to configure the Orientation property.

1. In an VIEW page, add a helper element to render it as a Slider widget.





[_cshtml]

/ / Add this code in your view page

@(Html.EJ().Slider("BasicSlider").Height("150").Width("20").Orientation(Orientation.Vertical))





Execute the above code example to render the following output.

{ ![](Orientation_images/Orientation_img1.png) | markdownify }
{:.image }


_Slider in vertical Orientation_

