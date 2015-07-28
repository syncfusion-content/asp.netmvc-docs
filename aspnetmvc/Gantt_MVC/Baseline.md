---
layout: post
title: Baseline
description: baseline
platform: ejmvc
control: Gantt
documentation: ug
---

# Baseline

Baseline is used to describe the original plan of the task and it can be the same as current duration of the task or different. The following code example shows you how to enable baseline in Gantt control.





{% highlight html %}



@(Html.EJ().Gantt("Gantt")

//...

.BaselineStartDateMapping("BaselineStartDate")

.BaselineEndDateMapping("BaselineEndDate")

.RenderBaseline(true)

.Datasource(ViewBag.datasource)

)



{% endhighlight %}





The following screenshot shows the baseline in Gantt control.



![](Baseline_images/Baseline_img1.png)



