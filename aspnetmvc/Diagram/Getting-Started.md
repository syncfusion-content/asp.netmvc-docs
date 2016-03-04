---
layout: post
title: Getting started with Syncfusion Essential Diagram for ASP.NET MVC
description: Getting started walk through to create your first Flow Diagram and Organizational Chart Diagram
platform: ejmvc
control: Diagram
documentation: ug
---

# Getting Started

Getting started with your MVC Diagram is easy. You can start by creating a simple flow chart.

## Flow Diagram

### Initialize Diagram
1\. Create an ASP.NET MVC application. You can refer [MVC Getting Started documentation](http://help.syncfusion.com/aspnetmvc/getting-started) to create a new project and to add necessary assemblies and script files.

2\. Add a placeholder `div` element to initialize diagram control

{% highlight razor %}

<div>
    @Html.EJ().Diagram("diagram").Width("100%").Height("600px")
</div>

{% endhighlight %}

3\. This creates an empty diagram

![](/aspnetmvc/Diagram/Getting-Started_images/Getting-Started_img1.png)

### Create and add Node

Let us create and add a `node` with specific position, size, label and shape.
{% tabs %}
{% highlight razor %}

@*Initializes diagram control*@
<div>
   @Html.EJ().Diagram("diagram", ViewData["diagramModel"] as Syncfusion.JavaScript.DataVisualization.Models.DiagramProperties)
</div>

{% endhighlight %}

{% highlight c# %}

   DiagramProperties model = new DiagramProperties();
   FlowShape start = CreateNode("Start", 140, 50, 300, 50, FlowShapes.Terminator, "Start");
   model.Nodes.Add(start);
   ViewData["diagramModel"] = model;          
            
   FlowShape CreateNode(string name, int width, int height, int offsetX, int offsetY, FlowShapes shape, string text)
   {
       FlowShape node = new FlowShape()
       {
           Shape = shape,
           Name = name,
           Width = width,
           Height = height,
           OffsetX = offsetX,
           OffsetY = offsetY,
           Labels = new Collection() { new Label() { Text = text } }
       };
       return node;
   }
  
{% endhighlight %}
{% endtabs %}

N> `Labels` property is an array, which indicates that more than one label can be added to a node.

Added node will be displayed in diagram as shown below.

![](/aspnetmvc/Diagram/Getting-Started_images/Getting-Started_img2.png)

### Connect nodes

* Create another `node` with another set of data.

{% highlight c# %}

    DiagramProperties model = new DiagramProperties();
    model.Nodes.Add(CreateNode("Start", 140, 50, 300, 50, FlowShapes.Terminator, "Start"));
    model.Nodes.Add(CreateNode("Init", 140, 50, 300, 140, FlowShapes.Process, "var i = 0;"));
    ViewData["diagramModel"] = model;
            
    FlowShape CreateNode(string name, int width, int height, int offsetX, int offsetY, FlowShapes shape, string text)
    {
        FlowShape node = new FlowShape()
        {
            Shape = shape,
            Name = name,
            Width = width,
            Height = height,
            OffsetX = offsetX,
            OffsetY = offsetY,
            Labels = new Collection() { new Label() { Text = text } }
        };
        return node;
    }
    
{% endhighlight %}

Connect these two nodes by adding a `connector` into `Connectors` collection with reference to source and target end.

{% highlight c# %}
    
    //Add a connector to `Connectors` collection of diagram model
    model.Connectors.Add(ConnectNodes("connector1", "Start", "Init"));
    
    Connector ConnectNodes(string name, string source, string target)
    {
        return new Connector()
        {
            Name = name,
            SourceNode = source,
            TargetNode = target,
            Segments = new Collection() { 
                new Segment(Segments.Orthogonal)
            }
        };
    }

{% endhighlight %}

* `Connector` connects the two nodes as shown below.

![](/aspnetmvc/Diagram/Getting-Started_images/Getting-Started_img3.png)

* Default values for all nodes and connectors can be set using default settings. For example if all nodes have same `Width` and `Height`, we can move such properties into `DefaultSettings`. Above code can be rewritten as shown below.

{% highlight c# %}
    DiagramProperties model = new DiagramProperties();
    //Default Settings
    model.DefaultSettings.Node = new Node() { Type = Shapes.Flow, Width = 140, Height = 50, OffsetX = 300 };
    model.DefaultSettings.Connector = new Connector()
    {
        Labels = new Collection() { new Label() { FillColor = "white" } },
        Segments = new Collection() { new Segment(Segments.Orthogonal) }
    };
    //Create Nodes
    model.Nodes.Add(CreateNode("Start", 50, FlowShapes.Terminator, "Start"));
    model.Nodes.Add(CreateNode("Init", 140, FlowShapes.Process, "var i = 0;"));
    //Connect Nodes
    model.Connectors.Add(ConnectNodes("connector1", "Start", "Init"));
    ViewData["diagramModel"] = model;
        
    Connector ConnectNodes(string name, string source, string target)
    {
        return new Connector()
        {
            Name = name,
            SourceNode = source,
            TargetNode = target
        };
    }

    FlowShape CreateNode(string name, int width, int height, int offsetX, int offsetY, FlowShapes shape, string text)
    {
        FlowShape node = new FlowShape()
        {
            Shape = shape,
            Name = name,
            OffsetY = offsetY,
            Labels = new Collection() { new Label() { Text = text } }
        };
        return node;
    }

{% endhighlight %}

### Complete flow diagram

Similarly we can add required nodes and connectors to form a complete flow diagram.

{% highlight c# %}

      //Initialize model properties
      DiagramProperties model = new DiagramProperties();
      //Default Settings
      model.DefaultSettings.Node = new Node() { Type = Shapes.Flow, Width = 140, Height = 50, OffsetX = 300 };
      model.DefaultSettings.Connector = new Connector()
      {
          Labels = new Collection() { new Label() { FillColor = "white" } },
          Segments = new Collection() { new Segment(Segments.Orthogonal) }
      };
      //Create Nodes
      model.Nodes.Add(CreateNode("Start", 50, FlowShapes.Terminator, "Start"));
      model.Nodes.Add(CreateNode("Init", 140, FlowShapes.Process, "var i = 0;"));
      model.Nodes.Add(CreateNode("Condition", 230, FlowShapes.Decision, "i < 10?"));
      model.Nodes.Add(CreateNode("Print", 320, FlowShapes.PreDefinedProcess, "i < 10?"));
      model.Nodes.Add(CreateNode("Increment", 410, FlowShapes.Process, "i < 10?"));
      model.Nodes.Add(CreateNode("End", 500, FlowShapes.Terminator, "i < 10?"));

      //Connect Nodes
      model.Connectors.Add(ConnectNodes("connector1", "Start", "Init"));
      model.Connectors.Add(ConnectNodes("connector2", "Init", "Condition"));
      model.Connectors.Add(ConnectNodes("connector3", "Condition", "Print", "Yes"));
      model.Connectors.Add(ConnectNodes("connector4", "Condition", "End", "No",
          new Segment() { Type = Segments.Orthogonal, Direction = "right", Length = 30 }));
      model.Connectors.Add(ConnectNodes("connector5", "Print", "Increment"));
      model.Connectors.Add(ConnectNodes("connector5", "Increment", "Condition", "",
        new Segment() { Type = Segments.Orthogonal, Direction = "left", Length = 30 }));

      ViewData["diagramModel"] = model;
      
      
      //Helper methods      
     Connector ConnectNodes(string name, string source, string target, string text = "", Segment segment = null)
     {
         Connector connector = new Connector()
         {
             Name = name,
             SourceNode = source,
             TargetNode = target,
             Labels = new Collection() { new Label() { Text = text } }
         };
         if (segment != null) connector.Segments = new Collection() { segment };
         return connector;
     }

     FlowShape CreateNode(string name, int offsetY, FlowShapes shape, string text)
     {
         FlowShape node = new FlowShape()
         {
             Shape = shape,
             Name = name,
             OffsetY = offsetY,
             Labels = new Collection() { new Label() { Text = text } }
         };
         return node;
     }

{% endhighlight %}

Final flow chart will looks as shown below.

![](/aspnetmvc/Diagram/Getting-Started_images/Getting-Started_img4.png)

## Automatic organization chart

In 'Flow Diagram' section we saw how to create a diagram manually, now let us see how to create and position diagram automatically.

### Initialize diagram
Initializing diagram is already discussed in Flow Diagram > [Initialize diagram](#initialize-diagram) section.

### Business object (Employee information)

* Define Employee Information as JSON data. The following code example shows an employee array whose,
	* `Name` is used as a unique identifier and
	* `ReportingPerson` is used to identify the person to whom an employee report to, in the organization.

{% highlight razor %}

//Initialize data source - Saved in a JSON file...
{
    data: [
        { Name: "Elizabeth", Role: "Director" },
        { Name: "Christina", ReportingPerson: "Elizabeth", Role: "Manager" },
        { Name: "Yoshi", ReportingPerson: "Christina", Role: "Lead" },
        { Name: "Philip", ReportingPerson: "Christina", Role: "Lead" },
        { Name: "Yang", ReportingPerson: "Elizabeth", Role: "Manager" },
        { Name: "Roland", ReportingPerson: "Yang", Role: "Lead" },
        { Name: "Yvonne", ReportingPerson: "Yang", Role: "Lead" }
    ]
}

{% endhighlight %}

### Map data source

* You can configure this "Employee Information" with Diagram, so that the node and connector are automatically generated using mapping properties. The following code examples show how dataSourceSetting is used to map id and parent with property name identifiers for employee information.

{% highlight c# %}

     DiagramProperties model = new DiagramProperties();
     model.DataSourceSettings.DataSource = GetEmployeeData();
     model.DataSourceSettings.Id = "Name";
     model.DataSourceSettings.Parent = "ReportingPerson";
         
     Array GetEmployeeData()
     {
         string text = System.IO.File.ReadAllText(Server.MapPath("~/App_Data/employee.json"));
         Dictionary<string, object> data = (Dictionary<string, object>)new JavaScriptSerializer().DeserializeObject(text);
         return (Array)data["data"];
     }

{% endhighlight %}

### Visualize employee

Following code examples indicate how to define the default appearance of node and connector using defaultSettings. The NodeTemplate is used to update each node based on employee data.

{% tabs %}
{% highlight c# %}

     DiagramProperties model = new DiagramProperties();

     //Configure data source
     model.DataSourceSettings.DataSource = GetEmployeeData();
     model.DataSourceSettings.Id = "Name";
     model.DataSourceSettings.Parent = "ReportingPerson";

     //Default Settings
     model.DefaultSettings.Node = new Node()
     {
         Width = 70,
         Height = 30,
         Shape = { Type = Shapes.Rectangle, CornerRadius = 5 },
         Labels = new Collection() { new Label() { FontSize = 11, Bold = true, FontFamily = "Segoe UI", FontColor = "white" } }
     };

     model.DefaultSettings.Connector = new Connector()
     {
         Segments = new Collection() { new Segment(Segments.Orthogonal) }
     };

     model.NodeTemplate = "nodeTemplate";
     ViewData["diagramModel"] = model;                 

{% endhighlight %}

{% highlight razor %}

    //To represent the roles
    var codes = {
    	 Director: "rgb(0, 139,139)",
    	 Manager: "rgb(30, 30,113)",
    	 Lead: "rgb(0, 100,0)"
    }

    // Bind custom data with node
    function nodeTemplate(diagram, node) {
    	 node.labels[0].text = node.Name;
    	 node.fillColor = codes[node.Role];
    }

{% endhighlight %}
{% endtabs %}

### Apply org chart layout

* Next you need to arrange nodes in an organizational chart structure, and to do this you can apply layout as shown in following code example. You can see that spacing, margin and orientation are defined, that can also be customized based on the needs.

{% highlight c# %}

     DiagramProperties model = new DiagramProperties();
     model.Layout.Type = LayoutTypes.OrganizationalChart;
     model.Layout.MarginX = 10;
     model.Layout.MarginY = 50;
     model.Layout.HorizontalSpacing = 50;
     model.Layout.VerticalSpacing = 50;
     model.Layout.Orientation = LayoutOrientations.TopToBottom;

{% endhighlight %}

* The Employee details are displayed in the Diagram as follows.

![](/aspnetmvc/Diagram/Getting-Started_images/Getting-Started_img5.png)
