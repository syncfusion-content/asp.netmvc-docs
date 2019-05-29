---
layout: post
title:  Frozen Header | PivotGrid | ASP.NET MVC | Syncfusion
description:  This document illustrates that how to enable frozen header feature and its options in ASP.NET MVC PivotGrid control
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Frozen Header

Allows you to freeze the header of the Grid so that it will be always visible when scrolling the content with a large number of rows or columns providing a precise view.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(.....).FrozenHeaderSettings(frohead => frohead.EnableFrozenHeaders(true))

{% endhighlight %}

![Frozen header, aka Freeze headers support in ASP NET MVC pivot grid control](FrozenHeader_images/row_col_freeze.png)

We can also freeze the row/column headers individually by setting the below properties.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(.....).FrozenHeaderSettings(frohead => frohead.EnableFrozenRowHeaders(true))  //To Freeze the Row headers

{% endhighlight %}

![Frozen row headers in ASP NET MVC pivot grid control](FrozenHeader_images/row_freeze.png)

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(.....).FrozenHeaderSettings(frohead => frohead.EnableFrozenColumnHeaders(true))  //To Freeze the Column headers

{% endhighlight %}

![Frozen column headers in ASP NET MVC pivot grid control](FrozenHeader_images/col_freeze.png)

We can also set the size of the scroller (horizontal and vertical) in PivotGrid by using below property.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(.....).FrozenHeaderSettings(frohead => frohead.ScrollerSize(18))

{% endhighlight %}

![Scroller size in ASP NET MVC pivot grid control](FrozenHeader_images/scroll_size.png)