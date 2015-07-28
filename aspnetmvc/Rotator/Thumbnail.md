---
layout: post
title: Thumbnail
description: thumbnail 
platform: ejmvc
control: Rotator
documentation: ug
---

# Thumbnail 

This feature implements Thumbnail in Rotator control. You can view or access any of the Rotator items instantly. All the images are given as Thumb Element to use this feature. 

The property ShowThumbnail is Boolean type, which allow us to Show or Hide the Thumbnail in Rotator control. Thumbnail is used to navigate between slides. Thumbnail supports only single slide transition. You must specify the source for thumbnail elements through the ThumbnailSourceID property. The default value is ‘false’.

The property ThumbnailSourceID specifies the source for thumbnail elements. The default value is null. The value set to this property is object. 

You can refer the following code example of Thumbnail in Rotator.

{% highlight html %}

<ul id="slide" style="display: none">

    <li>

        <img src="@Url.Content("~/Images/rotator/green.jpg")" title="Green" /></li>

    <li>

        <img src="@Url.Content("~/Images/rotator/snow.jpg")" title="Snow" /></li>

    <li>

        <img src="@Url.Content("~/Images/rotator/wheat.jpg")" title="Wheat" /></li>

    <li>

        <img src="@Url.Content("~/Images/rotator/tablet.jpg")" title="Tablet" /></li>

    <li>

        <img src="@Url.Content("~/Images/rotator/sea.jpg")" title="Sea" /></li>

    <li>

        <img src="@Url.Content("~/Images/rotator/bread.jpg")" title="Bread" /></li>

</ul>

@Html.EJ().Rotator("slidercontent").Items(itemElement =>

                       {

                           itemElement.Add().ContentTemplate(@<div>

                               <img class="image" src="@Url.Content("~/Images/rotator/green.jpg")" />

                           </div>);

                           itemElement.Add().ContentTemplate(@<div>

                               <img class="image" src="@Url.Content("~/Images/rotator/snow.jpg")"/>

                           </div>);

                           itemElement.Add().ContentTemplate(@<div>

                               <img class="image" src="@Url.Content("~/Images/rotator/wheat.jpg")" />

                           </div>);

                           itemElement.Add().ContentTemplate(@<div>

                               <img class="image" src="@Url.Content("~/Images/rotator/tablet.jpg")" />

                           </div>);

                           itemElement.Add().ContentTemplate(@<div>

                               <img class="image" src="@Url.Content("~/Images/rotator/sea.jpg")" />

                           </div>);

                           itemElement.Add().ContentTemplate(@<div>

                               <img class="image" src="@Url.Content("~/Images/rotator/bread.jpg")" />

                           </div>);

                       }).SlideWidth("600px").SlideHeight("350px").ShowThumbnail(true).ThumbnailSourceID("slide")          

{% endhighlight %}

![](Thumbnail_images/Thumbnail_img1.png)