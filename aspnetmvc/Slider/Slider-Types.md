---
layout: post
title: Slider-Types
description: slider types
platform: ejmvc
control: Slider
documentation: ug
---

## Slider Types

This feature allows you to specify the type of Slider. There are three different types of Slider, Default Slider, Min-Range Slider and Range Slider. By default, Default Slider renders. You can use the SliderType property to choose the type of Slider. Data type of this property is “Enum”

Both Default Slider and Min-Range Slider have same behaviour that is used to select a single value. In Min-Range Slider, a shadow is considered from the start value to current handle position. But Range Slider contains two handles that is used to select a range of values and a shadow is considered in between the two handles.

Possible Slider types are as follows,

_Property Table for MVC_

<table>
<tr>
<td>
Property</td><td>
Allowed values</td><td>
Description</td></tr>
<tr>
<td rowspan = "3">
SliderType</td><td>
Default (default value)</td><td>
It is the default Slider type. It helps to select a single value. </td></tr>
<tr>
<td>
MinRange</td><td>
Use this Slider to select a single value; Displays shadow from the start value to the current value.</td></tr>
<tr>
<td>
Range</td><td>
Use this Slider to select a range of values; Displays shadow in-between the selection range.</td></tr>
</table>


The following steps explains you on how to configure the SliderType property to display Range Slider and MinRange Slider.

1. In an VIEW page, specify the helper elements to render the RangeSlider and MinRangeSlider.





[_cshtml]

/ / Add this code in your view page

@(Html.EJ().Slider("minSlider").SliderType(SlideType.MinRange).Value("60").Width("500"))



@(Html.EJ().Slider("rangeSlider").SliderType(SlideType.Range).Values("30,60").Width("500"))



Execute the above code example to render the following output.



{ ![C:/Users/Gopal Lakshmanan/Desktop/ss3.PNG](Slider-Types_images/Slider-Types_img1.png) | markdownify }
{:.image }


_Shows different Slider types (Range and Min-Range sliders)_

