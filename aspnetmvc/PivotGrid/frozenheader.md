---
layout: post
title:  Frozen Header | PivotGrid | ASP.NET MVC | Syncfusion
description:  frozen header
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Frozen Header

Allows you to freeze the header of the Grid so that it will be always visible when scrolling the content with a large number of rows or columns providing a precise view.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(.....).FrozenHeaderSettings(frohead => frohead.EnableFrozenHeaders(true))

{% endhighlight %}

![](FrozenHeader_images/row_col_freeze.png)

We can also freeze the row/column headers individually by setting the below properties.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(.....).FrozenHeaderSettings(frohead => frohead.EnableFrozenRowHeaders(true))  //To Freeze the Row headers

{% endhighlight %}

![](FrozenHeader_images/row_freeze.png)

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(.....).FrozenHeaderSettings(frohead => frohead.EnableFrozenColumnHeaders(true))  //To Freeze the Column headers

{% endhighlight %}

![](FrozenHeader_images/col_freeze.png)