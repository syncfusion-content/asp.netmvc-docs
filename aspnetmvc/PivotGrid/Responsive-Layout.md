---
layout: post
title: Responsive | PivotGrid | ASP.NET MVC | Syncfusion
description: responsive
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Responsive

PivotGrid and PivotTable Field list control supports responsive rendering based on the target device (desktop & tablet) resolution. It supports resolution upto 1024x600. You can enable responsiveness in PivotGrid by setting `IsResponsive` property to true.
 
On resizing the browser, the PivotTable Field list will get collapse and an icon will appear on the left-hand side of the browser. User can toggle its view and perform UI interaction.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("/OLAPService")).IsResponsive(true)

{% endhighlight %}

![](Responsive-Layout_images/normal.png)

_Normal PivotGrid_

![](Responsive-Layout_images/responsive.png)

_Responsive PivotGrid_

![](Responsive-Layout_images/res-schema.png)

_Responsive PivotTable Field List - Collapsed_

![](Responsive-Layout_images/res-schema1.png)

_Responsive PivotTable Field List - Expanded_

