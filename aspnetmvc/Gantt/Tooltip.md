---
layout: post
title: Tooltip| Gantt | ASP.NET MVC | Syncfusion
description: Tooltip
platform: ejmvc
control: Gantt
documentation: ug
---

# Tooltip

The Gantt has support to display tooltip for both taskbars and for column cells.

## Taskbar and dependency line tooltip

In Gantt, you can enable or disable taskbar and dependency line mouse hover tooltip by using the `EnableTaskbarTooltip` property. The default value of this property was `true`. The following code example shows, how to enable the taskbar and dependency line tooltip in Gantt.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EnableTaskbarTooltip(true)
    .PredecessorMaping("Predecessors")
    .Datasource(ViewBag.datasource)
)

{% endhighlight %}

Taskbar tooltip can be customized by using the `TaskbarTooltipTemplate` property and  dependency line tooltip can be customized by using the `PredecessorTooltipTemplate` property, these properties are described briefly in the [customization](/aspnetmvc/gantt/customizations) section.

![](Tooltip_images/Tooltip_img3.png)
Taskbar Tooltip
{:.caption}

![](Tooltip_images/Tooltip_img4.png)
Dependency Tooltip
{:.caption}

## Taskbar drag tooltip

It is possible to enable or disable the tooltip while performing editing actions on taskbar (left resizing, right resizing, dragging and progress resizing) by using the `EnableTaskbarDragTooltip` property. By default, this property is set to `true`. The following code example explains this behavior.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EnableTaskbarDragTooltip(true)
    .Datasource(ViewBag.datasource)
)

{% endhighlight %}


## Cell tooltip

It is possible to enable or disable the TreeGrid cell tooltip in mouse hover by using the `ShowGridCellTooltip`  property. By default, this property is set to `true`. The following code example explains how to enable disable this property.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .ShowGridCellTooltip(true)
    .Datasource(ViewBag.datasource)
)

{% endhighlight %}


This tooltip can be customized using the `CellTooltipTemplate` property, which is described briefly in the [customization](/aspnetmvc/gantt/customizations) section.

![](Tooltip_images/Tooltip_img1.png)

## Tree column (Expander column) tooltip 

It is also possible to display tooltip only for expander column by setting the `ShowGridExpandCellTooltip` property. The following code example shows you to enable expander column tooltip in Gantt.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .ShowGridExpandCellTooltip(true)
    .Datasource(ViewBag.datasource)
)

{% endhighlight %}

![](Tooltip_images/Tooltip_img2.png)

