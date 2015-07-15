---
layout: post
title: RTL-support
description: rtl support
platform: ejmvc
control: Slider
documentation: ug
---

## RTL support

Slider includes the Right to Left alignment support. Operations in the Slider is performed from Right to Left.

Enabling RTL

Use the EnableRTL property to enable the RTL support. By default this property is disabled. Data type of this property is “Boolean”.

The following steps explains you on how to enable RTL support in Slider.

1. In an VIEW page, specify the helper elements to render the Range Slider.



[_cshtml]

/ / Add this code in your view page

   @(Html.EJ().Slider("rangeSlider").SliderType(SlideType.Range).Values("25,75")

    .Width("500").EnableRTL(true))





Execute the above code example to render the following output.


{ ![C:/Users/Gopal Lakshmanan/Desktop/s3.PNG](RTL-support_images/RTL-support_img1.png) | markdownify }
{:.image }


