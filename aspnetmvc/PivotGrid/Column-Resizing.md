---
layout: post
title:  Column Resizing | PivotGrid | ASP.NET MVC | Syncfusion
description: This document illustrates that how to enable column resizing feature and its customization through API in ASP.NET MVC PivotGrid control
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

The `ResizeColumnsToFit` property automatically adjusts the width of each column based on the maximum content length available in the respective column.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").ResizeColumnsToFit(true).DataSource(.....)

![Column resizing in ASP NET MVC pivot grid control](Column-Resizing_images/columnresizing.png)

{% endhighlight %}