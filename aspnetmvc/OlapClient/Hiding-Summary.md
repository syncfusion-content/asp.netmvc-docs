---
layout: post
title: Hiding Summary | OLAPClient | ASP.NET MVC | Syncfusion
description: hiding summary
platform: ejmvc
control: OlapClient
documentation: ug
---

# Hiding Summary

By setting the “GridLayout” property as “NoSummaries”, the summary cells in PivotGrid control is hidden. By default, “Normal” layout is set.

{% highlight html %}
@Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title("OLAP Browser").GridLayout(PivotGridLayout.NoSummaries) 
{% endhighlight %}

