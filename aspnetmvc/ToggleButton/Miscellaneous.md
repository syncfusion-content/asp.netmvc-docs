---
layout: post
title: Miscellaneous | ToggleButton | ASP.NET MVC | Syncfusion
description: miscellaneous
platform: ejmvc
control: ToggleButton
documentation: ug
---

# Miscellaneous

## ShowRoundedCorner 

It sets the corner of Toggle Button in rounded shape. The Toggle Button, by default doesn’t have rounded corner. To set rounded corner, you can enable ShowRoundedCorner property.

The following steps explains you the details about rendering the Toggle Button with Rounded corner support. 

1. In the View page, add the following button elements to configure Toggle Button widget.

{% highlight CSHTML %}

@*Add the code in CSHTML page to configure the widget and initialize the control*@

<div class="one">

	@*set rounded corner for toggle button*@       
	@Html.EJ().ToggleButton("toggleButton_roundedCorner").Size(ButtonSize.Small).ShowRoundedCorner(true).ContentType(ContentType.TextAndImage).DefaultText("Play").ActiveText("Next").DefaultPrefixIcon("e-icon e-mediaplay").ActivePrefixIcon("e-icon e-medianext")       

</div>

{%  endhighlight %}

Execute the above code to render the following output.

![](Miscellaneous_images/Miscellaneous_img1.png)

Toggle button with Rounder corner
{:.caption}

## PreventToggle

This property is used to prevent the state change of Toggle Button when it is clicked. When you set PreventToggle property as true, then the state of the Toggle Button is not changed even though it is clicked. Default value of PreventToggle is false.

The following steps explains you the details about rendering the Toggle Button with PreventToggle property enabled.

1. In the View page, add the following button elements to configure Toggle Button widget.

{% highlight CSHTML %}

@*Add the code in CSHTML page to configure the widget and initialize the control*@

<div class="one">

	@* set prevent toggle property for preventing states*@       

	 @Html.EJ().ToggleButton("toggleButton_preventToggle").Size(ButtonSize.Small).ContentType(ContentType.TextAndImage).DefaultText("Play").ActiveText("Next").DefaultPrefixIcon("e-icon e-mediaplay").ActivePrefixIcon("e-icon e-medianext").PreventToggle(true)       

</div>
	
{% endhighlight %}

Execute the above code to render the following output.



![](Miscellaneous_images/Miscellaneous_img2.png)

Toggle button with prevent Toggle
{:.caption}



