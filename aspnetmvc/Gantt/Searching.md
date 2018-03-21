---
layout: post
title: Searching | Gantt | ASP.NET MVC | Syncfusion
description: searching
platform: ejmvc
control: Gantt
documentation: ug
---
# Searching

The Gantt control for JavaScript has in-built support for searching any content in Gantt.

### Searching for content columns

In Gantt, we can search the content using the JavaScript method [`searchItem`](/api/js/ejgantt#methods:searchitem "searchItem(searchString)") with search key as parameter. Also, we can integrate the search text box in Gantt toolbar by adding search toolbar item in `ToolbarSettings.ToolbarItems` property.

The following code example shows you how to add search option in Gantt toolbar.

{% highlight CSHTML %}

@(Html.EJ().Gantt("GanttContainer")
          //...
		  .ToolbarSettings(toolbar=>
		 {
			 toolbar.ShowToolbar(true);
			 toolbar.ToolbarItems(new List<GanttToolBarItems>(){
				 GanttToolBarItems.Search   //To search the task
			 });
     })   	
)@(Html.EJ().ScriptManager())

{% endhighlight %}

The following screenshot shows the output of searching for string in Gantt control.

![](Searching_images/Searching_img1.png)