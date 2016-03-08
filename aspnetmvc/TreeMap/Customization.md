---
layout: post
title: Customization of Syncfusion treeMap control for ASP.NET MVC
description: Learn how to customize the treemap control
platform: ejmvc
control: TreeMap
documentation: ug
---

# Customization

TreeMap control supports color customization to determine the exact combination of colors for tree nodes displayed in TreeMap and tooltip support to display additional information of treemap data.

## Color Customization

You can customize the colors of the leaf nodes of TreeMap using the ColorMapping support of the TreeMap. 

`ColorMapping` is categorized into three different types such as,

* `UniColorMapping`
* `RangeBrushColorMapping`
* `DesaturationColorMapping`

## Uni Color Mapping

You can color, all the leaf nodes with the same color by setting the color value of the `UniColorMapping` property of the TreeMap.

{% highlight CSHTML %}

    
    @(Html.EJ().TreeMap("treemap")
  
    .TreeMapUniColorMapping(cm =>

    {

       cm.Color("crimson");

    })

    .Render())

{% endhighlight %}

![](Customization_images/Customization_img1.png)



## Range Color Mapping

You can group the leaf nodes based on the range of the data’s color values. You can set a unique color for every ranges. To achieve this, specify the `To` and `From` values as range bound and `Color` value to fill the leaf nodes of the particular range, through the `RangeColorMapping` property of the TreeMap.

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")

    .TreeMapRangeColorMappings(cm => 

    {

	   cm.To(1).From(0).Color("#77D8D8").Add();

	   cm.To(2).From(0).Color("#AED960").Add();

	   cm.To(3).From(0).Color("#FFAF51").Add();

	   cm.To(4).From(0).Color("#F3D240").Add();

    })

    .Render())

{% endhighlight %}

![](Customization_images/Customization_img2.png)


## Desaturation Color Mapping

You can differentiate all the leaf nodes using the `DesaturationColorMapping` property of the TreeMap. Differentiation is achieved, even though same color is applied for all the leaf nodes by varying the opacity of the leaf nodes based on the color value specified in the color value range using `RangeMinimum` and `RangeMaximum` value of the data collection. You can also bound the opacity range by setting from and to property of the `DesaturationColorMapping`.

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")

    .TreeMapDesaturationColorMapping(cm => 

    {

        cm.To(0.2).From(1).Color("DeepSkyBlue")

        .RangeMinimum(0).RangeMaximum(4); 
    })

    .Render())


{% endhighlight %}

![](Customization_images/Customization_img3.png)

## Tooltip

You can enable the tooltip support for the TreeMap by setting the `ShowTooltip` property to true. By default, it takes the property of the bound object that is referred to in the `GroupPath` and displays its content when the corresponding node is tapped. The `TooltipTemplate` is a HTML element that is used to expose the custom template for the tooltip.

## Leaf Item Setting

You can customize the Leaf level TreeMap items using `LeafItemsSetting`. The Label and tooltip values take the property of bound object that is referred in the LabelPath when defined.

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")

    .DataSource(datasource)
    .ColorValuePath("Growth")
    .WeightValuePath("Population")
    .Levels(lv =>
    {

	   lv.GroupPath("Continent")
	     .GroupGap(5)
	     .Add();                            
    })   
    .TreeMapRangeColorMappings(cm => 
    {
        cm.To(1).From(0).Color("#77D8D8").Add();
        cm.To(2).From(0).Color("#AED960").Add();
        cm.To(3).From(0).Color("#FFAF51").Add();
        cm.To(4).From(0).Color("#F3D240").Add();
    })
    .LeafItemsSetting(li =>
    {
	   li.LabelPath("Region")
	     .ShowLabels(true)
    })
    .ShowTooltip(true)
    .TooltipTemplate("tooltiptemplate")                
    .Render())   
    
    </div>   

    <script  id="tooltiptemplate" type="application/jsrender">

        <div  style="margin-left:17px;margin-top:-45px;">      

            <div style="height:auto;width:auto;background:black;border-radius:3px;opacity:0.6">

                <div style="margin-top:-20px;margin-left:9px;padding-top:3px;margin-right:9px;">

                    <label style="margin-top:-20px;font-weight:normal;font-size:12px;color:white;font-family:Segoe UI;">{{:Region}}</label>

                </div>

                <div style="height:10px;"></div>

                <div style="margin-top:-10px;margin-left:9px;margin-right:9px;padding-bottom:3px;">

                    <label style="margin-top:-10px;font-weight:normal;font-size:14px;color:white;font-family:segoe ui light;">{{:Population}}</label>

                </div>

            </div>

        </div>            

    </script>



{% endhighlight %}



![](Customization_images/Customization_img4.png)

