---
layout: post
title: Resource Histogram View | Gantt | ASP.NET MVC | Syncfusion
description: resource histogram view
platform: ejmvc
control: Gantt
documentation: ug
---

# Resource Histogram

A resource histogram displays the scheduled working time range of resources for its assigned tasks. Using this, you can easily identify the resource's availability and its working time. The resource histogram is used to allocate the resources properly throughout the project and find the details about allocated resources and the allocated time ranges of a specific resource.

## Databinding
You can render the histogram view for both project view Gantt and resource view Gantt by using the `ViewType` as `GanttViewType.HistogramView`. 
The following code example explains how to bind the resource histogram view for project view Gantt.
{% highlight CSHTML %}
@(Html.EJ().Gantt("GanttContainer")
    .TaskIdMapping("TaskID")
    .TaskNameMapping("TaskName")
    .StartDateMapping("StartDate")
    .DurationMapping("Duration")
    .ProgressMapping("Progress")
    .ResourceInfoMapping("ResourceID")
    .ResourceNameMapping("ResourceName")
    .ResourceIdMapping("ResourceID")
    .ChildMapping("SubTasks")
    .ViewType(GanttViewType.ProjectView)
    //..
    .Resources(ViewBag.resources)
    .Datasource(ViewBag.datasource)
)

@(Html.EJ().Gantt("HistogramContainer")
    .ViewType(GanttViewType.HistogramView)
    .TaskIdMapping("TaskID")
    .TaskNameMapping("TaskName")
    .StartDateMapping("StartDate")
    .DurationMapping("Duration")
    .ProgressMapping("Progress")
    .ChildMapping("SubTasks")
    .ResourceInfoMapping("ResourceID")
    .ResourceNameMapping("ResourceName")
    .ResourceIdMapping("ResourceID")
    //..
    .Resources(ViewBag.resources)
    .Datasource(ViewBag.histogramData)
)
@(Html.EJ().ScriptManager())
{% endhighlight %}
N> You should bind the data source and necessary mapping properties to render the histogram view. You can differentiate whether the bound data source is project view data or resource view data using the `ganttObject.isProjectViewData` boolean property and `Load` event. Set this property to `true` if the provided data is project view and set to `false` for resource view data.

## Synchronize resource histogram view Gantt with other views

You can synchronize the splitter position and horizontal scroller position in chart side and task values of the project view/resource view Gantt control with resource histogram view Gantt by using the `ActionComplete` and `SplitterResized` events.

### Synchronize with project view

The following code snippet shows how to synchronize the resource histogram view Gantt with project view Gantt.

{% highlight CSHTML %}
@(Html.EJ().Gantt("GanttContainer")
    .TaskIdMapping("TaskID")
    .TaskNameMapping("TaskName")
    .StartDateMapping("StartDate")
    .DurationMapping("Duration")
    .ProgressMapping("Progress")
    .ResourceInfoMapping("ResourceID")
    .ResourceNameMapping("ResourceName")
    .ResourceIdMapping("ResourceID")
    .ChildMapping("SubTasks")
    .ViewType(GanttViewType.ProjectView)
    .ClientSideEvents(cs => {
        cs.SplitterResized("splitterResized").ActionComplete("actionComplete");
    })
    //..
    .Resources(ViewBag.resources)
    .Datasource(ViewBag.datasource)
)

@(Html.EJ().Gantt("HistogramContainer")
    .ViewType(GanttViewType.HistogramView)
    .TaskIdMapping("TaskID")
    .TaskNameMapping("TaskName")
    .StartDateMapping("StartDate")
    .DurationMapping("Duration")
    .ProgressMapping("Progress")
    .ChildMapping("SubTasks")
    .ResourceInfoMapping("ResourceID")
    .ResourceNameMapping("ResourceName")
    .ResourceIdMapping("ResourceID")
    .ClientSideEvents(cs => {
        cs.Load("load").SplitterResized("splitterResized").ActionComplete("actionComplete");
    })
    //..
    .Resources(ViewBag.resources)
    .Datasource(ViewBag.histogramData)
)
@(Html.EJ().ScriptManager())
<script type="text/javascript">
    function load(args) {
        this.isProjectViewData = true;
    }
    function splitterResized(args) {
        if (args.isOnResize == false) return;
        if (this._id == "GanttContainer") {
            $("#HistogramContainer").ejGantt("setSplitterPosition", args.currentSplitterPosition);
        } else if (this._id == "HistogramContainer") {
            $("#GanttContainer").ejGantt("setSplitterPosition", args.currentSplitterPosition);
        }
    }
    function actionComplete(args) {
        if (args.requestType == "scroll" && args.scrollDirection == "horizontal") {
            var scrollLeft = args.scrollLeft;
            if (this._id == "GanttContainer" && !args.isScrollByMethod) {
                $("#HistogramContainer").ejGantt("setChartScrollLeft", scrollLeft);
            } else if (this._id == "HistogramContainer" && !args.isScrollByMethod) {
                $("#GanttContainer").ejGantt("setChartScrollLeft", scrollLeft);
            }
        } else if (args.requestType == "recordUpdate") {
            $("#HistogramContainer").ejGantt("updateHistogramTask", args.data, "update");
            if (args.updatedRecords && args.updatedRecords.length > 0) {
                for (var count = 0; count < args.updatedRecords.length; count++) {
                    $("#HistogramContainer").ejGantt("updateHistogramTask", args.updatedRecords[count], "update");
                }
            }
        } else if (args.requestType == "save" && args.modifiedRecord) {
            $("#HistogramContainer").ejGantt("updateHistogramTask", args.modifiedRecord, "update");
        } else if (args.requestType == "save" && args.addedRecord) {
            $("#HistogramContainer").ejGantt("updateHistogramTask", args.addedRecord, "add");
        } else if (args.requestType == "delete") {
            $("#HistogramContainer").ejGantt("updateHistogramTask", args.data, "delete");
        }
    }
