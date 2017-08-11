---
layout: post
title:  Column Resizing | PivotGrid | ASP.NET MVC | Syncfusion 
description: column resizing
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Resizing Column

Allows the user to change the column width by holding and dragging the column border using the mouse pointer.

You can enable the resizing option in PivotGrid by setting the `EnableColumnResizing` property to true.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableColumnResizing(true).DataSource(.....)

{% endhighlight %} 

![](Column-Resizing_images/columnresizing.png)


Additionally, the property `ResizeColumnsToFit` automatically adjusts the width of each column based on the maximum content length available in the respective column.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableColumnResizing(true).ResizeColumnsToFit(true).DataSource(.....)

{% endhighlight %} 