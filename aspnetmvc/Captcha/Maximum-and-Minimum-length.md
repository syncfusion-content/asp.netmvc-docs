---
layout: post
title: Maximum-and-Minimum-length
description: maximum and minimum length
platform: ejmvc
control: Captcha
documentation: ug
---

## Maximum and Minimum length

You can limit the Captcha characters by MinimumLength and MaximumLength property. MaximumLength property is used to define the maximum number of characters to be displayed in the image. MinimumLength sets minimum number of captcha characters need to display.

The following code example is used to render the Captcha with Minimum and Maximum length support.

1. Add the following code example to the corresponding CSHTML page to render Captcha with Minimum and Maximum length support.



[CSHTML]

@Html.EJ().Captcha("captcha").MaximumLength(6).MinimumLength(5)



2. The following screenshot illustrates the Captcha with Minimum and Maximum length support. 

{ ![](Maximum-and-Minimum-length_images/Maximum-and-Minimum-length_img1.png) | markdownify }
{:.image }


