---
title: Checkboxes in TreeView | TreeView | ASP.NET MVC | Syncfusion
description: specify checkboxes in TreeView and its settings
platform: ejmvc
control: TreeView
documentation: UG
keywords: TreeView,  Syncfusion, EJ MVC TreeView, UG Document, Checkboxes
---

    
# Checkboxes

TreeView consists of built-in checkbox option and it can be displayed to the left of the tree node by setting the **ShowCheckbox** property as true. It allows you to select more than one node at a time.
 
## Indeterminate Checkboxes
 
TreeView supports tristate checkboxes in addition with standard two state checkboxes. By default Treeview has been enabled with tristate in checkboxes. You can enable 2-state checkboxes by using **AutoCheckParentNode** as false. 
    
    {% highlight razor %}
    
    @*initialize and bind the TreeView with local data*@
    @*shows each node with check boxes*@
    @*enable 2-state check boxes*@
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
        )
        .ShowCheckbox(true)
        .AutoCheckParentNode(false)
    )
    {% endhighlight %}
    
## Auto Checkable

By default checkbox state of child nodes depends up on parent node checkbox state and also parent node state gets updated based on child nodes state. You can turn off this option by setting **AutoCheck** as false to make independent parent and child nodes checkboxes. 
    
    {% highlight razor %}
    
    @*initialize and bind the TreeView with local data*@
    @*shows each node with check boxes*@
    @*turns off auto check of parent and child nodes*@
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field => 
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
        )
        .ShowCheckbox(true)
        .AutoCheck(false)
    )
    
    {% endhighlight %}
    
## Check or Uncheck Node

Tree node can be checked or unchecked using [checkNode](https://help.syncfusion.com/api/js/ejtreeview#methods:checknode) and [uncheckNode](https://help.syncfusion.com/api/js/ejtreeview#methods:unchecknode) methods while [showCheckbox](https://help.syncfusion.com/api/js/ejtreeview#members:showcheckbox) property is enabled in TreeView. Also you can get or set the checked nodes of TreeView using [checkedNodes](https://help.syncfusion.com/api/js/ejtreeview#members:checkednodes) property, which indicates the checked nodes index collection as array. The [nodeCheck](https://help.syncfusion.com/api/js/ejtreeview#events:nodecheck) and [nodeUncheck](https://help.syncfusion.com/api/js/ejtreeview#events:nodeuncheck) event occurs based on checkbox state.
You can use [isNodeChecked](https://help.syncfusion.com/api/js/ejtreeview#methods:isnodechecked) method to check the particular TreeView node is checked or unchecked. Also you can use [checkAll](https://help.syncfusion.com/api/js/ejtreeview#methods:checkall) method to check all the nodes in TreeView.

    {% highlight javascript %}
    
        //create an instance from an existing TreeView.
        // only after control creation you can get treeObj otherwise it throws exception.
        treeObj = $("#treeView").ejTreeView('instance');
                
        //to check node
        treeObj.checkNode("2");
    
        //to uncheck node
        treeObj.uncheckNode("2");
    
    
    {% endhighlight %}

## Get Checked Nodes

To get checked nodes of TreeView, you can use [getCheckedNodes](http://help.syncfusion.com/js/api/ejtreeview#methods:getcheckednodes) method. It returns the collection of checked tree nodes. Also you can get currently checked nodes indexes in TreeView by using [getCheckedNodesIndex](https://help.syncfusion.com/api/js/ejtreeview#methods:getcheckednodesindex) method.

    {% highlight razor %}
    
    <script type="text/javascript">
        function onClick() {
            //create an instance from an existing TreeView.
            // only after control creation you can get treeObj otherwise it throws exception.
            treeObj = $("#treeView").ejTreeView('instance');
    
            //to get checked nodes
            treeObj.getCheckedNodes();
        }        
    </script>
    
    {% endhighlight %}

