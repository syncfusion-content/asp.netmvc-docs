---
layout: post
title: Interactive features of treeMap control for Asp.Net MVC
description: Learn how to enables the effective interaction on treeMap elements
platform: ejmvc
control: TreeMap
documentation: ug
---

# User Interaction

You can interact with the TreeMap control by selecting either the leaf nodes or the groups.

## Selection

Selection support enables you to highlight the items where the mouse tapping has occurred. You can select the following contents of the TreeMap control:

* Leaf Nodes
* Group

### Single Selection

To enable the selection of leaf nodes, the `HighlightOnSelection` property in treemap is set as true. When selection occurs, the item is highlighted with a bounding rectangle around the selected leaf node.
The border can be customized with `HighlightBorderBrush` and `HighlightBorderThickness` properties.


{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")
        
        // ...
        .HighlightOnSelection("true")
        
        .HighlightBorderBrush("#3e3e3e")
        
        .HighlightBorderThickness("1")
        
        // ...
    )

{% endhighlight %}

![](User-Interaction_images/User-Interaction_img1.png)

### Group Selection

To enable the selection of leaf nodes, the `HighlightGroupOnSelection` property in treemap is set as true. When selection occurs, bounding rectangle highlights the selected group.

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")
    
        // ...
    
        .HighlightGroupOnSelection("true")
    
        .HighlightBorderBrush("#3e3e3e")
    
        .HighlightBorderThickness("1")
    
        // ...
                
     )

        
{% endhighlight %}
        
![](User-Interaction_images/User-Interaction_img3.png)

### MultiSelection

This feature enables you to select multiple leaf nodes or groups simultaneously. To enable this feature for leaf nodes, use `ItemSelectionMode` as "multiple" and for groups, use `GroupSelectionMode` as "multiple"
To select multiple items simultaneously, the mouse tap should be done along with a continuous press of "`Ctrl`" key.  

#### Selection (Multiple)

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")

        // ...
                
        .HighlightOnSelection("true")
                
        .ItemSelectionMode("Multiple")
                
        // ...
                
    )
        
{% endhighlight %}

![](User-Interaction_images/User-Interaction_img2.png)

#### Group Selection (Multiple)

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")

        // ...
                
        .HighlightGroupOnSelection("true")
                
        .GroupSelectionMode("Multiple")
                
        // ...
                
    )
        
{% endhighlight %}

![](User-Interaction_images/User-Interaction_img4.png)

## Drag On Selection

This feature enables you to highlight/select the leaf nodes or groups by the dragging the mouse pointer over the TreeMap items.

### Dragging On Selection

To enable this feature, you have to set `DraggingOnSelection` as "true".

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")
    
        // ...
                
        .DraggingOnSelection("true")
                
        // ...
                
    )
        
{% endhighlight %}

![](User-Interaction_images/User-Interaction_img5.png)

### Dragging Group On Selection

To enable this feature, you have to set `DraggingGroupOnSelection` as "true".

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")
    
        // ...
                
        .DraggingGroupOnSelection("true")
                
        // ...
                
    )
        
{% endhighlight %}

![](User-Interaction_images/User-Interaction_img6.png)