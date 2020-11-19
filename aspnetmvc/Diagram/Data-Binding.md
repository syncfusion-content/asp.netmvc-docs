---
layout: post
title: Populate Diagram from external data sources
description: How to populate the Diagram from the local data, remote data, or HTML tables?
platform: ejmvc
control: Diagram
documentation: ug
---

# Data Binding

* Diagram can be populated with the nodes and connectors based on the information provided from an external data source.
* Diagram exposes its specific data-related properties allowing you to specify the data source fields from where the node information has to be retrieved from.

To explore those properties, see [Data source settings](http://help.syncfusion.com/cr/aspnetmvc/Syncfusion.JavaScript.DataVisualization.Models.Diagram.DataSourceSettings.html "Data source settings")

* Diagram supports three different kinds of Data binding.
	* Local Data
	* Remote Data
	* HTML Table Data

## Local Data

Diagram can be populated based on the user defined JSON data (**Local Data**) by mapping the relevant data source fields.

To map the user defined JSON data with Diagram, you have to configure the fields of `DataSourceSettings`. The following code example illustrates how to bind local data with the Diagram.

{% tabs %}
{% highlight razor %}
@Html.EJ().Diagram("Diagram", ViewData["diagramModel"] as Syncfusion.JavaScript.DataVisualization.Models.DiagramProperties)

<script type="text/javascript">
    //Binds custom JSON with node
    function nodeTemplate(diagram, node) {
        // Sets the Name field of JSON data as label.
        node.labels[0].text = node.Name;
    }
</script>
{% endhighlight %}

{% highlight c# %}
public ActionResult Index()
{
    DiagramProperties model = new DiagramProperties();
    //Uses layout to auto-arrange nodes on the Diagram page
    model.Layout.Type = LayoutTypes.HierarchicalTree;
    model.Layout.HorizontalSpacing=30;
    model.Layout.VerticalSpacing=30;
    
    //Sets the default properties for nodes and connectors
    Label label = new Label() { Name = "label1", FontColor = "white", Bold = true };
    model.DefaultSettings.Node = new Node() { Width = 100, Height = 40, FillColor = "darkcyan" };
    model.DefaultSettings.Node.Labels.Add(label);
    model.DefaultSettings.Connector = new Connector()
    {
        Segments = new Collection() { new Segment(Segments.Orthogonal) },
        TargetDecorator = new Decorator() { Shape = DecoratorShapes.None },
    };  
    
    //Configures data source for Diagram
    //Defines the unique field of each JSON data
    model.DataSourceSettings.Id = "Name";
    //Defines the parent field which builds the relationship
    model.DataSourceSettings.Parent = "ReportingPerson";
    //Sets the local data source to the diagram.
    model.DataSourceSettings.DataSource = GetDataSource(); 
    //Initializes the node template.
    model.NodeTemplate = "nodeTemplate";
    
    ViewData["diagramModel"] = model;
    return View();
}
public Array GetDataSource()
{
    String allText = System.IO.File.ReadAllText(Server.MapPath("~/App_Data/data.json"));
    Dictionary<string, object> requestArgs = (Dictionary<string, object>)new JavaScriptSerializer().DeserializeObject(allText);
    requestArgs = (Dictionary<string, object>)requestArgs["root"];
    return (Array)requestArgs.Values.ElementAt(0);
}
{% endhighlight %}

{% highlight js %}
{root: {data: [ 
    { "Name": "Director" },
    { "Name": "Manager", "ReportingPerson": "Director" },
    { "Name": "TeamLead", "ReportingPerson": "Director" },
    { "Name": "Software Developer", "ReportingPerson": "TeamLead" },
    { "Name": "Testing engineer", "ReportingPerson": "TeamLead" },
    { "Name": "Software Developer", "ReportingPerson": "Manager" },
    { "Name": "Testing engineer", "ReportingPerson": "Manager" }
]}}
{% endhighlight %}
{% endtabs %}

![](Data-Binding_images/Data-Binding_img1.png)

## Remote Data

You can bind the Diagram with Remote Data by using dataManager.

* DataManager supports the following types of data-binding: JSON, Web Services, oData.
* It uses two different classes: ej.DataManager for processing and ej.Query for serving data. ej.DataManager communicates with data source and ej.Query generates data queries that are read by the dataManager.
* To learn more, refer to [Data Manager](/aspnetmvc/DataManager/Getting-Started "Data Manager").

To bind remote data to the Diagram, you have to configure the fields of `DataSourceSettings`. The following code illustrates how to bind remote data to the Diagram.

{% tabs %}
{% highlight razor %}
@Html.EJ().Diagram("Diagram", ViewData["diagramModel"] as Syncfusion.JavaScript.DataVisualization.Models.DiagramProperties)

<script type="text/javascript">
    //Binds custom JSON with node
    function nodeTemplate(diagram, node) {
        // Sets the Name field of JSON data as label.
        node.labels[0].text = node.FirstName;
    }
</script>
{% endhighlight %}

{% highlight c# %}
public ActionResult Index()
{
    DiagramProperties model = new DiagramProperties();
    
    //Uses layout to auto-arrange nodes on the Diagram page
    model.Layout.Type = LayoutTypes.HierarchicalTree;
    model.Layout.HorizontalSpacing = 30;
    model.Layout.VerticalSpacing = 30;

    //Sets the default properties for nodes and connectors
    Label label = new Label() { Name = "label1", FontColor = "white", Bold = true };
    model.DefaultSettings.Node = new Node() { Width = 100, Height = 40, FillColor = "darkcyan" };
    model.DefaultSettings.Node.Labels.Add(label);
    model.DefaultSettings.Connector = new Connector()
    {
        Segments = new Collection() { new Segment(Segments.Orthogonal) },
        TargetDecorator = new Decorator() { Shape = DecoratorShapes.None },
    };

    //Initializes the node template.
    model.NodeTemplate = "nodeTemplate";

    model.DataSourceSettings.DataSource = "http://mvc.syncfusion.com/Services/Northwnd.svc/";
    model.DataSourceSettings.Query = "ej.Query().from('Employees').select('EmployeeID,ReportsTo,FirstName')";
    model.DataSourceSettings.Id = "EmployeeID";
    model.DataSourceSettings.Parent = "ReportsTo";
    model.DataSourceSettings.TableName = "Employees";   
}
{% endhighlight %}
{% endtabs %}

![](Data-Binding_images/Data-Binding_img2.png)

## HTML Table Data

The Diagram provides support to populate the Diagram from the **HTML table**. It is flexible to convert HTML table to Diagram by using **Data Manager**.

The following code illustrates how to convert HTML table to the Diagram.

{% tabs %}
{% highlight c# %}

                DiagramProperties Model = new DiagramProperties();
                Model.Height = "600px";
                Model.Width = "600px";
                //Initializes the node template.
                Model.NodeTemplate = "nodeTemplate";
                Model.Layout.Type = LayoutTypes.HierarchicalTree;
                Model.Layout.VerticalSpacing = 30;
                Model.Layout.HorizontalSpacing = 30;
                Model.DefaultSettings.Node = new Node()
                {
                    Width = 120,
                    Height = 40,
                    BorderColor = "transparent",
                    Labels = new Collection() { new Label() { Name = "label1", FontColor = "#ffffff" } }
                };
                Model.DefaultSettings.Connector = new Connector()
                {
                    Segments = new Collection() { new Segment(Segments.Orthogonal) },
                    TargetDecorator = new Decorator() { FillColor = "#4F4F4F", BorderColor = "#4F4F4F" }
                };
                ViewData["Diagram"] = Model;
                
{% endhighlight %}
{% highlight razor %}

@Html.EJ().Diagram("Diagram", ViewData["diagramModel"] as Syncfusion.JavaScript.DataVisualization.Models.DiagramProperties)
@using Syncfusion.JavaScript.DataVisualization.DiagramEnums 
@using Syncfusion.JavaScript.DataVisualization.Models.Diagram
@using Syncfusion.JavaScript.DataVisualization.Models.Collections

@(Html.EJ().Diagram("Diagram").Width("100%").Height("600px")
@*Configures data source for Diagram*@
.DataSourceSettings(e => 
{ 
    e.DataSource(dataSource => dataSource.Table("#binding"))
    .Id("Id")
    .Parent("ReportingPerson");
}))

<!-- HTML Table -->
<script id="binding" type="text/template" >
    <table style="display: none">
        <thead>
            <tr>
                <th>Id</th>
                <th>Designation</th>
                <th>Color</th>
                <th>ReportingPerson</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>parent</td>
                <td>Managing Director</td>
                <td>#822b86</td>
                <td>null</td>
            </tr>
            <tr>
                <td>1</td>
                <td>Project manager</td>
                <td>#3c418d</td>
                <td>parent</td>
            </tr>
            <tr>
                <td>2</td>
                <td>Project manager</td>
                <td>#108d8d</td>
                <td>parent</td>
            </tr>
            <tr>
                <td>3</td>
                <td>Product Lead</td>
                <td>#3c418d</td>
                <td>1</td>
            </tr>
            <tr>
                <td>4</td>
                <td>Product Lead</td>
                <td>#3c418d</td>
                <td>1</td>
            </tr>
            <tr>
                <td>5</td>
                <td>Product Lead</td>
                <td>#108d8d</td>
                <td>2</td>
            </tr>
            <tr>
                <td>6</td>
                <td>Product Lead</td>
                <td>#108d8d</td>
                <td>2</td>
            </tr>
            <tr>
                <td>7</td>
                <td>S/W engineer</td>
                <td>#3c418d</td>
                <td>4</td>
            </tr>
            <tr>
                <td>8</td>
                <td>S/W engineer</td>
                <td>#3c418d</td>
                <td>4</td>
            </tr>
        </tbody>
    </table>
</script>

<script type="text/javascript">
//Binds custom JSON with node
    function nodeTemplate(diagram, node) {
        node.labels[0].text = node.Designation;
        node.fillColor = node.Color;
    }
</script>
{% endhighlight %}
{% endtabs %}

![](Data-Binding_images/Data-Binding_img4.png)

# CRUD

* This feature allows the user to read the DataSource and perform add/edit/delete the data in datasource at runtime.

## Read DataSource

* This feature allows you to define nodes and connectors collection in the DataSource and ConnectionDataSource respectively.
* We can set the data collection in the model’s DataSourceSettings DataSource property. The nodes will be generated based on the data specified in the DataSource. 
* We can set the connector collection in the model’s DataSourceSettings ConnectionDataSource property.
* If we have a data (data will be set in the DataSource property) with parent relationship in the database and also defined the connector in the ConnectionDataSource simultaneously, then the connectors set in the ConnectionDataSource will be considered as a priority to render the connector.

{% tabs %}
{% highlight c# %}
 
         model.DataSourceSettings = new DataSourceSettings()
            {
               //set the data collection
                DataSource = DiagramContext.HierarchicalData.ToList(),
                //bind the column name to the Id property which generates the unique name for the object
                Id = "Name",
                //Specify the custom property/columns which is available in the DataSource.
                CustomFields = new List<string>() 
                {
                    "Description",
                    "Color"
                },
                ConnectionDataSource = new ConnectionDataSourceSettings()
                {
                    //set the connector collection
                    DataSource = DiagramContext.HierarchicalDetails.ToList(),
                  //bind the column name to the Id property which generates the unique name for the object 
                    Id = "Name",
                    SourceNode = "SourceNode",
                    TargetNode = "TargetNode",

                //Specify the custom property/columns which is available in the ConnectionDataSource.
                 CustomFields = new List<string>() 
                    {
                    "Description",
                    "Color"
                     },
                }
            };
            
{% endhighlight %}
{% endtabs %}

## How to perform Editing at runtime

We need to specify the URL for create/update/destroy of nodes and connectors.

## InsertData

* The following code example illustrates how to send the newly added/inserted data from client to server side.

{% tabs %}
{% highlight js %}

var diagram = $("#diagram").ejDiagram("instance");
//Sends the newly added nodes/connectors from client side to the server side through the URL which is specified in server side.
diagram.insertData();

{% endhighlight %}

{% highlight c# %}
 
            model.DataSourceSettings = new DataSourceSettings()
            {
                CrudAction = new CRUDAction()
                {
                   //Specify the method name which is used to get the newly added data from client side to the server side 
                    Create = "/Diagram/InsertShape",                
                },
                ConnectionDataSource = new ConnectionDataSourceSettings()
                {
 
                    CrudAction = new CRUDAction()
                    {
                    //Specify the method name which is used to get the newly added data from client side to the server side                         
                     Create = "/Diagram/InsertConnector",
                    }
                }
            };

        [HttpPost]
        public void InsertShape(List<HierarchicalData> data)
        {
            foreach (HierarchicalData hierarchicalData in data)
            {
                DiagramContext.HierarchicalData.InsertOnSubmit(hierarchicalData);
                DiagramContext.SubmitChanges();
            }
        }

        [HttpPost]
        public void InsertConnector(List<HierarchicalDetail> data)
        {
            foreach (HierarchicalDetail hierarchicalData in data)
            {
                DiagramContext.HierarchicalDetails.InsertOnSubmit(hierarchicalData);
                DiagramContext.SubmitChanges();
            }
        }

{% endhighlight %}
{% endtabs %}

## UpdateData

* The following code example illustrates how to send the updated data from client to the server side.

{% tabs %}
{% highlight js %}

var diagram = $("#diagram").ejDiagram("instance");
//Sends the updated nodes/connectors from client side to the server side through the URL which is specified in server side.
diagram.updateData();

{% endhighlight %}

{% highlight c# %}
 
        model.DataSourceSettings = new DataSourceSettings()
            {
                CrudAction = new CRUDAction()
                {
                 //Specify the method name which is used to get the updated data from client side to the server side                         
                    Update = "/Diagram/UpdateShape",                
                },
                ConnectionDataSource = new ConnectionDataSourceSettings()
                {
                    CrudAction = new CRUDAction()
                    {
                        //Specify the method name which is used to get the updated data from client side to the server side                        
                        Update = "/Diagram/UpdateConnector",
                    }
                }
            };
        [HttpPost]
        public void UpdateShape(List<HierarchicalData> data)
        {
            foreach (HierarchicalData hierarchicalData in data)
            {
                HierarchicalData originalData = DiagramContext.HierarchicalData.Single(h => h.Name == hierarchicalData.Name);
                originalData.Description = hierarchicalData.Description;
                originalData.Color = hierarchicalData.Color;
                DiagramContext.SubmitChanges();
            }
            
        }
        [HttpPost]
        public void UpdateConnector(List<HierarchicalDetail> data)
        {
            foreach (HierarchicalDetail hierarchicalData in data)
            {
                HierarchicalDetail originalData = DiagramContext.HierarchicalDetails.Single(h => h.Name == hierarchicalData.Name);
                originalData.SourceNode = hierarchicalData.SourceNode;
                originalData.TargetNode = hierarchicalData.TargetNode;
                DiagramContext.SubmitChanges();
            }
        }

{% endhighlight %}
{% endtabs %}

## DeleteData

The following code example illustrates how to send the deleted data from client to the server side.

{% tabs %}
{% highlight js %}

var diagram = $("#diagram").ejDiagram("instance");
//Sends the deleted nodes/connectors from client side to the server side through the URL which is specified in server side.
diagram.removeData();

{% endhighlight %}

{% highlight c# %}
 
       model.DataSourceSettings = new DataSourceSettings()
            {
                CrudAction = new CRUDAction()
                {
                    
                     //Specify the method name which is used to get the deleted data from client side to the server side                                            
                      Destroy = "/Diagram/DeleteShape",                
                },
                ConnectionDataSource = new ConnectionDataSourceSettings()
                {
                    CrudAction = new CRUDAction()
                    {
                      //Specify the method name which is used to get the updated data from client side to the server side                        
                        Destroy = "/Diagram/DeleteConnector",
                    }
                }
            };
        [HttpPost]
        public void DeleteShape(List<HierarchicalData> data)
        {
            foreach (HierarchicalData hierarchicalData in data)
            {
                HierarchicalData originalData = DiagramContext.HierarchicalData.Single(h => h.Name == hierarchicalData.Name);
                DiagramContext.HierarchicalData.DeleteOnSubmit(originalData);
                DiagramContext.SubmitChanges();
            }
        }
        [HttpPost]
        public void DeleteConnector(List<HierarchicalDetail> data)
        {
            foreach (HierarchicalDetail hierarchicalData in data)
            {
                HierarchicalDetail originalData = DiagramContext.HierarchicalDetails.Single(h => h.Name == hierarchicalData.Name);
                DiagramContext.HierarchicalDetails.DeleteOnSubmit(originalData);
                DiagramContext.SubmitChanges();
            }
        }

{% endhighlight %}
{% endtabs %}