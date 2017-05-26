---
layout: post
title: Multi-level Labels | PivotChart | ASP.NET MVC | Syncfusion
description: multilevellabels
platform: ejmvc
control: PivotChart
documentation: ug
---

# Multi-level Labels

Multi-level labels allows you to drill down to access the detailed level of data or drill up to see the summarized data by using the expander present in the OlapChart.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").EnableMultiLevelLabels(true)

{% endhighlight %}


## Relational

![](MultiLevelLabels_images/relational.png)

## OLAP

![](MultiLevelLabels_images/olap.png)

