---
layout: post
title: getting started
description: getting started
platform: ejmvc
control: Signature
documentation: ug
---

# Getting Started

The Signature simplifies creation of a signature capture in a browser, allowing a user to draw a signature using mouse or touch.

This section explains briefly about how to create a **Signature** control in your application with ASP.NET MVC application by the step-by-step instructions. The following screenshot demonstrates the functionality of Signature widget.

![](getting_started_images\gettingstarted_img1.png)

## Creating your first Signature in MVC application

Create an MVC Project and add necessary assemblies, scripts and CSS files given in [MVC-Getting Started](http://help.syncfusion.com/aspnetmvc/getting-started) Documentation.

Add Signature control using the helper from EJ namespace.

{% highlight razor %}

  @Html.EJ().Signature("mysign").Height("400px")

{% endhighlight %}

Execute the code to render a Signature widget as follows.

![](getting_started_images\gettingstarted_img2.png)

## Adjusting Signature Size

We can customize the width and height of the Signature by width and height properties. These properties completely depend on signature canvas. The width and height are adjusted within the signature canvas.

The following code example is used to render the Signature control with customized width and height.

{% highlight razor %}

  @Html.EJ().Signature("mysign").Height("500px").Width("200px")

{% endhighlight %}

The following screenshot illustrates signature with customized width and height.

![](getting_started_images\gettingstarted_img3.png)



