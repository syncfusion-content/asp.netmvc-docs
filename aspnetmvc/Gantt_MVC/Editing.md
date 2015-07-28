---
layout: post
title: Editing
description: editing
platform: ejmvc
control: Gantt
documentation: ug
---

# Editing

The Gantt control provides built-in support to add, insert and update the task inside Gantt. Gantt provides three types of editing, they are:

* Cell Editing
* Normal Editing
* Taskbar Editing
* Predecessor Editing



## Cell Editing

Update the task details through grid cell editing by setting EditMode as CellEditing.

The following code example shows you how to enable CellEditing in Gantt control.





{% highlight html %}



@(Html.EJ().Gantt("Gantt")

//...

.EditSettings(edit=>{

   edit.AllowEditing(true);

   edit.EditMode("cellEditing")

})

.Datasource(ViewBag.datasource)

)



{% endhighlight %}





The output of Gantt with CellEditing is as follows.



![](Editing_images/Editing_img1.png)



## Normal Editing

Update the task details through edit dialog by setting EditMode as Normal.

The following code example shows you how to enable normal editing in Gantt control.





{% highlight html %}



@(Html.EJ().Gantt("Gantt")

//...

.EditSettings(edit=>{

   edit.AllowEditing(true);

   edit.EditMode("normal")       

})

.Datasource(ViewBag.datasource)

)



{% endhighlight %}





The following screenshot shows the output of normal editing.



![C:/Users/pongeetha/Desktop/NormalEditing.png](Editing_images/Editing_img2.png)



## Taskbar Editing

Update the task details by interactions such as resizing and dragging the taskbar. The following code example shows you how to enable taskbar resizing in Gantt control.





{% highlight html %}



@(Html.EJ().Gantt("Gantt")

//...

.AllowGanttChartEditing(true)

.Datasource(ViewBag.datasource)

)



{% endhighlight %}



## Predecessor Editing

Update the predecessor details of a task using mouse interactions. The following code example shows how to enable predecessor editing.



{% highlight html %}



@(Html.EJ().Gantt("Gantt")

           //..

           .PredecessorMapping("predecessor")

           .AllowGanttChartEditing(true)                               

           .Datasource(ViewBag.datasource)

 )



{% endhighlight %}





The following screen shot shows the predecessor editing in Gantt control.

![C:/Users/labuser/Desktop/hello.png](Editing_images/Editing_img3.png)



_Figure 39 : Predecessor Editing_

