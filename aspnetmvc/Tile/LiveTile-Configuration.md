---
layout: post
title: LiveTile-Configuration
description: livetile configuration
platform: ejmvc
control: Tile
documentation: ug
---

## LiveTile Configuration

Live Tiles are used to display the current or up to date information like scores, stocks, weather, etc. You can enable Live Tile using enabled property by setting it to true. Type property allows you to specify the type of animation while updating the information in Tile. There are three types of Tile animation supported: Flip, Slide and Carousel.

ImageUrl property sets background image for Live Tile. This property accepts array values so you can specify the image url’s for all the Tiles that are used in single Live Tile. 

You can specify time interval for each Tile update/animation using UpdateInterval property. Time interval is given in milliseconds. The default value is 2000.

Refer to the following code examples.





@Html.EJ().Tile("tile").LiveTile(live => { live.Enabled(true).Type(LiveTileType.Flip).UpdateInterval(2500).ImageUrl(new string[] { "http://js.syncfusion.com/UG/Web/Content/tile/people_1.png","http://js.syncfusion.com/UG/Web/Content/tile/people_2.png"}); }).ImagePosition(TileImagePosition.Fill).Text("Peoples").TileSize(TileSize.Medium)                    



In ImageTemplateId property, you can give Live Tile images outside the Tile rendering. To achieve this, you are required to give image content inside the element where the path is specified by templateid. You can update the ImageTemplateId dynamically through updateTemplateID public method.

Refer to the following code examples. 





@Html.EJ().Tile("tile").LiveTile(live => { live.Enabled(true).ImageTemplateId(new string[] { "temp1", "temp2" }); }).ImagePosition(TileImagePosition.Fill).Text("Peoples").TileSize(TileSize.Medium)



&lt;div id="temp1" style="background-image:url('http://js.syncfusion.com/ug/web/content/tile/people_1.png'); width:100%; height:100%;"&gt;

&lt;/div&gt;

&lt;div id="temp2" style="background-image: url('http://js.syncfusion.com/ug/web/content/tile/people_2.png'); width:100%; height:100%;"&gt;

&lt;/div&gt;



You can specify the array of images for Live Tile through CSS classes by using ImageClass property and you can define the desired styles in the specified class.

Refer to the following code examples.





@Html.EJ().Tile("tile").LiveTile(live => { live.Enabled(true).ImageClass(new string[] { "people1", "people2" }); }).ImagePosition(TileImagePosition.Fill).Text("Peoples").TileSize(TileSize.Medium)

&lt;style&gt;

    .people1 {

        background-image: url('http://js.syncfusion.com/UG/Web/Content/tile/people_1.png');

    }



    .people2 {

        background-image: url('http://js.syncfusion.com/UG/Web/Content/tile/people_2.png');

    }

&lt;/style&gt;