</script>
{% endhighlight %}

The following screenshot shows the resource histogram with project view Gantt.
![](HistogramView_images/HistogramView_1.png)

Please find our online demo sample for further reference
[ResourceHistogram](https://mvc.syncfusion.com/demos/web/gantt/histogramview)

### Synchronize with resource view
The following code snippet shows how to synchronize the resource histogram view Gantt with resource view Gantt.

{% highlight CSHTML %}
@(Html.EJ().Gantt("GanttContainer")
    .TaskIdMapping("TaskID")
    .TaskNameMapping("TaskName")
    .StartDateMapping("StartDate")
    .EndDateMapping("EndDate")
    .DurationMapping("Duration")
    .ProgressMapping("Progress")
    .GroupNameMapping("TeamName")
    .GroupIdMapping("TeamId")
    .ViewType(GanttViewType.ResourceView)
    .ResourceIdMapping("ResourceId")
    .ResourceInfoMapping("ResourceID")
    .ResourceNameMapping("ResourceName")
    //..
    .ClientSideEvents(cs => {
        cs.ActionComplete("actionComplete");
        cs.SplitterResized("splitterResized");
    })
    .GroupCollection(ViewBag.groups)
    .Resources(ViewBag.resources)
    .Datasource(ViewBag.datasource)
)
@(Html.EJ().Gantt("HistogramContainer")
    .TaskIdMapping("TaskID")
    .TaskNameMapping("TaskName")
    .StartDateMapping("StartDate")
    .EndDateMapping("EndDate")
    .DurationMapping("Duration")
    .ProgressMapping("Progress")
    .GroupNameMapping("TeamName")
    .GroupIdMapping("TeamId")
    .ViewType(GanttViewType.HistogramView)
    .ResourceIdMapping("ResourceId")
    .ResourceInfoMapping("ResourceID")
    .ResourceNameMapping("ResourceName")
    //..
    .ClientSideEvents(cs => {
        cs.Load("load");
        cs.ActionComplete("actionComplete");
        cs.SplitterResized("splitterResized");
    })
    .GroupCollection(ViewBag.groups)
    .Resources(ViewBag.resources)
    .Datasource(ViewBag.datasource)
)
@(Html.EJ().ScriptManager())
<script type="text/javascript">
    function load(args) {
        this.isProjectViewData = false;
    }
    function splitterResized(args) {
        if (args.isOnResize == false) return;
        if (this._id == "GanttContainer") {
            $("#HistogramContainer").ejGantt("setSplitterPosition", args.currentSplitterPosition);
        } else if (this._id == "HistogramContainer") {
            $("#GanttContainer").ejGantt("setSplitterPosition", args.currentSplitterPosition);
        }
    }
    function actionComplete(args) {
        if (args.requestType == "scroll" && args.scrollDirection == "horizontal") {
            var scrollLeft = args.scrollLeft;
            if (this._id == "GanttContainer" && !args.isScrollByMethod) {
                $("#HistogramContainer").ejGantt("setChartScrollLeft", scrollLeft);
            } else if (this._id == "HistogramContainer" && !args.isScrollByMethod) {
                $("#GanttContainer").ejGantt("setChartScrollLeft", scrollLeft);
            }
        }
        //task drag and drop action and edit action
        else if (args.requestType == "save" && args.modifiedRecord || args.requestType == "recordUpdate") {
            var data = args.requestType == "save" ? args.modifiedRecord : args.item ? args.item : args.data;
            $("#HistogramContainer").ejGantt("updateHistogramTask", data, "update");
            //row delete & group delete
            if (args.updatedRecords) {
                for (var i = 0; i < args.updatedRecords.length; i++) {
                    var data = args.updatedRecords[i];
                    $("#HistogramContainer").ejGantt("updateHistogramTask", data, "update");
                }
            }
        }
        //add row
        else if (args.requestType == "save" && args.addedRecord) {
            $("#HistogramContainer").ejGantt("updateHistogramTask", args.addedRecord, "add");
        }
        //task delete
        else if (args.requestType == "delete") {
            $("#HistogramContainer").ejGantt("updateHistogramTask", args.data, "delete");
        }
    }
</script>
{% endhighlight %}

The following screenshot shows the resource histogram for resource view Gantt.
![](HistogramView_images/HistogramView_2.png)
