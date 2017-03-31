---
layout: post
title: Levels
description: Learn how to customize various levels in SunburstChart
platform: ejmvc
control: SunburstChart
documentation: ug
---

## Levels

Sunburst chart is used to display hierarchical data. You can add more than one hierarchical data by using the **Levels** property of Sunburst chart. Each level of the hierarchy is represented by circle.
The following code snippet illustrates 

{% highlight js %}
@(Html.EJ().SunburstChart("chartContainer")

       .Levels(
         //.. to add the hierarchical levels 
                      })
 )

{% endhighlight %}

## GroupMemberPath

It is the string property that is used to map the group category value in the dataSource .
You can define the levels as shown in the below code example

{% highlight js %}

@(Html.EJ().SunburstChart("chartContainer")

       .Levels(
         //.. to add the hierarchical levels 
         lv.GroupMemberPath("Level1").Add();
                        lv.GroupMemberPath("Level2").Add();
                        lv.GroupMemberPath("Level3").Add();
                      })
 )

 {% endhighlight %}

The following screenshot illustrates the Sunburst Chart with different levels

![](Levels_images/Levels_img1.png)
