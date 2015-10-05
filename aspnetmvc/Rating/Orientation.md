---
layout: post
title: Orientation | Rating | ASP.NET MVC | Syncfusion
description: orientation
platform: ejmvc
control: Rating
documentation: ug
---

# Orientation

Rating provides support for Vertical orientation. By default Rating renders with Horizontal orientation. You can change the orientation by the Orientation property.

The following code example is used to render the Rating control with Verticalorientation.

Add the following code in your view page to render the Rating with customizedOrientation.



{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Rating with customized orientation.

<div id="container" style="border: 1px solid black; width: 300px; padding: 2px">

    <table>

        <tr>

            <td valign="top">Rating:

            </td>

            <td>

                @Html.EJ().Rating("Rating").Orientation(Orientation.Vertical)

            </td>

        </tr>             

    </table>

</div>
{% endhighlight %}




The following screenshot illustrates the Rating with Vertical orientation.

![](Orientation_images/Orientation_img1.png)



