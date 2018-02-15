---
layout: post
title: ToolTip | PivotGrid | ASP.NET MVC | Syncfusion
description: ToolTip
platform: ejmvc
control: PivotGrid
documentation: ug
---

# ToolTip

Allows you to display the details of the cell on hovering value cells. By default, tooltip is enabled.  You can disable tooltip in PivotGrid by setting the `EnableToolTip` property to false.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableToolTip(false)

{% endhighlight %}

## ToolTip Animation

The PivotGrid provides option to animate tooltip displayed in the grid.  The animation enhances the appearance of tooltip by displaying it slowly.  You can enable animation in tooltip by setting `EnableToolTipAnimation` property to true.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableToolTipAnimation(true)

{% endhighlight %}

![](ToolTip_images/tooltip.png)

