---
layout: post
title: RTL
description: rtl
platform: ejmvc
control: RichTextEditor
documentation: ug
---

# RTL

RTL control supports right-to-left functionality and features for languages that work in a right-to-left way for entering, editing, and displaying text. You can change your display to read right-to-left. Arabic and Hebrew are written from right to left. The customers with writing style from right-to left can use this feature in RTE. You can achieve this in the editing area by using the enableRTL property. Setting this property to “True” allows you to write in the right-to-left format. Position of the toolbars also changes from right to left.

1. Add the following code to the script section in your CSHTML page to initialize the RTE

{% highlight html %}

	\\ Add the following code in your view page to render the RTE.

	@{Html.EJ().RTE("rteSample").Width("850px").ContentTemplate(@<p></p>).EnableRTL(true).Render(); }

{% endhighlight %}

![](RTL_images/RTL_img1.png)

The following screenshot displays the output.