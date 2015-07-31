---
layout: post
title: Image-Configuration
description: image configuration
platform: ejmvc
control: Tile
documentation: ug
---

## Image Configuration

ImagePosition property is used to adjust the position of Tile image at the Center on initialization. The possible values for the ImagePosition are as follows

1. Center
2. Top
3. Bottom
4. Right
5. Left
6. TopLeft
7. BottomRight
8. BottomLeft 
9. Fill

ImageUrl property is used to set the background image for Tile, where the image is given in the path specified by ImageUrl property.

Refer to the following code examples.

@Html.EJ().Tile("tile").Text("Weather").ImagePosition(TileImagePosition.Center).TileSize(TileSize.Wide).ImageUrl("http://js.syncfusion.com/UG/web/Content/tile/Weather_2.png ")





{{ '![](Image-Configuration_images/Image-Configuration_img1.png)' | markdownify }}
{:.image }


You can give images for each tile through css classes by using ImageClass property. You can define your desired styles in the specified class.

Refer to the following code examples.



@Html.EJ().Tile("tile").Text("Pictures").ImagePosition(TileImagePosition.Center).TileSize(TileSize.Medium).ImageClass("pictures")

       <style>

        .pictures

         {

            background: url("http://js.syncfusion.com/UG/web/Content/tile/pictures.png ");

            background-size:30px 30px;

         }

    </style>



{{ '![](Image-Configuration_images/Image-Configuration_img2.png)' | markdownify }}
{:.image }


