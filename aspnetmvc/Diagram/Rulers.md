---
layout: post
title:  Ruler is used to measure the distance of nodes and connectors from origin of the page.
description: how to measure the distance of Nodes and Connectors?
platform: ejmvc
control: Diagram
documentation: ug
---


# Rulers

The Ruler provides a Horizontal and Vertical guide for measuring in the Diagram control. The Ruler can be used to measure the Diagram objects, indicate positions, and align Diagram elements. This is especially useful in creating scale models. 

## Adding Rulers to the Diagram
Use the following code example to add the ruler to the Diagram.


{% highlight c# %}

    DiagramBuilderModel diagramModel = new DiagramBuilderModel();

    diagramModel.Model.RulerSettings = new RulerSettings();
    diagramModel.Model.RulerSettings.ShowRulers = true;

{% endhighlight %}


![](/aspnetmvc/Diagram/Rulers_images/Rulers_images1.png)

## Customizing the Ruler

By default, ruler segments are arranged based on measurement units.

Segment width, the textual description of the ruler segment, and the appearance of the ruler ticks can be customized. Use the following code example to customize the ruler.

{% tabs %} 
{% highlight c# %}

    DiagramBuilderModel diagramModel = new DiagramBuilderModel();

    diagramModel.Model.RulerSettings = new RulerSettings();
    diagramModel.Model.RulerSettings.ShowRulers = true;
    //Customizing the horizontal ruler.
    DiagramRuler HorizontalRuler = new DiagramRuler();
    //Creating a custom segment with 6 intervals.
    HorizontalRuler.Interval = 6;
    // Customizing the ruler segment width.
    HorizontalRuler.SegmentWidth = 100;
    // Customizing the Ruler ticks.
    HorizontalRuler.ArrangeTick = "arrangeTick";
    // Customizing the Ruler ticks alignment.
    HorizontalRuler.TickAlignment = TickAlignment.LeftOrTop;
    // Customizing the Ruler marker color
    HorizontalRuler.MarkerColor = "blue";
    // Customizing the thickness of the ruler bar.
    HorizontalRuler.Thickness = 25;

    DiagramRuler VerticalRuler = new DiagramRuler();
    VerticalRuler.Interval = 6;
    VerticalRuler.SegmentWidth = 100;
    VerticalRuler.ArrangeTick = "arrangeTick";
    VerticalRuler.TickAlignment = TickAlignment.LeftOrTop;
    VerticalRuler.MarkerColor = "blue";
    VerticalRuler.Thickness = 25;

    diagramModel.Model.RulerSettings.HorizontalRuler = HorizontalRuler;
    diagramModel.Model.RulerSettings.VerticalRuler = VerticalRuler;

{% endhighlight %}


{% highlight js %} 

    function arrangeTick(args) {
        // Customizing the Ruler ticks.
        if (args.tickInterval % 100 == 0) {
        }
        else if (args.tickInterval % 50 == 0) {
            args.tickLength = 12.5
        }
    }

{% endhighlight %}
{% endtabs %}

![](/aspnetmvc/Diagram/Rulers_images/Rulers_images2.png)

