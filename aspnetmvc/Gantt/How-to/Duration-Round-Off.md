---
layout: post
title: Duration Round-Off | Gantt | ASP.NET MVC | Syncfusion
description: Rounding off duration
platform: ejmvc
control: Gantt
documentation: ug
---
## Round-off start date, end date and duration value on taskbar editing
In Gantt start date, end date and duration values can be round-off as per current `ScheduleHeaderSettings.ScheduleHeaderType` value on taskbar resizing and dragging actions. This can be achieved by setting `roundOffDuration` argument value as `true` in `TaskbarEditing` event.

The below code example explains how to achieve this requirement. 

{% highlight CSHTML %}

@(Html.EJ().Gantt("gantt")
    
    .ClientSideEvents(eve =>
    {
      eve.TaskbarEditing("taskbarEditing");
    })
    
)
<script type="text/javascript">  
function taskbarEditing(args) {
    args.roundOffDuration = true;
}
<script>
{% endhighlight %}

![](Duration-Round-Off_images/OnResizing_img1.png)

![](Duration-Round-Off_images/AfterResizing_img2.png)