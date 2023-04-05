---
layout: post
title: Change Splitter position | Gantt | ASP.NET MVC | Syncfusion
description: Learn here more about change splitter position support in Syncfusion Essential ASP.NET MVC Gantt Control, its elements, and more.
platform: ejmvc
control: Gantt
documentation: ug
---

# Change Splitter position in ASP.NET MVC Gantt

In Gantt control, Splitter separates the TreeGrid section from the Chart section. 

![Change Splitter position in ASP.NET MVC Gantt](Change-Splitter-position_images/Change-Splitter-position_img1.png)


It is possible to change the position of the Splitter while loading the Gantt by using the `SplitterPosition` property, thereby varying the width of the TreeGrid and Chart sections in the control.  SplitterPosition property denotes the percentage of the TreeGrid section’s width to be rendered and this property supports both pixels and percentage values.

The following code example explains how to define the SplitterPosition property in the Gantt.


{% highlight CSHTML %}

@(Html.EJ().Gantt("gantt")    
    .SplitterPosition("50%")
    //also you can define with pixel value as 
    //.SplitterPosition(”650”) (or) .SplitterPosition(”650px”)
    )
@(Html.EJ().ScriptManager())

{% endhighlight %}

![Gantt with 30 % splitter position in ASP.NET MVC Gantt](Change-Splitter-position_images/Change-Splitter-position_img2.png)

Gantt with 30 % splitter position
{:.caption}

![Gantt with 50% splitter position in ASP.NET MVC Gantt](Change-Splitter-position_images/Change-Splitter-position_img3.png)

Gantt with 50% splitter position
{:.caption}

![Gantt with 600px splitter position in ASP.NET MVC Gantt](Change-Splitter-position_images/Change-Splitter-position_img4.png)

Gantt with 600px splitter position
{:.caption}


