---
layout: post
title: Customize-size
description: customize size
platform: ejmvc
control: Tile
documentation: ug
---

## Customize size

You can customize the size of the Tile by using TileSize property. The following built-in tile sizes are supported.

1. Medium
2. Small
3. Large
4. Wide

The default TileSize value is set to Small.

Refer to the following code examples.



@Html.EJ().Tile("tile").Text("Pictures").ImagePosition(TileImagePosition.Center).TileSize(TileSize.Medium).ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/pictures.png ")





{{ '![](Customize-size_images/Customize-size_img1.png)' | markdownify }}
{:.image }


