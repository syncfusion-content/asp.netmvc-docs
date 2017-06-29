---
layout: post
title: Advanced Filtering and Soritng | PivotClient | ASP.NET MVC | Syncfusion 
description: advanced filtering and sorting
platform: ejmvc
control: PivotClient
documentation: ug
---


# Advanced Filtering & Sorting

It allows to filter and sort the field members in PivotClient.

### Client Mode

In client mode, you can enable Advanced Filtering and Sorting option in PivotClient by setting the [`EnableAdvancedFilter`] property under [`DataSource`] to true.

{% highlight html %}

@Html.EJ().Pivot().PivotClient("PivotClient1").DataSource(dataSource => dataSource.EnableAdvancedFilter(true))

{% endhighlight %}

### Server Mode

In server mode, you can enable the Advanced Filtering and Sorting option in PivotClient by setting the [`EnableAdvancedFilter`] property to true.

{% highlight html %}

@Html.EJ().Pivot().PivotClient("PivotClient1").EnableAdvancedFilter(true)

{% endhighlight %}

## Sorting

Sorting provides an option to sort the members of a field either in ascending or descending order. 

![](AdvanceFiltering_images/sorting.png)

## Label Filtering

Label filtering provides an option to filter the members of a field purely based on their caption. 

![](AdvanceFiltering_images/filtering.png)

![](AdvanceFiltering_images/filtering_dialog.png)

## Value Filtering

Value filtering provides an option to filter members based on the total values of the appropriate measure between the members of the level. 

![](AdvanceFiltering_images/valuefilter.png)

![](AdvanceFiltering_images/valuefilter_dialog.png)
