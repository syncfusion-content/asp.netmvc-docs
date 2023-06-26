---
layout: post
title: Work Breakdown Structure | Gantt | ASP.NET MVC | Syncfusion
description: Learn here about Work Breakdown Structure in Syncfusion Essential ASP.NET MVC Gantt Control, its elements, and more.
platform: ejmvc
control: Gantt
documentation: ug
---

# Work Breakdown Structure

Work Breakdown Structure(WBS) in Gantt represents the entire project activities in various sub modules. It is used to split the large tasks into manageable small tasks. WBS value and WBS predecessor value of Gantt tasks are displayed in WBS column and WBS predecessor column. This can be enabled in Gantt by using `EnableWBS` and `EnableWBSPredecessor` properties. The following code example shows how to enable WBS columns in Gantt.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
	// ...
	.EnableWBS(true)
	.EnableWBSPredecessor(true)
	)
@(Html.EJ().ScriptManager())

{% endhighlight %}

The below screenshot depicts the output of above code example.

![Work Breakdown Structure in ASP.NET MVC Gantt](WorkBreakdownStructure_images/wbs_img1.png)

[Click](https://ej2.syncfusion.com/home/aspnetmvc.html#platform) here to view the online demo sample for WBS in Gantt.
