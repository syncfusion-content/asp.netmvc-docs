---
layout: post
title: Title-Customization
description: title customization
platform: ejmvc
control: TagCloud
documentation: ug
---

# Title Customization

## ShowTitle

The TagCloud items are displayed with a Title element by default. ShowTitle is a Boolean type, which allow us to Hide or Show the Title. This property is set true by default.

### How to disable title in TagCloud

The following step explains you on how to configure title for a TagCloud.

{% highlight c# %}

<%-- Configure datasource referring local data binding section and assign it to datasource property -- %>

@Html.EJ().TagCloud("tagcloud").Datasource((IEnumerable<WebsiteCollection>)ViewBag.datasource)
.TagCloudFields(tag => tag.Text("Text").Url("Url")
.Frequency("Frequency"))
.ShowTitle(false)

{% endhighlight %}

The following screenshot illustrates a TagCloud control when you set false to ShowTitle,

![](Title-Customization_images/Title-Customization_img1.png)


## Title

TagCloud widget allows us to set a custom Title text by using the Title property. By default Title property is set to string value “Title”.

### Defining title text for TagCloud

The following step explain to us on how to configure Title for a TagCloud.

{% highlight c# %}

@Html.EJ().TagCloud("tagcloud").Datasource((IEnumerable<WebsiteCollection>)ViewBag.datasource)
.TagCloudFields(tag => tag.Text("Text").Url("Url")
.Frequency("Frequency"))
.Title("Tech sites")

{% endhighlight %}

The following screenshot illustrates the TagCloud control with customized title text.

![](Title-Customization_images/Title-Customization_img2.png)

## TitleImage

TagCloud widget provides TitleImage to set an image for the title. You can set the desired image URL to TitleImage property.

### Defining Title Image for TagCloud

The following step explains us to configure TitleImage for a TagCloud.

{% highlight c# %}

<%-- Configure datasource referring local data binding section and assign it to datasource property -- %>

@Html.EJ().TagCloud("tagcloud").Datasource((IEnumerable<WebsiteCollection>)ViewBag.datasource)
.TagCloudFields(tag => tag.Text("Text").Url("Url")
.Frequency("Frequency")).Title("Tech sites")
.TitleImage("http://js.syncfusion.com/demos/web/images/waitingpopup/js_logo.png")

{% endhighlight %}

1. Using CSS class you can resize the Title image content as follows.

   ~~~ html

        <style type="text/css">

			.e-title-img {

            height::35px;

            width:35px;

			}

		</style>

   ~~~
   {:.prettyprint }

	The following screenshot illustrates the TagCloud control with customized title image.

	![](Title-Customization_images/Title-Customization_img3.png)



