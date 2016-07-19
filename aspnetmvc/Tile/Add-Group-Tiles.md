---
layout: post
title: Add Group Tiles | Tile | ASP.NET MVC | Syncfusion
description: add group tiles
platform: ejmvc
control: Tile
documentation: ug
---

# Add Group Tiles

To make a Tile as grouped tile, you can use the following mentioned pre-defined classes.

<table>
<tr>
<th>
Class Name</th><th>
Explanation</th></tr>
<tr>
<td>
e-tile-group</td><td>
To group the column elements</td></tr>
<tr>
<td>
e-tile-column</td><td>
To align the tile in column manner</td></tr>
<tr>
<td>
e-tile-small-col-2</td><td>
To align the small size tiles</td></tr>
</table>
To render group tile, refer to the following code example.

{% highlight CSHTML %}

<div class="group">

    <div class="column">

           <!— Add tile control here -->

    </div>

</div>


{% endhighlight %}


To render column grouped tile, you need to render the number of tiles inside a <div> element with class ‘column’. Then that column group element is appended to a <div> with class ‘group’.     

To render small-col-2 grouped tile, you need to render the number of tiles inside a <div> element with class ‘small-col-2’. Then that small-col-2 group element is appended to a <div> with class ‘column’. Then you need to append those column inside the main group <div> element.                                                     

 Refer the following code examples.

{% highlight CSHTML %}

 <div class="e-tile-group">

     <div class="e-tile-column">

        @Html.EJ().Tile("tile1").ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/alerts.png").TileSize(TileSize.Medium).Caption(caption => caption.Enabled(true).Text("Alert"))

        @Html.EJ().Tile("tile2").ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/pictures.png").TileSize(TileSize.Medium).Caption(caption => caption.Enabled(true).Text("pictures"))

        @Html.EJ().Tile("tile3").ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/camera.png").TileSize(TileSize.Medium).Caption(caption => caption.Enabled(true).Text("Camera"))

        @Html.EJ().Tile("tile4").ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/messages.png").TileSize(TileSize.Medium).Caption(caption => caption.Enabled(true).Text("Messages"))

        @Html.EJ().Tile("tile5").ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/games.png").TileSize(TileSize.Wide).Caption(caption => caption.Enabled(true).Text("Games"))

     </div>

     <div class="e-tile-column">

        @Html.EJ().Tile("tile6").ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/map.png").TileSize(TileSize.Medium).Caption(caption => caption.Enabled(true).Text("Map"))

        @Html.EJ().Tile("tile7").ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/bing.png").TileSize(TileSize.Medium).Caption(caption => caption.Enabled(true).Text("Bing"))

        @Html.EJ().Tile("tile8").ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/favs.png").TileSize(TileSize.Medium).Caption(caption => caption.Enabled(true).Text("Health"))

        @Html.EJ().Tile("tile9").ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/people_2.png").TileSize(TileSize.Medium).ImagePosition(TileImagePosition.Fill).Caption(caption => caption.Enabled(true).Text("Peoples"))

        @Html.EJ().Tile("tile10").ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/weather.png").TileSize(TileSize.Medium).Caption(caption => caption.Enabled(true).Text("Weather"))

        @Html.EJ().Tile("tile11").ImageUrl("http://js.syncfusion.com/UG/Web/Content/tile/music.png").TileSize(TileSize.Medium).Caption(caption => caption.Enabled(true).Text("Music"))

    </div>

</div>


{% endhighlight %}



![](Add-Group-Tiles_images/Add-Group-Tiles_img1.png)



