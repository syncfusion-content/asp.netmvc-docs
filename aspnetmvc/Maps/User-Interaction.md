---
layout: post
title: User-Interaction
description: user interaction
platform: ejmvc
control: Maps
documentation: ug
---

# User Interaction

Options like zooming, panning and map selection enables the effective interaction on map elements.

## Map Selection

Each shape in the map can be selected and deselected during interaction with shapes. 

The SelectionColor property is used to get or set the selected shape color. The SelectionStroke and SelectionStrokeWidth properties are used to customize the selected shape border.

You can select the shape by tapping on the shape. The Single selection is enabled by the EnableSelection property of shape layer. When EnableSelection is set to false, the shapes cannot be selected. 



{% highlight html %}


@(Html.EJ().Map("maps") 

            .Layers(lr =>

            {

                Lr

                .ShapeData(mapData)

                .ShapeSettings(sp =>

                {

                    sp.StrokeThickness(0.5)

                        .Fill("#9CBF4E")

                        .Stroke("white")

                        .SelectionColor("#BC5353")

                        .SelectionStrokeWidth(2)

                        .SelectionStroke("white");

                })

                .EnableSelection(true)

                .Add();

            })

   )        



{% endhighlight %}



![](User-Interaction_images/User-Interaction_img1.png)


## Zooming

The zooming feature enables you to zoom in and out of the map to show in-depth information. It is controlled by the level property of the map. When the zoom level of the Map control is increased, the map is zoomed in. When the zoom level is decreased, then the map is zoomed out.

### Properties Related to Zooming

The following properties are related to the zooming feature of the Maps control:

1. Level
2. EnableZoom
3. MinValue
4. MaxValue

#### Level

The Level property determines the map’s scale size when zooming. The default value of Level is 1. 

> Note: The  level cannot be less than 1.

#### EnableZoom

The EnableZoom property enables or disables the zooming feature. 

#### MinValue

The MinValue property is used to set the minimum zoom level of the map. 

#### MaxValue

The MaxValue property is used to set the maximum zoom level of the map.



{% highlight html %}

@(Html.EJ().Map("maps") 

            .Layers(lr =>

            {

                lr.ShapeData(mapData)                  

                 .Add();

            })

            .ZoomSettings(zm=>

            {

                zm.EnableZoom(true)

                  .MinValue(1)

                  .MaxValue(20)

                  .Level(1);

            })               



    )      



{% endhighlight %}

### Additional Options to Zoom the Map

Maps can be zoomed using the following options also,

* Using Zoom method.
* Using mouse scroll.
* Using mouse double tap.
* Using shape selection
* Using Position

#### Using Zoom method

You can zoom the Maps using zoom method. The zoom method contains parameter zoom value. The map can be zoomed or scaled based on zoom value parameter.



{% highlight html %}

   $("#map").ejMap("zoom", 2);



{% endhighlight %}



#### Using mouse scroll

You can zoom the map with mouse events using mouse scroll. When the mouse is scrolled up, the map is zoomed in and when the mouse is scrolled down, the map is zoomed out.

#### Using mouse double tap

When the map is double-tapped using mouse, the zoom in operation is performed. 



{{ '![](User-Interaction_images/User-Interaction_img2.png)' | markdownify }}
{:.image }


#### Using Shape Selection

Map shape is zoomed to the whole map area, on the shape selected. Animation can be applied for that zooming, using the EnableAnimation property as true. 

You can enable this feature by setting EnableZoomOnSelection property value as ‘_True_’. 

When EnableZoomOnSelection property is set to true, then, zoom on double click is muted.



{% highlight html %}

@(Html.EJ().Map("maps") 

            // ...

.ZoomSettings(zm=>

            {

                zm.EnableZoomOnSelection(true);

            })                          // ...

 )      



{% endhighlight %}



#### Using Position

Depending on the latitude and longitude, you can zoom the map to the exact position. All locations are considered as latitude and longitude values and the exact location is considered as map coordinates.

The navigateTo is a method defined that allows you to zoom the map control to the given location. This method contains three attributes as follows.

_Attribute Table_

<table>
<tr>
<th>
Attribute</th><th>
Type</th><th>
Description</th></tr>
<tr>
<td>
Latitude</td><td>
Double</td><td>
Latitude point of the position </td></tr>
<tr>
<td>
Longitude</td><td>
Double</td><td>
Longitude point of the postion</td></tr>
<tr>
<td>
Level</td><td>
Double</td><td>
Zoom level of the map</td></tr>
</table>


{% highlight html %}

<script type="text/javascript">

function buttonClick() {

 $("#map").ejMap("navigateTo", 13, 80, 5);

}



</script> 



{% endhighlight %}

### Panning 

The panning feature enables map navigation. The EnablePan property is used to enable or disable the panning support.



{% highlight html %}

@(Html.EJ().Map("maps") 

            // ...

            .EnablePan(true)

                       // ...

 )      



{% endhighlight %}



## Navigation Control

Navigation control is built-in with Maps control. With Navigation control, Maps can be panned in any direction and zoomed. It is possible to show or hide the NavigationControl by EnableNavigation property.

### Structure of Navigation Control

![C:/Users/labuser/Desktop/a.png](User-Interaction_images/User-Interaction_img3.png)


{% highlight html %}


@(Html.EJ().Map("maps") 

            // ...

            .NavigationControl(nc =>

               {

                   nc.EnableNavigation(true);

               })

                       // ...

 )      



{% endhighlight %}



### Zoom with Navigation Control

With Navigation control, the Maps can be zoomed. When you click on the ZoomIn button the Map is zoomed in and when you click on the ZoomOut button the Map is zoomed out.

### Panning with Navigation Control

Maps can be panned with Pan buttons (TopPan button, RightPan button, BottomPan button and LeftPan button). When you click on a particular Pan button the Map is panned on the respective directions.

### Navigation Control Positions

The Navigation control can be positioned in two ways.

* Absolute Position
* Dock Position

### Absolute Position

Based on the margin values of X and Y-axes, the navigation control can be positioned with the help of the X and Y properties available in AbsolutePosition. For positioning the navigation control based on margins corresponding to a map, DockPosition value is set as _‘_None’.

### Dock Position

The navigation control can be positioned in following locations within the container.

* TopLeft
* TopCenter
* TopRight
* CenterLeft
* Center
* CenterRight
* BottomLeft
* BottomRight
* BottomCenter
* BottomRight
* None

You can set this option by using DockPosition property in NavigationControl.



{% highlight html %}


@(Html.EJ().Map("maps") 

            // ...

            .NavigationControl(nc =>

               {

                 nc.EnableNavigation(true)

                   .Orientation(Orientation.Vertical)

                   .AbsolutePosition(new ShapePoint(5, 12))

                   .DockPosition(Syncfusion.JavaScript.

                      DataVisualization.Models.DockPosition.None);

               })

                       // ...

 )      



{% endhighlight %}



