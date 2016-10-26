---
layout: post
title: RTL support | ToggleButton | ASP.NET MVC | Syncfusion
description: rtl support
platform: ejmvc
control: ToggleButton
documentation: ug
---

# RTL support

In some cases, it is necessary to use right to left alignment. You can render RTL support by using EnableRTL property. In RTL mode, when there is more than one content (image/text, image/image) in button, then the content is aligned in right to left format. For example, when text is in left and image is in right position, after applying right to left alignment these positions are interchanged.

The following steps explains you the details about rendering the Toggle Button with Right to left alignment support.

1. In the View page, add the following button elements to configure Toggle Button widget.


{% highlight CSHTML %}

//Add the code in CSHTML page to configure the widget and initialize the control

<div class="one">

	@*enable right to left alignment*@

	@Html.EJ().ToggleButton("toggleButton_rtl").Size(ButtonSize.Small).ShowRoundedCorner(true).ContentType(ContentType.TextAndImage).DefaultText("Play").ActiveText("Next").DefaultPrefixIcon("e-icon e-mediaplay").ActivePrefixIcon("e-icon e-medianext").EnableRTL(true)       

</div>

{% endhighlight %}

In above mentioned code example PrefixIcon property is used and the icon that is to be on left side, (before text) is rendered on right side as EnableRTL property is used with PrefixIcon. Consequently, the alignment is changed in right to left order.

Output of above steps



![](RTL-support_images/RTL-support_img1.png)

Toggle button with RTL support
{:.caption}
