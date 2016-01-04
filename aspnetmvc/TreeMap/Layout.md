---
layout: post
title: Layout in treeMap control
description: Learn how to apply the layout in treeMap control
platform: ejmvc
control: TreeMap
documentation: ug
---

# Layout

You can decide on the visual representation of nodes belonging to all the treemap levels using the `ItemsLayoutMode` property of the TreeMap.

There are four different TreeMap layouts such as

* Squarified Layout
* SliceAndDiceAuto Layout
* SliceAndDiceHorizontal Layout
* SliceAndDiceVertical Layout

## Squarified Layout

`Squarifiedlayout` creates rectangles with best aspect ratio.

{% highlight CSHTML %}

	@(Html.EJ().TreeMap("treemap")

		.DataSource(datasource)

		.ColorValuePath("Growth")

		.WeightValuePath("Population")               

		.Levels(lv =>

		{

			lv.GroupPath("Continent")

			  .GroupGap(5).Add();

		})     

		.ItemsLayoutMode("Squarified")           

		.Render())

{% endhighlight %}



![](Layout_images/Layout_img1.png)

## SliceAndDiceAuto Layout

`SliceAndDiceAuto` layout creates rectangles with high aspect ratio and displays them sorted both horizontally and vertically.

{% highlight CSHTML %}

	@(Html.EJ().TreeMap("treemap")

		.ItemsLayoutMode("SliceAndDiceAuto ")

		.Render())

{% endhighlight %}



![](Layout_images/Layout_img2.png)

## SliceAndDiceHorizontal Layout

`SliceAndDiceHorizontal` layout creates rectangles with high aspect ratio and displays them sorted horizontally.

{% highlight CSHTML %}

	@(Html.EJ().TreeMap("treemap")

		.ItemsLayoutMode("SliceAndDiceHorizontal ")

		.Render())

{% endhighlight %}



![](Layout_images/Layout_img3.png)

## SliceAndDiceVertical Layout

`SliceAndDiceVertical` layout creates rectangles with high aspect ratio and displays them sorted vertical.

{% highlight CSHTML %}

	@(Html.EJ().TreeMap("treemap")

		.ItemsLayoutMode("SliceAndDiceVertical ")

		.Render())

{% endhighlight %}



![](Layout_images/Layout_img4.png)

