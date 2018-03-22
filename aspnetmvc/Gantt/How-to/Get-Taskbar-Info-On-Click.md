---
layout: post
title: Get taskbar information on click action | Gantt | ASP.NET MVC | Syncfusion
description: Get taskbar information on click action
platform: ejmvc
control: Gantt
documentation: ug
---

# Get taskbar information on click action

When we click on the taskbar, `TaskbarClick` event will be triggered, using this event and it's arguments, we can do any action related to taskbar. The following code example shows how to use this event.

{% highlight CSHTML %}

@(Html.EJ().Gantt("gantt")    
    .ClientSideEvents(eve =>
    {
      eve.TaskbarClick("taskbarClick");
    })    
    )
<script type="text/javascript">  
function taskbarClick(args) {
     var taskbarElement = args.taskbarElement,
                taskData = args.data,
                target = args.target;
            //...            
}
<script>
{% endhighlight %}