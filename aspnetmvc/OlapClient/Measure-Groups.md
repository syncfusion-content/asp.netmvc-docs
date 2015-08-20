---
layout: post
title: Measure-Groups
description: measure groups 
platform: ejmvc
control: OLAPClient
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

![](Measure-Groups_images/Measure-Groups_img1.png)

![](Measure-Groups_images/Measure-Groups_img2.png)