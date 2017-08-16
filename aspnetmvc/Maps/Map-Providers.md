---
layout: post
title: Map Providers
description: Learn how to customize map providers
platform: ejmvc
control: Maps
documentation: ug
---

# Map Providers

Map control support map providers such as OpenStreetMap that can be added to any layers in maps.

## Open Street Map

OpenStreetMap is a map of the entire world. The OpenStreetMap allows you to view, edit and use geographical data in a collaborative way from any place on the Earth.

### Enable OSM

You can enable this feature by setting the LayerType property value as "OSM".

{% highlight CSHTML %}

	@(Html.EJ().Map("map")

	.Layers(layer =>

	{

		layer.LayerType(Syncfusion.JavaScript.DataVisualization.Models.LayerType.OSM)

		.UrlTemplate("http://a.tile.openstreetmap.org/level/tileX/tileY.png”);

	})           

	) 

{% endhighlight %}

### URL Template

The `UrlTemplate` property determines the format of tile map. You can specify the template for the tile layer. 


![](Map-Providers_images/Map-Providers_img1.png)


## Bing Map

Bing Map is a key feature in accessing the external geospatial imagery services for deep-zoom satellite view. 

### Enable Bing Maps

You can enable this feature by defining the `LayerType` as “Bing”.



{% highlight CSHTML %}

	@(Html.EJ().Map("map")

	.Layers(layer =>

	{

		layer.LayerType(Syncfusion.JavaScript.DataVisualization.Models.LayerType.Bing)

		.Key("// ...bingMapKey”).Add();

	})           

	) 
{% endhighlight %}

### Key

The bing Map Key is provided as input to this `key` property. The Bing Map key can be obtained from [http://www.microsoft.com/maps/create-a-bing-maps-key.aspx](http://www.microsoft.com/maps/create-a-bing-maps-key.aspx). 


![](Map-Providers_images/Map-Providers_img2.png)


