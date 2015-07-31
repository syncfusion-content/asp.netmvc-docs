---
layout: post
title: RTL-Support
description: rtl support
platform: ejmvc
control: NumericTextBox
documentation: ug
---

## RTL Support

NumericTextBox provides RTL (Right-To-Left) support. The alignment of NumericTextBox can be changed from Left-To-Right into Right-To-Left.

Enable RTL

In the View page add NumericTextBox helper, and configure the EnableRTL property.



[_cshtml]

@Html.EJ().NumericTextbox("numeric").Value("11").EnableRTL(true)



Output of NumericTextBox when EnableRTL is “True” is as follows. 

{{ '![](RTL-Support_images/RTL-Support_img1.png)' | markdownify }}
{:.image }






_NumericTextBox with enableRTL_

