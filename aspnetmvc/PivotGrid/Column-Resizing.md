---
layout: post
title:  Column Resizing | PivotGrid | ASP.NET MVC | Syncfusion 
description: column resizing
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Column Resizing

Allows you to resize the column by changing its width while holding and dragging the column border using the mouse.

You can enable column resizing option in PivotGrid by setting the `EnableColumnResizing` property to true.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableColumnResizing(false).DataSource(.....)

{% endhighlight %} 

![](Column-Resizing_images/columnresizing.png)