---
layout: post
title: Cell Editing | PivotGrid | ASP.NET MVC | Syncfusion
description: cell editing
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Cell Editing

I> This feature is applicable only for Relational data source.

Cell editing allows you to edit and alter the values in PivotGrid. The summary values will be recreated based on the edited values. By selecting multiple cells (like in cell selection feature), you can edit multiple cells at the same time.

You can enable cell editing option in PivotGrid by setting the `EnableCellEditing` property to true.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableCellEditing(false).DataSource(.....)

{% endhighlight %}

![Cell editing in ASP NET MVC pivot grid control](Cell-Editing_images/celleditingclient.png)


