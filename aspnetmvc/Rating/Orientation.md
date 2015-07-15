---
layout: post
title: Orientation
description: orientation
platform: ejmvc
control: Rating
documentation: ug
---

## Orientation

Rating provides support for Vertical orientation. By default Rating renders with Horizontal orientation. You can change the orientation by the Orientation property.

The following code example is used to render the Rating control with Verticalorientation.

Add the following code in your view page to render the Rating with customizedOrientation.



[CSHTML]

// Add the following code example to the corresponding CSHTML page to render Rating with customized orientation.



&lt;div id="container" style="border: 1px solid black; width: 300px; padding: 2px"&gt;

    &lt;table&gt;

        &lt;tr&gt;

            <td valign="top">Rating:

            &lt;/td&gt;

            &lt;td&gt;

                @Html.EJ().Rating("Rating").Orientation(Orientation.Vertical)

            &lt;/td&gt;

        &lt;/tr&gt;             

    &lt;/table&gt;

&lt;/div&gt;





The following screenshot illustrates the Rating with Vertical orientation.

{ ![](Orientation_images/Orientation_img1.png) | markdownify }
{:.image }


