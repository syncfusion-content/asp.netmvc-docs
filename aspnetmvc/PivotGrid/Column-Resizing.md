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

## Column Width Based on Size

The property `EnableColumnResizing` adjusts the width of each column based on size of the widget.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableColumnResizing(true).DataSource(.....)

{% endhighlight %} 

## Column Width Based on Text

The property `ResizeColumnsToFit` automatically adjusts the width of each column based on the maximum content length available in the respective column.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").ResizeColumnsToFit(true).DataSource(.....)

![](Column-Resizing_images/columnresizing.png)

{% endhighlight %} 