---
title: How To| TreeView | ASP.NET MVC | Syncfusion
description: How To section
platform: ejmvc
control: TreeView
documentation: UG
keywords: TreeView,  Syncfusion, EJ MVC TreeView, UG Document, How To
---

# How To

## Update the modified data from tree to database.

TreeView allows us to get the updated tree data after performing such operation like node editing, drag and drop, add and remove node. Using [getTreeData](http://help.syncfusion.com/js/api/ejtreeview#methods:gettreedata) method you can get the updated tree data.

Refer the following code block to know how to get updated data from TreeView.

In the controller page, create a data list that contains the details about tree nodes and specify the method to store modified data.
    
    
    
    {% highlight c# %}
    
    public partial class TreeViewController : Controller
        {
            List<LoadData> load = new List<LoadData>();
            public ActionResult TreeViewFeatures()
            {
                var storedData = System.Web.HttpContext.Current.Session ["modifiedData"];
                if (storedData == null)
                {
                    load.Add(new LoadData { Id = 1, Parent = 0, Text = "Item 1", Expanded = true });
                    load.Add(new LoadData { Id = 2, Parent = 0, Text = "Item 2" });
                    load.Add(new LoadData { Id = 3, Parent = 0, Text = "Item 3" });
                    load.Add(new LoadData { Id = 4, Parent = 0, Text = "Item 4" });
                    load.Add(new LoadData { Id = 5, Parent = 1, Text = "Item 1.1" });
                    load.Add(new LoadData { Id = 6, Parent = 1, Text = "Item 1.2" });
                    load.Add(new LoadData { Id = 7, Parent = 1, Text = "Item 1.3" });
                    load.Add(new LoadData { Id = 8, Parent = 3, Text = "Item 3.1" });
                    load.Add(new LoadData { Id = 9, Parent = 3, Text = "Item 3.2" });
                    load.Add(new LoadData { Id = 10, Parent = 5, Text = "Item 1.1.1" });
                    ViewBag.datasource = load;
                }
                else
                    ViewBag.datasource = storedData;
                return View();
            }
            public ActionResult StoreData(List<LoadData> data)
            {
                System.Web.HttpContext.Current.Session ["modifiedData"] = data;
                return View("TreeViewFeatures");
            }
        }
        
    {% endhighlight %}
    
    
    
In the view page, add TreeView helper and specify the scripts for sending modified data through AJAX action with that also specify clear cache option.
    
    
    
    {% highlight razor %}
    
    @using TreeView_Doc.Models
    
    <div style="width: 250px">
        @(Html.EJ().TreeView("treeView")
            .TreeViewFields(field =>
                field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
                .Id("Id")
                .ParentId("Parent")
                .Text("Text")
                .Expanded("Expanded")
            )
            .ClientSideEvents(events =>
                events.Create("onCreate")
            )
        )
        @(Html.EJ().Button("move")
            .Text("Move Node")
            .Size(ButtonSize.Normal)
            .ClientSideEvents(events => 
                events.Click("moveNode")
            )
        )
        @(Html.EJ().Button("clear")
            .Text("Clear Cache")
            .Size(ButtonSize.Normal)
            .ClientSideEvents(events => 
                events.Click("clearCache")
            )
        )
    </div>
    <script type="text/javascript">
        var treeObj;
        function onCreate() {
            treeObj = $("#treeView").data('ejTreeView');
        }
        function moveNode() {
            treeObj.moveNode($('#4'), $('#1'), 11);
            var updatedData = treeObj.getTreeData();
            ajaxRequest(updatedData);
        }
        function ajaxRequest(updatedData) {
            $.ajax({
                url: "StoreData",
                data: JSON.stringify({ data: updatedData }),
                type: "POST",
                contentType: "application/json",
                dataType: "JSON"
            });
        }
        function clearCache() {
            treeObj.destroy();
            ajaxRequest();
        }
    </script>
    
    {% endhighlight %}
    
You can also get the updated data source for remote data binding after performing the operation like editing, selecting/unselecting, expanding/collapsing, checking/unchecking and removing node. You cannot get the updated data source when you perform operation like drag and drop, adding node for remote data binding.

The updated data source also contains custom attributes ("ContactTitle", "OrderID", "EmployeeID", "Freight") if you return these from server.

Refer the following code block to know more about how to get updated data with custom attributes from TreeView for remote data binding.

In the view page, add TreeView helper and specify the scripts for getting updated data source.

{% highlight razor %}
<button id="btn1" onclick="getSelectedNodeObject()">GetSelectedNodeObject</button>

@Html.EJ().TreeView("tree1").TreeViewFields(s => s.Datasource(data => data.URL("//js.syncfusion.com/ejServices/Wcf/Northwind.svc/").CrossDomain(true))
        .Query("ej.Query().from('Orders').select('CustomerID,OrderID,EmployeeID,Freight').take(3)").Id("CustomerID").Text("CustomerID")
        .Child(c => c.Datasource(childData => childData.URL("//js.syncfusion.com/ejServices/Wcf/Northwind.svc/").CrossDomain(true))
        .Query("ej.Query().from('Customers').select('CustomerID,ContactTitle,ContactName,Country')").Id("Country").ParentId("CustomerID").Text("ContactName")))

<script>
    function getSelectedNodeObject() {
        var treeObj = $("#tree1").data("ejTreeView");
        var nodeId = treeObj.getSelectedNode().attr("id"); //get selected node id
        if (nodeId != null) {
            var node = treeObj.getTreeData(nodeId); //get the given node object
            if (node[0].OrderID != null)
                alert("The OrderID of node '" + node[0].CustomerID + "' is: '" + node[0].OrderID + "'");
            else
                alert("The ContactTitle of node '" + node[0].ContactName + "' is: '" + node[0].ContactTitle + "'");
        } else
            alert("Select any node");
    }
</script>
{% endhighlight %}
    
## TreeView context menu to process node operations.

TreeView control is availed with the context menu options that open on right-click, over the node. Other than the default menu items available, you can add the new node dynamically in TreeView and also delete the item, enable and disable the item in TreeView. It is achieved by adding the Context Menu option to the TreeView.

**Menu Item**

By default, the context menu options are provided with four items namely: Add New Item, Delete Item, Enable Item and Disable Item. When you want to customize and use your own custom menu items, then you can customize the TreeView with the desired collections.

The following code example illustrates how to configure the context menu elements for the TreeView and in the following example, you have to specify the menu type as ej.MenuType.ContextMenu and in the menuClick function, you can check the cases with add, delete, remove or enable item in TreeView.

And each functionality in the context menu option is done by specific methods. For example, you have added the new item in TreeView by using the addNode() method, delete the item using removeNode() method, disable the item using disableNode() method and enable the item enableNode() method respectively.

The following steps explain how you can enable the **ShowCheckbox** property for TreeView.

In the view page, add TreeView helper and specify context menu.
    
    
    
    {% highlight razor %}
    
    <div style="width: 250px">
        @Html.EJ().TreeView("treeview").Items(items =>
        {
            items.Add().Text("Favorites").Expanded(true).Children(child =>
            {
                child.Add().Text("Desktop");
                child.Add().Text("Downloads");
                child.Add().Text("Recent places");
            });
            items.Add().Text("Libraries").Expanded(true).Children(child =>
            {
                child.Add().Text("Documents").Children(child1 =>
                    {
                        child1.Add().Text("My Documents");
                        child1.Add().Text("Public Documents");
                    });
                child.Add().Text("Pictures").Children(child1 =>
                    {
                        child1.Add().Text("My Pictures");
                        child1.Add().Text("Public Pictures");
                    });
                child.Add().Text("Music").Children(child1 =>
                    {
                        child1.Add().Text("My Music");
                        child1.Add().Text("Public Music");
                    });
                child.Add().Text("Subversion");
            });
            items.Add().Text("Computer").Children(child =>
            {
                child.Add().Text("Folder(C)");
                child.Add().Text("Folder(D)");
                child.Add().Text("Folder(E)");
            });
        })
    </div>
    <div>
        @(Html.EJ().Menu("treeviewMenu")
            .Items(items =>
            {
                items.Add().Text("Add New Item");
                items.Add().Text("Remove Item");
                items.Add().Text("Disable Item");
                items.Add().Text("Enable Item");
            })
            .OpenOnClick(false)
            .MenuType(MenuType.ContextMenu)
            .ShowSubLevelArrows(true)
            .ContextMenuTarget("#treeview")
            .ClientSideEvents(events =>
                events.Click("menuClick")
                .BeforeOpen("beforeOpen")
            )
        )
    </div>
    
      
    <script type="text/javascript">
        //Define the events for menu click in the script section as follows,
        var tabIndex = 1, treeviewObj, selectedNode;
        function beforeOpen(args) {
            var treeviewObj = $("#treeview").data("ejTreeView");
            if (!$(args.target).hasClass("e-text"))
                args.cancel = true;
            else {
                selectedNode = args.target;
                treeviewObj.selectNode(selectedNode);
            }
        }
    
        function menuClick(args) {
            var treeviewObj = $("#treeview").data("ejTreeView");
            if (args.events.text == "Add New Item") {
                treeviewObj.addNode("Item" + tabIndex, selectedNode);
                tabIndex++;
            }
            else if (args.events.text == "Remove Item") {
                treeviewObj.removeNode(selectedNode);
            }
            else if (args.events.text == "Disable Item") {
                treeviewObj.disableNode(selectedNode)
            }
            else if (args.events.text == "Enable Item") {
                treeviewObj.enableNode(selectedNode)
            }
        }
    
    </script>
    
    {% endhighlight %}
    
    
    
The output for the context menu for TreeView control is as follows.

![http://help.syncfusion.com/aspnetmvc/treeview/how-to_images/how-to_img1.png](how-to_images/how-to_img1.jpeg)


## Sorted data using refresh method

TreeView allows you to refresh the entire tree data by using [refresh](http://help.syncfusion.com/js/api/ejtreeview#methods:refresh) method. Refer the below code block to know how to sort entire tree data using refresh method.

In the controller page, create a data list that contains the details about tree nodes.
    
    
    
    {% highlight c# %}
    
        public partial class TreeViewController : Controller
        {
            List<LoadData> load = new List<LoadData>();
            public ActionResult TreeViewFeatures()
            {
                load.Add(new LoadData { Id = 1, Parent = 0, Text = "Item 1", Expanded = true });
                load.Add(new LoadData { Id = 2, Parent = 0, Text = "Item 3" });
                load.Add(new LoadData { Id = 3, Parent = 0, Text = "Item 2" });
                load.Add(new LoadData { Id = 4, Parent = 0, Text = "Item 4" });
                load.Add(new LoadData { Id = 5, Parent = 1, Text = "Item 1.1" });
                load.Add(new LoadData { Id = 6, Parent = 1, Text = "Item 1.2" });
                load.Add(new LoadData { Id = 7, Parent = 1, Text = "Item 1.3" });
                load.Add(new LoadData { Id = 8, Parent = 3, Text = "Item 3.1" });
                load.Add(new LoadData { Id = 9, Parent = 3, Text = "Item 3.2" });
                load.Add(new LoadData { Id = 10, Parent = 5, Text = "Item 1.1.1" });
                ViewBag.datasource = load;
                return View();
            }
        }
        
    {% endhighlight %}
    
    
    
In the view page, add TreeView helper and map the properties defined in to the corresponding fields in data source with that specify the scripts for sorting and refreshing tree data.
    
    
    
    {% highlight razor %}
    
    <div style="width: 250px">
        @(Html.EJ().TreeView("treeView")
            .TreeViewFields(field => 
                field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
                .Id("Id")
                .ParentId("Parent")
                .Text("Text")
                .Expanded("Expanded")
            )
        )
        @(Html.EJ().Button("move")
            .Text("Sort Countries")
            .Size(ButtonSize.Normal)
            .ClientSideEvents(events =>
                events.Click("sortCountries")
            )
        )
    </div>
    <script type="text/javascript">
        function sortCountries() {
            window.tree = $("#treeView").data("ejTreeView");
            TreeNodeData = sortResults(tree.model.fields.dataSource, "Text", true);
            tree.model.fields.dataSource = TreeNodeData;
            tree.refresh();
        }
        //Sorting the tree data based on ascending order
        function sortResults(data, fieldName, ascOrder) {
            return data.sort(function (a, b) {
                if (ascOrder) return (a[fieldName] > b[fieldName]);
                else return (b[fieldName] > a[fieldName]);
            });
        }
    </script>
    
    {% endhighlight %}
    
    
    
## Persist updated data after edit, add and remove node

TreeView allows us to persist the updated data after performing some tree operations like node add and delete. Refer the following code block to know how to persist updated tree data after refresh.

The [nodeAdd](https://help.syncfusion.com/api/js/ejtreeview#events:nodeadd), [nodeCut](https://help.syncfusion.com/api/js/ejtreeview#events:nodecut), [nodeDelete](https://help.syncfusion.com/api/js/ejtreeview#events:nodedelete) and [nodePaste](https://help.syncfusion.com/api/js/ejtreeview#events:nodepaste) events occurs based on Treeview node manipulation. The [beforeAdd](https://help.syncfusion.com/api/js/ejtreeview#events:beforeadd), 
[beforeCut](https://help.syncfusion.com/api/js/ejtreeview#events:beforecut), [beforeDelete](https://help.syncfusion.com/api/js/ejtreeview#events:beforedelete) and [beforePaste](https://help.syncfusion.com/api/js/ejtreeview#events:beforepaste) events are triggered before the TreeView component node manipulation.

In the controller page, create a data list that contains the details about tree nodes and specify the method to store modified data.
    
    
    
    {% highlight c# %}
    
        public partial class TreeViewController : Controller
        {
            List<LoadData> load = new List<LoadData>();
            public ActionResult TreeViewFeatures()
            {
                var storedData = System.Web.HttpContext.Current.Session["modifiedData"];
                if (storedData == null)
                {
                    load.Add(new LoadData { Id = 1, Parent = 0, Text = "Item 1", Expanded = true });
                    load.Add(new LoadData { Id = 2, Parent = 0, Text = "Item 2" });
                    load.Add(new LoadData { Id = 3, Parent = 0, Text = "Item 3" });
                    load.Add(new LoadData { Id = 4, Parent = 0, Text = "Item 4" });
                    load.Add(new LoadData { Id = 5, Parent = 1, Text = "Item 1.1" });
                    load.Add(new LoadData { Id = 6, Parent = 1, Text = "Item 1.2" });
                    load.Add(new LoadData { Id = 7, Parent = 1, Text = "Item 1.3" });
                    load.Add(new LoadData { Id = 8, Parent = 3, Text = "Item 3.1" });
                    load.Add(new LoadData { Id = 9, Parent = 3, Text = "Item 3.2" });
                    load.Add(new LoadData { Id = 10, Parent = 5, Text = "Item 1.1.1" });
                    ViewBag.datasource = load;
                }
                else
                    ViewBag.datasource = storedData;
                return View();
            }
            public ActionResult StoreData(List<LoadData> data)
            {
                System.Web.HttpContext.Current.Session["modifiedData"] = data;
                return View("TreeViewFeatures");
            }
        }
        
    {% endhighlight %}
    
    
    
In the view page, add TreeView helper and specify the scripts for sending modified data through AJAX action.
    
    
    
    {% highlight razor %}
    
    @using TreeView_Doc.Models
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
            .Expanded("Expanded")
        )
        .ClientSideEvents(events => 
            events.Create("onCreate")
            .NodeAdd("updateData")
            .NodeEdit("updateData")
            .NodeDelete("updateData")
        )
    )
    @(Html.EJ().Button("clear")
        .Text("Clear Cache")
        .Size(ButtonSize.Normal)
        .ClientSideEvents(events =>
            events.Click("clearCache")
        )
    )
    @(Html.EJ().Button("add")
        .Text("Add Node")
        .Size(ButtonSize.Normal)
        .ClientSideEvents(events =>
            events.Click("addNode")
        )
    )
    @(Html.EJ().Button("remove")
        .Text("Remove Node")
        .Size(ButtonSize.Normal)
        .ClientSideEvents(events => 
            events.Click("removeNode")
        )
    )
    
    <script type="text/javascript">
        var treeObj;
        function onCreate() {
            treeObj = $("#treeView").data('ejTreeView');
        }
        function updateData() {
            var updatedData = treeObj.getTreeData();
            ajaxRequest(updatedData);
        }
        function addNode() {
            treeObj.addNode({ Id: 11, Text: "NewNode1" });
        }
        function removeNode() {
            treeObj.removeNode();
        }
        function ajaxRequest(updatedData) {
            $.ajax({
                url: "StoreData",
                data: JSON.stringify({ data: updatedData }),
                type: "POST",
                contentType: "application/json",
                dataType: "JSON"
            });
        }
        function clearCache() {
            treeObj.destroy();
            ajaxRequest();
        }
    </script>
    
    {% endhighlight %}
    
    
    
## Filtering nodes in TreeView

You can able to filter TreeView nodes based on node text. Refer the below code blocks to filter tree nodes based on the node text.

In the controller page, create a data list that contains the details about tree nodes.
    
    
    
    {% highlight c# %}
    
        public partial class TreeViewController : Controller
        {
            List<LoadData> load = new List<LoadData>();
            public ActionResult TreeViewFeatures()
            {
                load.Add(new LoadData { Id = 1, Parent = 0, Text = "Item 1", Expanded = true });
                load.Add(new LoadData { Id = 2, Parent = 0, Text = "Item 3" });
                load.Add(new LoadData { Id = 3, Parent = 0, Text = "Item 2" });
                load.Add(new LoadData { Id = 4, Parent = 0, Text = "Item 4" });
                load.Add(new LoadData { Id = 5, Parent = 1, Text = "Item 1.1" });
                load.Add(new LoadData { Id = 6, Parent = 1, Text = "Item 1.2" });
                load.Add(new LoadData { Id = 7, Parent = 1, Text = "Item 1.3" });
                load.Add(new LoadData { Id = 8, Parent = 3, Text = "Item 3.1" });
                load.Add(new LoadData { Id = 9, Parent = 3, Text = "Item 3.2" });
                load.Add(new LoadData { Id = 10, Parent = 5, Text = "Item 1.1.1" });
                ViewBag.datasource = load;
                return View();
            }
        }
        
    {% endhighlight %}
    
    
    
In the view page, add TreeView helper and map the properties defined in to the corresponding fields in data source with that specify the script for filtering tree nodes.
    
    
    
    {% highlight razor %}
    
    <div style="margin: 20px; padding: 20px; height: 2000px;">
        <div class="heading">
            Treeview with Filtering Nodes
        </div>
        <div class="treeviewfilter">
            <!-- TextBox Element -->
            @(Html.EJ().MaskEdit("inputBox")
                .Width("100%")
                .InputMode(InputMode.Text)
                .MaskFormat("")
                .ClientSideEvents(events =>
                    events.Change("searchNodes")
                )
            )
            <!-- TreeView Element -->
            @(Html.EJ().TreeView("treeView")
                .TreeViewFields(field =>
                    field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
                    .Id("Id")
                    .ParentId("Parent")
                    .Text("Text")
                    .Expanded("Expanded")
                )
                .Width("100%")
                .ClientSideEvents(events =>
                    events.Create("onCreate")
                )
            )
        </div>
    </div>
    <script type="text/javascript">
        var treeObj, inputObj, count = 0;
        window._temp = [];
    
        function onCreate(args) {
            // Creating Objects for TreeView & MaskEdit TextBox
            treeObj = $("#treeView").data("ejTreeView");
            inputObj = $("#inputBox").data("ejMaskEdit");
        }
    
        //Function triggers while change the TextBox input value and start new search
        function searchNodes(args) {
            var treeElement = treeObj.element;
            // Getting the Input String
            var searchVal = inputObj.get_StrippedValue() ? inputObj.get_StrippedValue().toLowerCase() : "";
            // If the string length is greater than 0 then Do searching.
            if (searchVal.length > 0) {                
                var matchedNode = [], otherNodes = [];
                // Searching Anchor nodes
                var linkNodes = treeElement.find('ul>li>div>a');
                for (var p = 0; p < linkNodes.length; p++) {
                    if ($(linkNodes[p]).text().toLowerCase().indexOf(searchVal) != -1)
                        matchedNode.push(linkNodes[p]);     //  Stores the Matched nodes
                    else
                        otherNodes.push(linkNodes[p]);      // Stores the unMatched nodes
                }
                // Find the Matched nodes parent Li element and set Display "block"
                var resultNodes = treeElement.find(matchedNode).closest("li").css("display", "block");
                // Find the unMatched nodes parent Li element and set Display "none"
                treeElement.find(otherNodes).closest("li").css("display", "none");
                for (var i = 0; i < resultNodes.length; i++) {
                    var currentNode = $(resultNodes[i]);
                    // Get the Parent Li element of current li element and Set Display "block"
                    var parentNode = currentNode.parents('ul').closest('li').css("display", "block");
                    if (parentNode.length > 0) {
                        // Call expandNode function If a parentNode has children
                        treeObj.expandNode(parentNode);
                        if (treeObj.model.expandedNodes.indexOf($(treeObj._liList).index(parentNode)) == -1)
                            window._temp.push(parentNode);
                    }
                    var childrenUl = currentNode.children('ul');
                    if (childrenUl.length > 0 && childrenUl.children('li:visible').length == 0) {
                        currentNode.children('ul').children('li').css("display", "block");
                        // Call expandNode function If a resultNodes[i] has children
                        treeObj.expandNode(resultNodes[i]);
                        if (treeObj.model.expandedNodes.indexOf($(treeObj._liList).index(resultNodes[i])) == -1)
                            window._temp.push(resultNodes[i]);
                    }
                }
            }
            else {
    
                // window._temp contains Li elements, which is expanded while searching.
                treeElement.find('ul>li').css("display", "block");
                for (var i = 0; i < window._temp.length; i++) {
                    treeObj._collpaseNode(window._temp[i]);
                }
                window._temp = [];
            }
        }
    </script>
    
    <style type="text/css">
        .treeviewfilter {
            width: 200px;
            min-height: 300px;
            max-height: auto;
            border: 1px solid #bbbbbb;
            margin: 0 auto;
        }
    
        .e-mask .e-in-wrap {
            border: none;
            border-bottom: 1px solid #bbbbbb;
        }
    
        .heading {
            font-size: 22px;
            margin: 0 auto;
            width: 300px;
            margin-bottom: 10px;
        }
    </style>
    
    {% endhighlight %}
    
    
    
## AngularJS data binding to update data while add and remove node

TreeView allows us to bind and update tree data in mapped data component while add and removing node using AngularJS binding. Refer the below code block to know how to update data using AngularJS binding.
    
    
    
    {% highlight razor %}
    
    <div class="content-container-fluid" ng-controller="TreeCtrl">
        <div class="row">
            <div class="cols-sample-area">
                <div style="width: 400px; float:left">
                    <button type="button" ng-click="add()">Add</button>
                    <button type="button" ng-click="remove()">Remove</button>
                    <div id="treeView" e-allowediting="true" ej-treeview e-fields-datasource="dataList" e-fields-id="iconId" e-fields-parentid="parentId" e-fields-text="name" e-fields-haschild="hasChild" e-fields-expanded="expanded" e-showcheckbox="true" e-allowediting="true"></div>
                </div>
                <div style="width: 400px; float:left">
                    <table>
                        <tr>
                            <td>
                                <p>direct to $scope.dataList</p>
                                <div ng-repeat="icon in dataList">
                                    <input type="text" ng-model="icon.name" class="sampleText" /><button type="button" ng-click="delete(icon.iconId)">Delete</button><br />
                                </div>
                            </td>
                        </tr>
                    </table>
                </div>
            </div>
        </div>
    </div>
    
    <script>
    
        var phones = [
                { iconId: 1, name: "Fiction Book Lists", hasChild: true, expanded: true },
                { iconId: 2, parentId: 1, name: "To Kill a Mockingbird " },
                { iconId: 3, parentId: 1, name: "Pride and Prejudice " },
                { iconId: 4, parentId: 1, name: "Harry Potter and the Sorcerer's Stone" },
                { iconId: 5, parentId: 1, name: "The Hobbit " },
                { iconId: 6, name: "Mystery Book Lists", hasChild: true, expanded: true },
                { iconId: 7, parentId: 6, name: "And Then There Were None " },
                { iconId: 8, parentId: 6, name: "Angels & Demons" },
                { iconId: 9, parentId: 6, name: "In Cold Blood " },
                { iconId: 10, parentId: 6, name: "The Name of the Rose " },
                { iconId: 11, name: "Horror Novels", hasChild: true },
                { iconId: 12, parentId: 11, name: "The Shining (The Shining, #1) " },
                { iconId: 13, parentId: 11, name: "The Haunting of Hill House " },
                { iconId: 14, parentId: 11, name: "The Silence of the Lambs (Hannibal Lecter, #2) " },
                { iconId: 15, name: "Novel Lists", hasChild: true },
                { iconId: 16, parentId: 15, name: "Shadow Hills (Shadow Hills, #1) " },
                { iconId: 17, parentId: 15, name: "After Forever Ends " },
                { iconId: 18, parentId: 15, name: "Angel Star" },
                { iconId: 19, parentId: 15, name: "Raised by Wolves" },
                { iconId: 20, parentId: 15, name: "Falling From Grace" }];
        var Nodes = ["1", "2"];
        angular.module('treeApp', ['ejangular']).controller('TreeCtrl', function ($scope) {
            $scope.dataList = phones;
    
            $scope.add = function () {
                var treeObj = $("#treeView").data("ejTreeView"), obj;
                //obj = [{ iconId: 21, parentId: 1, name: "Newnode" }];
                obj = "New TextNode";
                treeObj.addNode(obj);    // Two way binding when add node
            };
    
            $scope.remove = function () {
                var treeObj = $("#treeView").data("ejTreeView");
                var id = treeObj.getSelectedNode()[0].id;
                treeObj.removeNode(treeObj.getSelectedNode());  // Two way binding when remove node
            };
    
            // Delete from outside tree
            $scope.delete = function (iconId) {
                for (var i = $scope.dataList.length - 1; i > -1; i--) {
                    if ($scope.dataList[i].iconId === iconId)
                        $scope.dataList.splice(i, 1); // Delete parent node
                }
                for (var i = $scope.dataList.length - 1; i > -1; i--) {
                    if ($scope.dataList[i].parentId === iconId)
                        $scope.dataList.splice(i, 1); // Delete child nodes
                }
            };
    
        });
    
    </script>
    
    {% endhighlight %}
    
    
    
## Set tooltip for TreeView nodes

TreeView allows you to set tooltip option to TreeView nodes using [fields.linkAttribute](http://help.syncfusion.com/js/api/ejtreeview#members:fields-linkattribute) property of TreeView. Refer the below code block to know how to set tooltip for TreeView nodes.

In the model page, add a class and define the properties as shown below.
    
    
    
    {% highlight c# %}
    
    namespace TreeView_Doc.Models
    {
        public class LoadData
        {
            public int Id { get; set; }
            public int Parent { get; set; }
            public string Text { get; set; }
            public bool Expanded { get; set; }
            public object LinkAttribute { get; set; }
        }
        public class LinkAttribute
        {
            public string Title { get; set; }
        }
    }
    
    {% endhighlight %}
    
    
    
In the controller page, create a data list that contains the details about tree nodes.
    
    
    
    {% highlight c# %}
    
        public partial class TreeViewController : Controller
        {
            List<LoadData> load = new List<LoadData>();
            public ActionResult TreeViewFeatures()
            {
                load.Add(new LoadData
                {
                    Id = 1,
                    Parent = 0,
                    Text = "Item 1",
                    Expanded = true,
                    LinkAttribute = new LinkAttribute()
                    {
                        Title = "First Item"
                    }
                });
                load.Add(new LoadData
                {
                    Id = 2,
                    Parent = 0,
                    Text = "Item 2",
                    LinkAttribute = new LinkAttribute()
                    {
                        Title = "Second Item"
                    }
                });
                load.Add(new LoadData
                {
                    Id = 3,
                    Parent = 0,
                    Text = "Item 3"
                });
                load.Add(new LoadData
                {
                    Id = 4,
                    Parent = 0,
                    Text = "Item 4"
                });
                load.Add(new LoadData
                {
                    Id = 5,
                    Parent = 1,
                    Text = "Item 1.1"
                });
                load.Add(new LoadData
                {
                    Id = 6,
                    Parent = 1,
                    Text = "Item 1.2"
                });
                load.Add(new LoadData
                {
                    Id = 7,
                    Parent = 1,
                    Text = "Item 1.3"
                });
                load.Add(new LoadData
                {
                    Id = 8,
                    Parent = 3,
                    Text = "Item 3.1"
                });
                load.Add(new LoadData
                {
                    Id = 9,
                    Parent = 3,
                    Text = "Item 3.2"
                });
                load.Add(new LoadData
                {
                    Id = 10,
                    Parent = 5,
                    Text = "Item 1.1.1"
                });
                ViewBag.datasource = load;
                return View();
            }
        }
        
    {% endhighlight %}
    
    
    
In the view page, add TreeView helper and map the properties defined in to the corresponding fields in data source
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
            .Expanded("Expanded")
            .LinkAttribute("LinkAttribute")
        )
    )
    
    {% endhighlight %}
    
    
    
## Auto hide/show the expand/collapse icon of TreeView

You can able to display expand icon on mouse entering into TreeView and hide while leaving from the TreeView. Refer the below code block to know how to hide/ show the expand/collapse icons automatically based on mouse position.

In the controller page, create a data list that contains the details about tree nodes.
    
    
    
    {% highlight c# %}
    
        public partial class TreeViewController : Controller
        {
            List<LoadData> load = new List<LoadData>();
            public ActionResult TreeViewFeatures()
            {
                load.Add(new LoadData { Id = 1, Parent = 0, Text = "Item 1", Expanded = true });
                load.Add(new LoadData { Id = 2, Parent = 0, Text = "Item 3" });
                load.Add(new LoadData { Id = 3, Parent = 0, Text = "Item 2" });
                load.Add(new LoadData { Id = 4, Parent = 0, Text = "Item 4" });
                load.Add(new LoadData { Id = 5, Parent = 1, Text = "Item 1.1" });
                load.Add(new LoadData { Id = 6, Parent = 1, Text = "Item 1.2" });
                load.Add(new LoadData { Id = 7, Parent = 1, Text = "Item 1.3" });
                load.Add(new LoadData { Id = 8, Parent = 3, Text = "Item 3.1" });
                load.Add(new LoadData { Id = 9, Parent = 3, Text = "Item 3.2" });
                load.Add(new LoadData { Id = 10, Parent = 5, Text = "Item 1.1.1" });
                ViewBag.datasource = load;
                return View();
            }
        }
        
    {% endhighlight %}
    
    
    
In the view page, add TreeView helper and map the properties defined in to the corresponding fields in data source with that specify the scripts to hide and show the icons of tree nodes.
    
    
    
    {% highlight razor %}
    
    <div style="width: 150px">
        <!-- TreeView Element -->
        @(Html.EJ().TreeView("treeView")
            .TreeViewFields(field =>
                field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
                .Id("Id")
                .ParentId("Parent")
                .Text("Text")
                .Expanded("Expanded")
            )
            .ClientSideEvents(events => 
                events.Create("onCreate")
            )
        )
    </div>
    
    <script type="text/javascript">
        function onCreate(args) {
            this.element.find(".e-item > div > .e-plus, .e-minus").css("visibility", "hidden");
            var treeObj = $("#treeView").data("ejTreeView");
            $("#treeView").on("mouseenter", function () {
                treeObj.element.find(".e-item > div > .e-plus, .e-minus").css("visibility", "");
            });
            $("#treeView").on("mouseleave", function () {
                treeObj.element.find(".e-item > div > .e-plus, .e-minus").css("visibility", "hidden");
            });
        }
    </script>
    
    {% endhighlight %}
    
    
    
## Customize the expand/collapse icons of TreeView

You can able to customize the TreeView expand and collapse icon by using “cssClass” property of TreeView. Refer the below code block to know how to customize the expand/collapse icons.

In the view page, add TreeView helper and map the properties defined in to the corresponding fields in data source with that specify the styles for customizing expand/ collapse icon of TreeView.
    
    
    
    {% highlight razor %}
    
    <div style="width: 150px">
        <!-- TreeView Element -->
        @(Html.EJ().TreeView("treeView")
            .TreeViewFields(field =>
                field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
                .Id("Id")
                .ParentId("Parent")
                .Text("Text")
                .Expanded("Expanded")
            )
            .CssClass("customize")
        )
    </div>
    
    <style type="text/css">
        .customize .e-icon {
            width: 16px;
            height: 16px;
            background-repeat: no-repeat;
            background-image: url("http://jsplayground.syncfusion.com/13.3.0.7/themes/web/images/ui-icons/ui-icons-default.png");
        }
    
        .customize .e-icon.e-plus:before, .customize .e-icon.e-minus:before {
            content: "";
        }
        
        .customize .e-icon.e-plus {
            background-position: -80px -46px;
        }
    
        .customize .e-icon.e-minus {
            background-position: -132px -46px;
        }
    </style>
    
    {% endhighlight %}
    
    
    
## In form post, how to get all checked nodes details of TreeView in server end

You have to create a hidden element for storing custom details of checked nodes and add it to the form element. These details will be sent to server at the time of form submit. 

Refer the following code block to know how to get checked nodes details in server end 

In the view page, add TreeView helper and specify the scripts for adding checked node details in form element.
    
    
    
    {% highlight razor %}
    
    <div style="width: 250px">
        <form action="\TreeView\CheckedNodes" method="post" id="myForm">
            @Html.EJ().TreeView("tree").Items(items =>
                    {
                        items.Add().Text("Item 1").Children(child =>
                        {
                            child.Add().Text("Item 1.1").Children(child1 =>
                            {
                                child1.Add().Text("Item 1.1.1");
                            });
                        });
                        items.Add().Text("Item 2").Expanded(true).Children(child =>
                        {
                            child.Add().Text("Item 2.1");
                            child.Add().Text("Item 2.2");
                        });
                        items.Add().Text("Item 3").Children(child =>
                        {
                            child.Add().Text("Item 3.1");
                        });
                    }).ShowCheckbox(true)
            <input type="submit" id="submit" value="GetCheckedNodes" />
    
        </form>
    </div>
    
    <script>
    
        $('#submit').click(function () {
            tree = $("#tree").data("ejTreeView");
            checkedNodes = tree.getCheckedNodes();
            for (i = 0; i < checkedNodes.length ; i++) {
                var checkedNode = checkedNodes[i];
                var nodeData = tree.getNode(checkedNode);
                var parentNode = tree.getParent(checkedNode);
                if (parentNode.length > 0)
                    $('#myForm').append('<input type="hidden" name="checkedNodes" value="' + parentNode[0].id + '/' + nodeData.id + '" />');
                else
                    $('#myForm').append('<input type="hidden" name="checkedNodes" value=" No Parent /' + nodeData.id + '" />');
            }
        });
    
    </script>
    
    {% endhighlight %}
    
    
    
In the controller page, configure following settings to get the checked node details in form submit.
    
    
    
    {% highlight c# %}
    
        public partial class TreeViewController : Controller
        {
            public ActionResult TreeViewFeatures()
            {
                return View();
            }
            // on data all checkedNodes are received
            public ActionResult CheckedNodes(List<string> checkedNodes)
            {
                ViewBag.CheckedNodes = checkedNodes;
                return PartialView();
            }
        }
    
    {% endhighlight %}
    
    
    
Using following partial view page, you can display the custom details of checked nodes.
    
    {% highlight razor %}
    
    <html>
    <body>
        <h3>Checked node ID</h3>
        <ul>
            @*using ViewBag, we can get the checked node details*@
            @if (ViewBag.CheckedNodes != null)
            {
                foreach (var nodes in ViewBag.CheckedNodes)
                {
                    <li>@nodes</li>
                }
            }
        </ul>
    </body>
    </html>
    
    {% endhighlight %}


## Populate data for TreeView using AJAX

TreeView provides AJAX action supports to populate the data for rendering TreeView nodes. Refer the following code blocks to achieve this behavior. 

In the model page, specify the TreeView node properties as shown below.
    
    
    
    {% highlight c# %}
    
        public class TreeViewData
        {
            public int id { get; set; }
            public int parentId { get; set; }
            public string name { get; set; }
            public bool hasChild { get; set; }
            public bool expanded { get; set; }
        }
    
    {% endhighlight %}
    
    
    
In the controller page, create a data list which contains the details about tree nodes and specify AJAX action handling method.
    
    
    
    {% highlight c# %}
    
        public partial class TreeViewController : Controller
        {
            public ActionResult TreeViewFeatures()
            {
                return View();
            }
            List<TreeViewData> m_templateData;
            public List<TreeViewData> TemplateData
            {
                get
                {
                    if (m_templateData == null)
                        InitializeTemplateData();
                    return m_templateData;
                }
            }
            private void InitializeTemplateData()
            {
                m_templateData = new List<TreeViewData>();
                m_templateData.Add(new TreeViewData
                {
                    id = 1,
                    parentId = 0,
                    name = "Local Disk(C:)",
                    hasChild = true
                });
                m_templateData.Add(new TreeViewData
                {
                    id = 2,
                    parentId = 1,
                    name = "Folder 1"
                });
                m_templateData.Add(new TreeViewData
                {
                    id = 3,
                    parentId = 1,
                    name = "Folder 2"
                });
                m_templateData.Add(new TreeViewData
                {
                    id = 4,
                    parentId = 1,
                    name = "Folder 3",
                    hasChild = true
                });
                m_templateData.Add(new TreeViewData
                {
                    id = 20,
                    parentId = 4,
                    name = "File 1"
                });
                m_templateData.Add(new TreeViewData
                {
                    id = 21,
                    parentId = 4,
                    name = "File 2"
                });
                m_templateData.Add(new TreeViewData
                {
                    id = 22,
                    parentId = 4,
                    name = "File 3"
                });
                m_templateData.Add(new TreeViewData
                {
                    id = 5,
                    parentId = 0,
                    name = "Local Disk(D:)",
                    hasChild = true
                });
                m_templateData.Add(new TreeViewData
                {
                    id = 6,
                    parentId = 5,
                    name = "Folder 4",
                    hasChild = true
                });
                m_templateData.Add(new TreeViewData
                {
                    id = 7,
                    parentId = 6,
                    name = "File 4"
                });
                m_templateData.Add(new TreeViewData
                {
                    id = 8,
                    parentId = 6,
                    name = "File 5"
                });
            }
            public ActionResult GetAllData()
            {
                return Json(TemplateData, JsonRequestBehavior.AllowGet);
            }
        }
    
    {% endhighlight %}
    
    
    
In the view page, add TreeView helper and map the properties defined to the corresponding fields in data source.
    
    
    
    {% highlight razor %}
    
    @using TreeView_Doc.Models
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource(data =>
                data.URL(@Url.Content("GetAllData"))            
            )
            .Id("id")
            .ParentId("parentId")
            .Text("name")
            .HasChild("hasChild")
            .Expanded("expanded")
        )
    )
    
    {% endhighlight %}
    
    
    
## Populate data for TreeView using XML data source

TreeView provides XML data binding support to populate the data for rendering TreeView nodes, so that values can be mapped to the TreeView fields from an existing XML data source as below.
    
    {% tabs %}
    
    {% highlight razor %}
    
    @* In the View page, add TreeView helper and map the properties defined to the corresponding fields in data source.*@
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<FileList>)ViewBag.datasource)
            .Id("Name")
            .ParentId("Parent")
            .Text("Name")
        )
    )
    
    {% endhighlight %}
    
    {% highlight c# %}
    
        //In controller part, need to convert XML data into List of Objects for specifying the list data in TreeView DataSource.
        public partial class TreeViewController : Controller
        {
            public ActionResult TreeViewFeatures()
            {
                XElement element = XElement.Load(Server.MapPath("~/App_Data/XMLFile1.xml"));
                List<FileList> fileList = ToFileList(element);
                ViewBag.datasource = fileList;
                return View();
            }
            //Convert XML element to List of Objects
            private List<FileList> ToFileList(XElement element)
            {
                if (element != null && element.HasElements)
                {
                    List<FileList> employees = new List<FileList>();
                    AddChildElements(element, employees);
                    return employees;
                }
                return null;
            }
            private FileList ToFileItem(XElement element, string parentId)
            {
                return new FileList()
                {
                    Name = element.Attribute("Text").Value,
                    Parent = parentId
                };
            }
            private void AddChildElements(XElement element, List<FileList> employees)
            {
                foreach (var child in element.Elements("RootItem"))
                {
                    var employee = ToFileItem(child, element.Attribute("Text").Value);
                    employees.Add(employee);
                    AddChildElements(child, employees);
                }
                foreach (var child in element.Elements("Item"))
                {
                    var employee = ToFileItem(child, element.Attribute("Text").Value);
                    employees.Add(employee);
                }
            }
        }
    
    {% endhighlight %}
    
    
    {% highlight xml %}
    
    <?xml version="1.0" encoding="utf-8" ?>
    
    <items Text="0">
    
    <RootItem Text="Favorites" Url="#">
    
        <Item Text="Desktop" Url="#"></Item>
    
        <Item Text="Downloads" Url="#"></Item>
    
        <Item Text="Recent places" Url="#"></Item>
    
    </RootItem>
    
    
    
    <RootItem Text="Libraries" Url="#">
    
        <RootItem Text="Documents" Url="#">
    
        <Item Text="My Documents" Url="#"></Item>
    
        <Item Text="Public Documents" Url="#"></Item>
    
        </RootItem>
    
        <RootItem Text="Pictures" Url="#">
    
        <Item Text="My Pictures" Url="#"></Item>
    
        <Item Text="Public Pictures" Url="#"></Item>
    
        </RootItem>
    
        <RootItem Text="Music" Url="#">
    
        <Item Text="My Music" Url="#"></Item>
    
        <Item Text="Public Music" Url="#"></Item>
    
        </RootItem>
    
    </RootItem>
    
    <RootItem Text="Computer" Expanded="True" Url="#">
    
        <Item Text="Folder(C)" Url="#"></Item>
    
        <Item Text="Folder(D)" Url="#"></Item>
    
        <Item Text="Folder(F)" Url="#"></Item>
    
    </RootItem>
    
    </items>
    
    {% endhighlight %}
    
    {% endtabs %}

