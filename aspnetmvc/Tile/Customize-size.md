---
layout: post
title: Customize size | Tile | ASP.NET MVC | Syncfusion
description: customize size
platform: ejmvc
control: Tile
documentation: ug
---

# Customize size

You can customize the size of the Tile by using TileSize property. The following built-in tile sizes are supported.

1. Medium
2. Small
3. Large
4. Wide

The default TileSize value is set to Small.

Refer to the following code examples.

{% highlight CSHTML %}

@Html.EJ().Tile("tile").Text("Pictures").ImagePosition(TileImagePosition.Center).TileSize(TileSize.Medium).ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/pictures.png ")


{% endhighlight %}


![](Customize-size_images/Customize-size_img1.png)



