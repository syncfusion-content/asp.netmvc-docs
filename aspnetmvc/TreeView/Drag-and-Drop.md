---
layout: post
title: Drag and Drop | TreeView | ASP.NET MVC | Syncfusion
description: drag and drop
platform: ejmvc
control: TreeView
documentation: ug
---

# Drag and Drop

To perform drag and drop operation in TreeView specify “**AllowDragAndDrop**” as true. It allows you to drag and drop node in all level of same TreeView.
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
        )
        .AllowDragAndDrop(true)
    )
    
    {% endhighlight %}
    
    
    
N>**Note: TreeView provides much easier option to drop the dragged nodes at any levels by indicator lines with icons.**

## Position Indicators

TreeView provides much easier option to drop the dragged nodes at any levels by indicator lines with icons such as line, plus/minus and restrict icons while dragging and dropping the nodes. It represents exact position where the node to be dropped as sibling or child.

<table>
<tr>
<td>
    {{'**Indicators**'| markdownify }}
</td>
<td>
    {{'**description**'| markdownify }}
</td>
</tr>
<tr>
<td>
Plus icon
</td>
<td>
represents the dragged node to be added as child of targeted node
</td>
</tr>
<tr>
<td>
Minus with restrict icon
</td>
<td>
represents the dragged node not to be dropped at the hovered region
</td>
</tr>
<tr>
<td>
In between icon
</td>
<td>
represents the dragged node to be dropped in between the nodes as siblings
</td>
</tr>
</table>
## Restriction
You can restrict the dragged nodes to be dropped at siblings or children’s level by using “**AllowDropSibling**” and ’‘**AllowDropChild’** properties.
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
        )
        .AllowDragAndDrop(true)
        .AllowDropSibling(true)
        .AllowDropChild(false)
    )
    
    {% endhighlight %}
    
    
    
## Drag and drop between Trees

You can drag and drop tree nodes between two TreeView by setting “**AllowDragAndDrop**” as true along with “**AllowDragAndDropAcrossControl**” as true.

In the controller page, create a data List that contains the details about tree nodes.
    
    
    
    {% highlight c# %}
    
    public partial class TreeViewController : Controller
        {
            List<LoadData> tree1 = new List<LoadData>();
            List<LoadData> tree2 = new List<LoadData>();
            public ActionResult TreeViewFeatures()
            {
                tree1.Add(new LoadData { Id = 1, Parent = 0, Text = "Item 1" });
                tree1.Add(new LoadData { Id = 2, Parent = 0, Text = "Item 2" });
                tree1.Add(new LoadData { Id = 3, Parent = 0, Text = "Item 3" });
                tree1.Add(new LoadData { Id = 4, Parent = 0, Text = "Item 4" });
                tree1.Add(new LoadData { Id = 5, Parent = 1, Text = "Item 1.1" });
                tree1.Add(new LoadData { Id = 6, Parent = 1, Text = "Item 1.2" });
                tree1.Add(new LoadData { Id = 7, Parent = 1, Text = "Item 1.3" });
                tree1.Add(new LoadData { Id = 8, Parent = 3, Text = "Item 3.1" });
                tree1.Add(new LoadData { Id = 9, Parent = 3, Text = "Item 3.2" });
                tree1.Add(new LoadData { Id = 10, Parent = 5, Text = "Item 1.1.1" });
                ViewBag.datasource1 = tree1;
    
                tree2.Add(new LoadData { Id = 11, Parent = 0, Text = "Item 5" });
                tree2.Add(new LoadData { Id = 12, Parent = 0, Text = "Item 6" });
                tree2.Add(new LoadData { Id = 13, Parent = 0, Text = "Item 7" });
                tree2.Add(new LoadData { Id = 14, Parent = 0, Text = "Item 4" });
                tree2.Add(new LoadData { Id = 15, Parent = 11, Text = "Item 5.1" });
                tree2.Add(new LoadData { Id = 16, Parent = 11, Text = "Item 5.2" });
                tree2.Add(new LoadData { Id = 17, Parent = 11, Text = "Item 5.3" });
                tree2.Add(new LoadData { Id = 18, Parent = 13, Text = "Item 7.1" });
                tree2.Add(new LoadData { Id = 19, Parent = 13, Text = "Item 7.2" });
                tree2.Add(new LoadData { Id = 10, Parent = 15, Text = "Item 5.1.1" });
                ViewBag.datasource2 = tree2;
                return View();
            }
        }
        
    {% endhighlight %}
    
    
    
In the View page, add TreeView helper and map the properties defined in to the corresponding fields in data source and specify the drag and drop settings.
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeViewDrag")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource1)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
        )
        .AllowDragAndDrop(true)
        .AllowDropSibling(true)
        .AllowDropChild(true)
        .AllowDragAndDropAcrossControl(true)
    )
    <br />
    <br />
    @(Html.EJ().TreeView("treeViewDrop")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource2)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
        )
        .AllowDragAndDrop(true)
        .AllowDropSibling(true)
        .AllowDropChild(true)
        .AllowDragAndDropAcrossControl(true)
    )
    
    {% endhighlight %}
    
    
    
## Auto node structuring

You may not need to have two TreeView to be in same structured node while drag and drop the nodes between them. But after the node has been dropped, it should get structure of the TreeView node in which dropped. By default TreeView auto structure the node whenever you drop a node from different tree.
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeViewDrag")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource1)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
        )
        .AllowDragAndDrop(true)
        .AllowDropSibling(true)
        .AllowDropChild(true)
        .AllowDragAndDropAcrossControl(true)
        .ShowCheckbox(true)
    )
    <br />
    <br />
    @(Html.EJ().TreeView("treeViewDrop")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource2)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
        )
        .AllowDragAndDrop(true)
        .AllowDropSibling(true)
        .AllowDropChild(true)
        .AllowDragAndDropAcrossControl(true)
    )
    
    {% endhighlight %}
    
    
N>**Note: auto node structure only applicable for well-structured node object.**

