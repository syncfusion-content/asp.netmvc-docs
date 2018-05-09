---
layout: post
title: Searching | TreeGrid | ASP.NET MVC | Syncfusion
description: Searching
platform: ejmvc
control: TreeGrid
documentation: ug
---

## Searching

The TreeGrid control has an option to search its content using toolbar search box. The toolbar search box can be enabled by using the `ToolbarSettings.ToolbarItems` property. The following code example explains how to integrate search textbox in toolbar.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")             
    .ToolbarSettings(tool =>
    {
        tool.ShowToolbar(true);
        tool.ToolbarItems(new List<TreeGridToolBarItems>()
        {
            TreeGridToolBarItems.Search, 
        });
    })      
)

{% endhighlight %}

The below screenshot shows TreeGrid search with `plan` key word.
![](Searching_images/Searching_img1.png)