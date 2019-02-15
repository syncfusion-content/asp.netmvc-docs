---
layout: post
title: Collapse by default | PivotGrid | ASP.NET MVC | Syncfusion
description: Collapse by default
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Collapse by default

I> This feature is applicable only for Relational datasource.

Allows you to collapse all members displayed in the grid. You can enable collapsing all members by default in the PivotGrid by setting the `EnableCollapseByDefault`(/api/js/ejpivotgrid#members: enablecollapsebydefault) property to true.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableCollapseByDefault(true)

{% endhighlight %}

![Collapse by default layout in ASP NET MVC pivot grid control](Collapse-By-Default_images/Collapse-Members.png)
