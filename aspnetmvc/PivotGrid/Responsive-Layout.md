---
layout: post
title: Responsive-Layout
description: responsive layout
platform: ejmvc
control: PivotGrid
documentation: ug
---

## Responsive Layout

Responsive layout is aimed at crafting sites to provide an optimal viewing experience - easy reading. It also provides navigation with a minimum of resizing, panning, and scrolling across a wide range of devices from tablet to desktop. To get responsive layout for PivotGrid, enable IsResponsive API to true. By using this feature, you can achieve an effective view of the PivotGrid control in all devices including desktops, tablets, mobiles, etc. 

[MVC]

@using Syncfusion.JavaScript;

@using Syncfusion.JavaScript.Olap;

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("~/wcf/OLAPService.svc")).IsResponsive(true)



{{ '![](Responsive-Layout_images/Responsive-Layout_img1.png)' | markdownify }}
{:.image }


{{ '![](Responsive-Layout_images/Responsive-Layout_img2.png)' | markdownify }}
{:.image }


