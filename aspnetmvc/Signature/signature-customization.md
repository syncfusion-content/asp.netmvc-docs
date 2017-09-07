---
layout: post
title: signature customization
description: signature customization
platform: ejmvc
control: Signature
documentation: ug
---

# Signature Customization

## Stroke color

Signature widget allows you to set the stroke color for the signature stroke using the **StrokeColor** property. When we set our required color, then the signature’s stroke color will be changed.

The following example is used to render the Signature control with stroke color.

In the View page, define the following code.

{% highlight razor %}

@Html.EJ().Signature("mySignature").StrokeColor("red")

{% endhighlight %}

The following screenshot illustrates the Signature with custom defined stroke color.

![](signature-customization_images\strokecolor_img1.png)

## Stroke Width

Signature widget allows you to set the stroke width for the control using the **StrokeWidth** property. When we set our required width, then the signature’s stroke width will be changed.

The following code example is used to render the Signature control with stroke width value.

In the View page, define the following code.

{% highlight razor %}

@Html.EJ().Signature("mySignature").StrokeWidth(5)

{% endhighlight %}

The following screenshot illustrates the Signature with custom defined stroke maximum value.

![](signature-customization_images\strokewidth_img1.png)


## Background color

Signature widget allows you to set the background Color for the control using the **BackgroundColor** property. When we set our required background, then the signature’s background color will be changed automatically.

The following code example is used to render the Signature control with background color.

In the View page, define the following code.

{% highlight razor %}

@Html.EJ().Signature("mySignature").BackgroundColor("grey")

{% endhighlight %}

The following screenshot illustrates the Signature with custom defined background color

![](signature-customization_images\backgroundcolor_img1.png)

## Background Image

Signature widget allows you to set the background image for the control using the **BackgroundImage** property. When we set our required background image, then the signature’s canvas will be changed with the given image.

The following code example is used to render the Signature control with customized background image.

In the View page, define the following code.

{% highlight razor %}

@Html.EJ().Signature("mySignature").BackgroundImage("image.jpg")

{% endhighlight %}

The following screenshot illustrates the Signature with custom defined background image.

![](signature-customization_images\backgroundimage_img1.png)




