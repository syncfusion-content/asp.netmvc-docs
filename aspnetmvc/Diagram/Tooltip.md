---
layout: post
title: Show tooltips when mouse hovers over objects
description: How to show/hide tooltips when mouse hovers over objects or during interaction?
platform: ejmvc
control: Diagram
documentation: ug
---

# Tooltip
In Graphical User Interface (GUI), tooltip is a message that is displayed when mouse hovers over an element. Diagram provides tooltip support while dragging, resizing, rotating a node, and when mouse hovers any Diagram element.

## Default tooltip

By default, Diagram displays a tooltip to provide the size, position, and angle related information while dragging, resizing, and rotation. The following images illustrate how the Diagram displays the node information during interaction.

| Drag | Resize | Rotate |
|---|---|---|
| ![](/Tooltip_images/Tooltip_img1.png) | ![](/Tooltip_images/Tooltip_img2.png) | ![](/Tooltip_images/Tooltip_img3.png) |

### Disable default tooltip

To disable the default tooltip, You need to set `SelectedItems.Tooltip` as `null`. The following code example illustrates how to disable default tooltip.

{% highlight c# %}

            // To Enables multiple tools
            DiagramProperties Model = new DiagramProperties();
           
            //Disable tooltip during interaction
            Model.SelectedItems.Tooltip = null;
{% endhighlight %} 


## Common tooltip for all nodes and connectors

Diagram provides support to show tooltip when mouse hovers over any node/connector. 
To show tooltip on mouse over, the `Tooltip` property of Diagram model needs to be set with the tooltip `TemplateId` and `Alignment` as shown in the following example.

{% highlight html %}

    <!--Define tooltip template-->
    <script type="text/x-jsrender" id="mouseovertooltip">
        <div style="background-color: #F08080; color: white; white-space: nowrap; height: 20px">
           <span style="padding: 5px;"> {{:addInfo.Designation}} </span>
        </div>
    </script>

{% endhighlight %}

{% highlight c# %}

   public partial class DiagramController : Controller
    {
        public ActionResult DiagramFeatures()
        {
           //Initialize the Diagram Model
            DiagramProperties Model = new DiagramProperties();

            Model.Width = "100%";
            Model.Height = "700px";
            //Defines mouse over tooltip
            Model.Tooltip = new Tooltip();
            Model.Tooltip.TemplateId = "mouseovertooltip";
            Model.Tooltip.Alignment.Horizontal = HorizontalAlignment.Center;
            Model.Tooltip.Alignment.Vertical = VerticalAlignment.Center;

            Label Label = new Label() { Text = "Elizabeth", FontColor = "white", Bold = true };
            Collection Labels = new Collection();
            Labels.Add(Label);
            //Defines nodes
            Node Node = new Node()
            {
                Name = "elizabeth",
                Width = 70,
                Height = 40,
                OffsetX = 100,
                OffsetY = 100,
                FillColor = "darkCyan",

                Labels = Labels
            };
            Node.AddInfo = new Dictionary<string, object>();
            Dictionary<string, object> AddInfo = new Dictionary<string, object>();
            AddInfo.Add("Designation", "Managing Director");
            Node.AddInfo = AddInfo;
            Model.Nodes.Add(Node);
            ViewData["diagramModel"] = Model;
            return View();
        }
        
{% endhighlight %} 

![](/Tooltip_images/Tooltip_img4.png)

### Disable tooltip at runtime

Tooltips on mouse over can be disabled by assigning `tooltip` property as `null`. The following code example illustrates how to disable the mouse over tooltip at runtime.

{% highlight js %}

    $("#diagram").ejDiagram({
        //Disables mouse over tooltip at runtime
        tooltip: null
    });

{% endhighlight %} 

## Tooltip for a specific node/connector

Tooltips can be customized for every node. Tooltip can be defined for individual node/connector by using the `Tooltip` property of that node/connector. In addition to that, you have to remove the **InheritTooltip** option from the `Constraints` of that node/connector. The following code example illustrates how to customize tooltips for individual elements.

{% highlight c# %}

            //Enables tooltip for any node/connector
            DiagramProperties Model = new DiagramProperties();
            Node Node = new Node(); 
            Node.Name = "elizabeth"; 
            //Remove InheritTooltip not to inherit the tooltip defined in model
            Node.Constraints = NodeConstraints.Default & ~NodeConstraints.InheritTooltip;
          
          
            //Defines mouse over tooltip for a node
            Node.Tooltip.TemplateId = "nodetooltiptemplate"; 
            Model.Nodes.Add(Node); 

            //Disables tooltip for any node/connector
            Node.Tooltip = null;
            Model.Nodes.Add(Node);

{% endhighlight %} 

## Tooltip alignments

### Tooltip relative to object

Diagram provides support to show tooltip around the node/connector that is hovered by mouse. You can align the tooltip as you wish by using the `Alignment` and `Margin` properties of tooltip. The `RelativeMode` property of tooltip defines whether the tooltip has to be displayed around the object or at the mouse position. The following code example illustrates how to position the tooltip around object.

{% highlight html %}

    <!--Define tooltip template-->
    <script type="text/x-jsrender" id="mouseovertooltip">
        <div style="background-color: #F08080; color: white; padding: 5px;">
            <span style="padding: 5px;"> {{:addInfo.Designation}} </span>
        </div>
    </script>

{% endhighlight %}

{% highlight c# %}

            //Initialize the Diagram Model
            DiagramProperties Model = new DiagramProperties();

            Model.Width = "100%";
            Model.Height = "700px";
            //Defines mouse over tooltip
            Model.Tooltip = new Tooltip();
            Model.Tooltip.TemplateId = "mouseovertooltip";
            Model.Tooltip.Alignment.Horizontal = HorizontalAlignment.Center;
            Model.Tooltip.Alignment.Vertical = VerticalAlignment.Center;

            Label Label = new Label() { Text = "Elizabeth", FontColor = "white", Bold = true };
            Collection Labels = new Collection();
            Labels.Add(Label);
            BasicShape Node = new BasicShape();

            //Defines nodes
            Node.Name = "elizabeth";
            Node.Width = 70; Node.Height = 40;
            Node.OffsetX = 100; Node.OffsetY = 100;
            //Removes inherit tooltip from constraints
            Node.Constraints = NodeConstraints.Default & ~NodeConstraints.InheritTooltip;
            //Defines tooltip for a node
            Node.Tooltip = new Tooltip();
            //Defines template id
            Node.Tooltip.TemplateId = "mouseovertooltip";
            //Sets to show tooltip around the element
            Node.Tooltip.RelativeMode = RelativeMode.Object;
            //Sets the alignment properties

            //Defines horizontal alignment around node
            Node.Tooltip.Alignment.Horizontal = HorizontalAlignment.Center;

            //Defines vertical alignment around node
            Node.Tooltip.Alignment.Vertical = VerticalAlignment.Top;
            Node.AddInfo = new Dictionary<string, object>();
            Dictionary<string, object> AddInfo = new Dictionary<string, object>();
            AddInfo.Add("Designation", "Managing Director");
            Node.AddInfo = AddInfo;
            Model.Nodes.Add(Node);
            
{% endhighlight %}

![](/Tooltip_images/Tooltip_img5.png)

### Tooltip relative to mouse position

To display the tooltip at mouse position, you need to set "Mouse" option to the `RelativeMode` property of tooltip. The following code example illustrates how to show tooltip at mouse position.

{% highlight c# %}

             //Initialize the Diagram Model
            DiagramProperties Model = new DiagramProperties();

            Model.Width = "100%";
            Model.Height = "700px";
            //Defines mouse over tooltip
            Model.Tooltip = new Tooltip();
            Model.Tooltip.TemplateId = "mouseovertooltip";
            Model.Tooltip.Alignment.Horizontal = HorizontalAlignment.Center;
            Model.Tooltip.Alignment.Vertical = VerticalAlignment.Center;

            Label Label = new Label() { Text = "Elizabeth", FontColor = "white", Bold = true };
            Collection Labels = new Collection();
            Labels.Add(Label);
            BasicShape Node = new BasicShape();

            //Defines nodes
            Node.Name = "elizabeth";
            Node.Width = 70; Node.Height = 40;
            Node.OffsetX = 100; Node.OffsetY = 100;
            //Removes inherit tooltip from constraints
            Node.Constraints = NodeConstraints.Default & ~NodeConstraints.InheritTooltip;
            //Disables tooltip for a node
            //Defines template id
            Node.Tooltip.TemplateId = "mouseovertooltip";
            //Sets to show tooltip around the element
            Node.Tooltip.RelativeMode = RelativeMode.Mouse;
            //Sets margin - absolute distance between mouse position and tooltip
            Node.Tooltip.Margin.Top = 10;
            Node.Tooltip.Margin.Left = 10;

            Node.AddInfo = new Dictionary<string, object>();
            Dictionary<string, object> AddInfo = new Dictionary<string, object>();
            AddInfo.Add("Designation", "Managing Director");
            Node.AddInfo = AddInfo;
            Model.Nodes.Add(Node);

{% endhighlight %}

![](/Tooltip_images/Tooltip_img6.png)


