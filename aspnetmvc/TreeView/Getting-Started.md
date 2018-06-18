---
layout: post
title: Getting Started with TreeView | TreeView | ASP.NET MVC | Syncfusion
description:  To get start with TreeView by adding references
platform: ejmvc
control: TreeView
documentation: ug
---

# Getting started	

This section explains briefly about how to create a TreeView in ASP.NET MVC platform.

## Create your first TreeView in MVC

Create a MVC Project and add necessary assemblies, CSS and scripts with the help of the given [MVC-Getting Started](http://help.syncfusion.com/aspnetmvc/getting-started) documentation. After creating this project, you can create a TreeView in following ways.

## TreeView using Helper element

You can create a tree using “Items” API of TreeView control. Here there is no necessary to use a data source for rendering TreeView. 

In the view page, add TreeView helper as shown below. It will render the TreeView with specified items.
    
    {% highlight razor %}

    @Html.EJ().TreeView("tree").Items(items =>
                {
                    items.Add().Text("Item 1").Children(child =>
                    {
                        child.Add().Text("Item 1.1").Children(child1 =>
                        {
                            child1.Add().Text("Item 1.1.1");
                        });
                    });
                    items.Add().Text("Item 2").Children(child =>
                    {
                        child.Add().Text("Item 2.1");
                        child.Add().Text("Item 2.2");
                    });
                    items.Add().Text("Item 3").Children(child =>
                    {
                        child.Add().Text("Item 3.1");
                    });
                })
                
    {% endhighlight %}       
    
## TreeView using Data Binding

Another way of creating TreeView is binding with the data source, you can bind local data source to create a TreeView. 

Render TreeView with local data source.

In the model page, specify the TreeView node properties as shown below.
    
    

    {% highlight c# %}

    public class LoadData
    {
        public int Id { get; set; }
        public int Parent { get; set; }
        public string Text { get; set; }
    }
    
    {% endhighlight %}
    
    
    
In the controller page, create a data list which contains the details about tree nodes.
    
    
    
    {% highlight c# %}

    public partial class TreeViewController : Controller
    {
        List<LoadData> load = new List<LoadData>();
        public ActionResult TreeViewFeatures()
        {
            load.Add(new LoadData { Id = 1, Parent = 0, Text = "Item 1" });
            load.Add(new LoadData { Id = 2, Parent = 0, Text = "Item 2" });
            load.Add(new LoadData { Id = 3, Parent = 0, Text = "Item 3" });
            load.Add(new LoadData { Id = 4, Parent = 1, Text = "Item 1.1" });
            load.Add(new LoadData { Id = 5, Parent = 1, Text = "Item 1.2" });
            load.Add(new LoadData { Id = 6, Parent = 3, Text = "Item 3.1" });
            ViewBag.datasource = load;
            return View();
        }
    }
    
    {% endhighlight %}
    
    
    
Above data can be directly assigned to [DataSource](http://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.TreeViewFieldsBuilder~Datasource.html) property and mapping data fields with respect to the mapper field in order to form TreeView.
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("tree")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
        )
    )
    
    {% endhighlight %}
    
    
## Create Instance for TreeView

You can create an instance for existing TreeView in following ways. Once a reference has been established, you can use the [API’s](http://help.syncfusion.com/js/api/ejtreeview) of TreeView to control its behavior.
    
        
    {% highlight javascript %}
    
    <script type="text/javascript">
        //Specify this after your TreeView creation
        //create instance for TreeView
        var treeObj = $("#treeView").ejTreeView('instance');
        //or
        var treeObj1 = $("#treeView").data("ejTreeView");
    </script>
    
    {% endhighlight %}
    
    
    
N>**To configure the API settings after TreeView creation, please refer [API configuration](http://help.syncfusion.com/js/api-configuration), [Invoking Methods](http://help.syncfusion.com/js/invoking-methods)**.
 
## TreeView events

EJ MVC TreeView supports all the [events](http://help.syncfusion.com/js/api/ejtreeview#events) which is available in EJ TreeView. Refer the following code example to specify an event using HTML helper of EJ MVC TreeView.
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
        )
        .ClientSideEvents(events =>
            events.NodeExpand("onNodeExpanded")
            .NodeCollapse("onNodeCollapsed")
            .NodeSelect("onNodeSelected")
        )
    )
    
    <script type="text/javascript">
        function onNodeCollapsed(args) {
            //Handle the node collapse event
        }
    
        function onNodeExpanded(args) {
            //Handle the node expand event
        }
    
        function onNodeSelected(args) {
            //Handle the node select event
        }
    </script>
    
    {% endhighlight %}
    
    
 