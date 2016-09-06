---
layout: post
title: Create and configure color codes for heatmap value. 
description: How to configure colors codes for heatmap?
platform: ejmvc
control: HeatMap
documentation: ug
---

# Color Mapping

Color mapping is used to indicate values as colors instead of numerical values. For example, if a HeatMap represents a data from 0 to 100. `ColorMapping` is used to specify a color for lower value and higher value. For any value between two values, a medium color will be automatically be chosen.

In color mapping, when white color is set to value 0 and red color is set for value 30, as shown below.

{% highlight c# %}

public ActionResult Default()
{
    HeatMapProperties Heatmap = new HeatMapProperties();
    List<HeatMapColorMapping> colorCollection = new List<HeatMapColorMapping>();
    colorCollection.Add(new HeatMapColorMapping() { Color = "#8ec8f8", Label = new HeatMapLabel() { Text = "0" }, Value = 0 });
    colorCollection.Add(new HeatMapColorMapping() { Color = "#0d47a1", Label = new HeatMapLabel() { Text = "100" }, Value = 100 });
    Heatmap.ColorMappingCollection = colorCollection;
    ViewData["HeatMapModel"] = Heatmap;
    return View();
}

{% endhighlight %}

Resultant HeatMap will be as shown below.

![](Color-Mapping_images/Color-Mapping_img1.png)
 