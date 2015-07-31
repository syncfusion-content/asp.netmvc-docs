---
layout: post
title: Text-Configuration
description: text configuration
platform: ejmvc
control: Tile
documentation: ug
---

# Text Configuration

ShowText property is used to show or hide the Tile caption. By default, the ShowText property is to true on initialization.Text property is used to set the caption of a Tile as a Text on initialization. TextAlignment property is used to align the Tile text as Normal on initialization. The possible position values for TextAlignment are as follows: 

1. Normal
2. Left
3. Right
4. Center



Refer to the following code examples.


{% highlight html %}

@Html.EJ().Tile("tile").Text("Camera").TextAlignment(TextAlignment.Center).ImagePosition(TileImagePosition.Center).TileSize(TileSize.Medium).ImageUrl("http://js.syncfusion.com/UG/web/Content/tile/camera.png")

{% endhighlight %}



![](Text-Configuration_images/Text-Configuration_img1.png)



