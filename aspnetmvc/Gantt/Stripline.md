---
layout: post
title: Stripline | Gantt | ASP.NET MVC | Syncfusion
description: stripline
platform: ejmvc
control: Gantt
documentation: ug
---

# Stripline

Stripline in Gantt control is used to highlight the important event in Gantt chart part. By using this feature, you can add the Striplines to highlight important days in your project. The following code example shows you how to add the Stripline in Gantt control.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
     //...
 .StripLines(new   List<Syncfusion.JavaScript.Models.StripLine> 
   {
        new Syncfusion.JavaScript.Models.StripLine()
         { 
                    Day="03/02/2014", 
                    Label="Project Release", 
                    LineStyle="dotted",
                    LineColor="blue",
                    LineWidth=2 }, 
        })
)
@(Html.EJ().ScriptManager())

{% endhighlight %}

The following screenshot shows stripline in Gantt control.

![](Stripline_images/Stripline_img1.png)

