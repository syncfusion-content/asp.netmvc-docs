---
layout: post
title: Tooltip | RangeNavigator | ASP.NET MVC | Syncfusion
description: tooltip
platform: ejmvc
control: RangeNavigator
documentation: ug
---

# Tooltip

RangeNavigator provides Tooltip support for sliders. Sliders are used to select data at particular range in the RangeNavigator control. Tooltips for sliders display the selected start and end DateTime values.

## Customization

RangeNavigator provides support for you to customize the text display in the tooltip and background using TooltipSettings property. You can change font family, font color, font style, font weight. By default “Segoe UI” font family is set to tooltip text.

{% highlight CSHTML %}

@(Html.EJ().RangeNavigator("container")

.TooltipSettings(tooltip=>tooltip

.Visible(true)

.BackgroundColor("Black")

//  To customize the tooltip text

.Font(font=>font

.Color("red")                                                        

. Family("Segoe UI")                                                         

.Style(RangeNavigatorFontStyle.Normal)

.Size("12px")

.Opacity(1)                                                           

.Weight(RangeNavigatorFontWeight.Regular)

)

))

{% endhighlight %}

![](Tooltip_images/Tooltip_img1.png)



## Label Format

By default, the tooltip texts are automatically determined based on the data points.  To make it readable and understandable you can format the tooltip text. For DateTime data, all globalized format are supported. By default the LabelFormat is "MM/dd/yyyy".

Some of the LabelFormat for DateTime data are as follows:

* 'MMM, yyyy'
* 'dd, MMM'
* 'dd/MM/yyyy'
* 'dd, hh:mm'
* 'hh:mm:ss'

'hh:mm:ss:tt'

{% highlight CSHTML %}
 
@(Html.EJ().RangeNavigator("container")

.TooltipSettings(tooltip=>tooltip.LabelFormat("MMM, yyyy"))

)

{% endhighlight  %}

![](Tooltip_images/Tooltip_img2.png)



Tooltip display mode

By default the tooltip for RangeNavigator gets displayed. You can change this behavior using the TooltipDisplayMode property in the TooltipSettings and it takes the following values.

_Tooltip values_

<table>
<tr>
<th>
Value</th><th>
Description</th></tr>
<tr>
<td>
always</td><td>
Tooltip get displayed for RangeNavigator always.</td></tr>
<tr>
<td>
onDemand</td><td>
Tooltip get displayed only when we move the slider.</td></tr>
</table>

{% highlight CSHTML %}

@(Html.EJ().RangeNavigator("container")

.TooltipSettings(tooltip=>tooltip.TooltipDisplayMode("onDemand"))

)

{% endhighlight %}

![](Tooltip_images/Tooltip_img3.png)



