---
layout: post
title: Measure-Groups
description: measure groups 
platform: ejmvc
control: OLAP Client
documentation: ug
---

# Measure Groups 

In Cube Dimension Browser tree-view can be viewed in a filtered manner through the Measure Groups option. This feature allows you to view the list of measure groups and dimensions associated with the selected measure group from the cube.

{% highlight c# %}

	@Html.EJ().Olap().OlapClient("OlapClient1")
	.EnableMeasureGroups(true)
	.Url(Url.Content("~/wcf/OlapClientService.svc"))

{% endhighlight %}

On selecting a measure group from the drop-down list, the Cube Dimension Browser tree-view displays the related dimensions as follows.

![C:/Users/Narendhran Muthuvel/Desktop/Capture7.PNG](Measure-Groups_images/Measure-Groups_img1.png)

![C:/Users/Narendhran Muthuvel/Desktop/Capture44.PNG](Measure-Groups_images/Measure-Groups_img2.png)