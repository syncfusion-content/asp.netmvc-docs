---
layout: post
title: Grid Layout | PivotGrid | ASP.NET MVC | Syncfusion
description: grid layout
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Grid Layout

## Normal Layout

A layout in which summary cells are positioned at the bottom of each parent member and their child members appear next to them. Normal layout is the default layout in PivotGrid control. The enumeration property `Layout` needs to be set to **"PivotGridLayout.Normal"** in-order to view PivotGrid in normal layout. 

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Layout(PivotGridLayout.Normal).Url(Url.Content("/OLAPService")) 

{% endhighlight %}

![](Grid-Layout_images/layout-normal.png)

## No Summaries Layout

I> This feature is applicable only for OLAP datasource.

A layout in which summary cells are completely hidden and the child members appear next to their parent member.  The enumeration property `Layout` needs to be set to **"PivotGridLayout.NoSummaries"** in-order to view PivotGrid without summaries. 

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Layout(PivotGridLayout.NoSummaries).Url(Url.Content("/OLAPService"))

{% endhighlight %}

![](Grid-Layout_images/layout-nosummary.png)


## Excel-like Layout

A layout in which summary cells are positioned besides each parent member and their child members appear next to them. The enumeration property `Layout` needs to be set to **"PivotGridLayout.ExcelLikeLayout"** in-order to view PivotGrid in excel-like layout.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Layout(PivotGridLayout.ExcelLikeLayout).Url(Url.Content("/OLAPService"))

{% endhighlight %} 

![](Grid-Layout_images/layout-excel.png)


## Top Summary Layout 

I> This feature is applicable only for OLAP datasource only at Server Mode.

A layout in which summary cells are positioned at the top of each parent member and their child members appear next to them. The enumeration property `Layout` needs to be set to **"PivotGridLayout.NormalTopSummary"** in-order to view PivotGrid in top summaries layout. 

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Layout(PivotGridLayout.NormalTopSummary).Url(Url.Content("~/OLAPService"))

{% endhighlight %}

![](Grid-Layout_images/layout-top.png)

