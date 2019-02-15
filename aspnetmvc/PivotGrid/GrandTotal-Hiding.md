---
layout: post
title:  GrandTotal Hiding | PivotGrid | ASP.NET MVC | Syncfusion
description: GrandTotal Hiding
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Grand Total Hiding

Grand Total Hiding can be classified into three categories.

* Row Grand Total Hiding
* Column Grand Total Hiding
* Both

## Row Grand Total Hiding

You can hide the **Grand Total** in row alone by setting the property `EnableRowGrandTotal` to `false`.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableRowGrandTotal(false).DataSource(.....)

{% endhighlight %}

![Hiding row totals in ASP NET MVC pivot grid control](GrandTotal-Hiding_images/enableRowGrandTotal.png)

## Column Grand Total Hiding

You can hide the **Grand Total** in column alone by setting the property `EnableColumnGrandTotal` to `false`.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableColumnGrandTotal(false).DataSource(.....)

{% endhighlight %}

![Hiding column totals in ASP NET MVC pivot grid control](GrandTotal-Hiding_images/enableColumnGrandTotal.png)

## Both

You can hide the **Grand Total** in both row and column by setting the property `EnableGrandTotal` to `false`.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableGrandTotal(false).DataSource(.....)

{% endhighlight %}

![Hiding totals in ASP NET MVC pivot grid control](GrandTotal-Hiding_images/enableGrandTotal.png)