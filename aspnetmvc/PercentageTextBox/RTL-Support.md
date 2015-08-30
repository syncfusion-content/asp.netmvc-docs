---
layout: post
title: RTL-Support
description: rtl support
platform: ejmvc
control: PercentageTextBox
documentation: ug
---

# RTL Support

PercentageTextBox provides RTL (Right-To-Left) support. The alignment of PercentageTextBox can be changed from Left-To-Right into Right-To-Left.

## Enable RTL

In the View page add PercentageTextBox helper, and configure the EnableRTL property.

{% highlight js %}

@Html.EJ().PercentageTextbox("percentage").Value("22").EnableRTL(true)

{% endhighlight %}

Output of PercentageTextBox when EnableRTL is “True” is as follows. 

![](RTL-Support_images/RTL-Support_img1.png)



