---
title: Populate Data | TreeView | ASP.NET MVC | Syncfusion
description: Populate Data
platform: ejmvc
control: TreeView
documentation: UG
keywords: TreeView,  Syncfusion, EJ MVC TreeView, UG Document, Populate Data
---


# Populate Data

TreeView can be populated with local or remote data source using a property [DataSource](http://help.syncfusion.com/cr/cref_files/aspnetmvc/ejmvc/Syncfusion.EJ~Syncfusion.JavaScript.TreeViewFieldsBuilder~Datasource.html), which is the member of “**TreeViewFields**” property.

In TreeView, you should use “**TreeViewFields**” property to go with data source. It specifies the mapping fields for the data source to receive the data, query to process the data and field mappers to map the data members.

## Fields

Below table list outs the field members with description.
  
<table>
<tr>
<td>
    {{'**Properties**'| markdownify }}
</td>
<td>
    {{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
DataSource
</td>
<td>
The data source contains the list of data for generating the TreeView list. Also contains properties to load data from remote data source.
</td>
</tr>
<tr>
<td>
Query
</td>
<td>
It specifies the query to retrieve the data from the online server.
</td>
</tr>
<tr>
<td>
TableName
</td>
<td>
It specifies the name of the table from which data to be processed from given data source.
</td>
</tr>
<tr>
<td>
Id
</td>
<td>
It specifies the ID of the node.
</td>
</tr>
<tr>
<td>
ParentId
</td>
<td>
It specifies the parent id of the node
</td>
</tr>
<tr>
<td>
Text
</td>
<td>
It specifies the text content of the node.
</td>
</tr>
<tr>
<td>
HasChild
</td>
<td>
It specifies the node has child (which is the nested or inner level of nodes). Also it’s used in load on demand of tree data.
</td>
</tr>
<tr>
<td>
Expanded
</td>
<td>
It specifies the tree node to be in expanded state
</td>
</tr>
<tr>
<td>
Selected
</td>
<td>
It specifies the select node at initialize. [note: only one node get selected]
</td>
</tr>
<tr>
<td>
IsChecked 
</td>
<td>
It specifies the node to be in checked state, if tree node represented with checkboxes. 
</td>
</tr>
<tr>
<td>
ImageUrl
</td>
<td>
It defines the image location.
</td>
</tr>
<tr>
<td>
ImageAttribute
</td>
<td>
It defines the image attributes such as height, width, styles, etc.
</td>
</tr>
<tr>
<td>
SpriteCssClass
</td>
<td>
It defines the sprite CSS for the image tag.
</td>
</tr>
<tr>
<td>
HtmlAttribute
</td>
<td>
It defines the HTML attributes such as class and styles for a node (li tag).
</td>
</tr>
<tr>
<td>
LinkAttribute
</td>
<td>
It defines the HTML attributes such as class and styles for a link tag, which is child of node.
</td>
</tr>
<tr>
<td>
Child
</td>
<td>
It used to specify the properties of child nodes in TreeView
</td>
</tr>
</table>

Mapping all fields with data source

In the model page, specify the TreeView node properties as shown below.
    
        
    {% highlight c# %}
    
        public class LoadData
        {
            public int Id { get; set; }
            public int Parent { get; set; }
            public string Text { get; set; }
            public string SpriteImage { get; set; }
            public string ImageURL { get; set; }
            public bool HasChild { get; set; }
            public bool Expanded { get; set; }
            public bool Selected { get; set; }
            public bool NodeChecked { get; set; }
            public object NodeProperty { get; set; }
            public object LinkProperty { get; set; }
            public object ImageProperty { get; set; }
        }
        
    {% endhighlight %}
    
    
    
In the controller page, create a data list which contains the details about tree nodes.
    
    
    
    {% highlight c# %}
    
        public partial class TreeViewController : Controller
        {
            List<LoadData> treeData = new List<LoadData>();
            public ActionResult TreeViewFeatures()
            {
                treeData.Add(new LoadData
                {
                    Id = 1,
                    Parent = 0,
                    Text = "Item 1",
                    Expanded = true,
                    NodeProperty = new Dictionary<string, string>() {
                    { "class", "textblue" },
                    { "value", "Item 1" }
                    }
                });
                treeData.Add(new LoadData
                {
                    Id = 2,
                    Parent = 0,
                    Text = "Item 2",
                    LinkProperty = new Dictionary<string, string>() {
                    { "class", "textunderline" },
                    { "href", "http://www.syncfusion.com" },
                    { "target", "_blank"}
                    }
                });
                treeData.Add(new LoadData
                {
                    Id = 3,
                    Parent = 0,
                    Text = "Item 3",
                    Selected = true,
                    SpriteImage = "mailicon sprite-calendar"
                });
                treeData.Add(new LoadData
                {
                    Id = 4,
                    Parent = 0,
                    Text = "Item 4",
                    NodeChecked = true,
                    ImageProperty = new Dictionary<string, string>() {
                    { "width", "20px" },
                    { "height", "20px" }
                    },
                    ImageURL = "http://cdn.syncfusion.com/13.3.0.7/js/web/flat-azure/images/ajax-loader.gif"
                });
                treeData.Add(new LoadData
                {
                    Id = 5,
                    Parent = 1,
                    Text = "Item 1.1"
                });
                treeData.Add(new LoadData
                {
                    Id = 6,
                    Parent = 1,
                    Text = "Item 1.2"
                });
                treeData.Add(new LoadData
                {
                    Id = 7,
                    Parent = 1,
                    Text = "Item 1.3"
                });
                treeData.Add(new LoadData
                {
                    Id = 8,
                    Parent = 3,
                    Text = "Item 3.1"
                });
                treeData.Add(new LoadData
                {
                    Id = 9,
                    Parent = 3,
                    Text = "Item 3.2"
                });
                treeData.Add(new LoadData
                {
                    Id = 10,
                    Parent = 5,
                    Text = "Item 1.1.1"
                });
                ViewBag.datasource = treeData;
                return View();
            }
        }
        
    {% endhighlight %}
    
    
    
In the view page, add TreeView helper and map the properties defined to the corresponding fields in data source.
    
    
    
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
                .IsChecked("NodeChecked")
                .Selected("Selected")
                .SpriteCssClass("SpriteImage")
                .ImageUrl("ImageURL")
                .LinkAttribute("LinkProperty")
                .HtmlAttribute("NodeProperty")
                .ImageAttribute("ImageProperty")
            )
            .ShowCheckbox(true)
        )
    </div>
    
    {% endhighlight %}
    
    
    
N>**Note: If you want to display nodes in root level, exclude parent attribute or specify “0” in corresponding value.**

## Local data

TreeView can be rendered from a self-referential data by providing the two required fields “**id”**and “**parent**”. 

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
    
    
    
Above data can be directly assigned to [DataSource](http://help.syncfusion.com/cr/cref_files/aspnetmvc/ejmvc/Syncfusion.EJ~Syncfusion.JavaScript.TreeViewFieldsBuilder~Datasource.html) property and mapping data fields with respect to the mapper field in order to form TreeView.
    
    
    
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
    
    
    
## Remote Data

When using remote data binding, the adaptor of [ej.DataManager](http://helpjs.syncfusion.com/js/api/ejdatamanager#) plays vital role in processing queries to make them suitable to sends along with data request and also process the response data from the server.

The following steps explain how you can bind remote data to TreeView control.

    1. In the View page, add TreeView helper to configure TreeView.

    2. In the DataSource field assign remote data source. Here dataManager gets the remote web service and filters the data using Query. The select property of ejQuery is used to retrieve the specified columns from the data source.

    3. Assign dataSource and query property values to bind the remote data. Map the corresponding fields in TreeView control 

### OData

**OData** is a standardized protocol for creating and consuming data. You can bind [oData service](http://www.odata.org/#) data to TreeView in two ways using [DataSource](http://help.syncfusion.com/cr/cref_files/aspnetmvc/ejmvc/Syncfusion.EJ~Syncfusion.JavaScript.TreeViewFieldsBuilder~Datasource.html#) API of “TreeView” control.
    
    1. Using **Datasource(DataSource)** API
    
   Create an object for [DataSource](http://help.syncfusion.com/cr/cref_files/aspnetmvc/ejmvc/Syncfusion.EJ~Syncfusion.JavaScript.DataSource_members.html#) class using OData service URL and then assign it to [DataSource](http://help.syncfusion.com/cr/cref_files/aspnetmvc/ejmvc/Syncfusion.EJ~Syncfusion.JavaScript.TreeViewFieldsBuilder~Datasource.html#) API of “TreeView”. 
    
    
    
    {% highlight razor %}
    
    @{
        DataSource treeData = new DataSource();
        treeData.URL = "http://mvc.syncfusion.com/Services/Northwnd.svc/";
    }
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource(treeData)
            .Query("ej.Query().from('Categories').select('CategoryID,CategoryName').take(3)")
            .Id("CategoryID")
            .Text("CategoryName")
            .Child(childField =>
                childField.Datasource(treeData)
                .TableName("Products")
                .Id("ProductID")
                .ParentId("CategoryID")
                .Text("ProductName")
            )
        )
    )
    
    {% endhighlight %}
    
    
    
    2. Using **Datasource(Action&lt;DataSourceBuilder&gt;)** API
    
   Here directly, you can specify the OData service URL using Action<[DataSourceBuilder](http://help.syncfusion.com/cr/cref_files/aspnetmvc/ejmvc/Syncfusion.EJ~Syncfusion.JavaScript.DataSourceBuilder_members.html#)> 
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource(data =>
                data.URL("http://mvc.syncfusion.com/Services/Northwnd.svc/")
            )
            .Query("ej.Query().from('Categories').select('CategoryID,CategoryName').take(3)")
            .Id("CategoryID")
            .Text("CategoryName")
            .Child(childField =>
                childField.Datasource(data =>
                    data.URL("http://mvc.syncfusion.com/Services/Northwnd.svc/")
                )
                .TableName("Products")
                .Id("ProductID")
                .ParentId("CategoryID")
                .Text("ProductName")
            )
        )
    )
    
    {% endhighlight %}
    
    
    
In above methods, you may also specify the **adaptor** as [ODataAdaptor](http://helpjs.syncfusion.com/js/datamanager/data-adaptors#odata-adaptor) and it is optional to specify.

You can provide adaptor value either as string value (“ODataAdaptor”) or Enum type (AdaptorType.ODataAdaptor)
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource(data =>
                data.URL("http://mvc.syncfusion.com/Services/Northwnd.svc/")
                .Adaptor(AdaptorType.ODataAdaptor)
            )
            .Query("ej.Query().from('Categories').select('CategoryID,CategoryName').take(3)")
            .Id("CategoryID")
            .Text("CategoryName")
            .Child(childField =>
                childField.Datasource(data =>
                    data.URL("http://mvc.syncfusion.com/Services/Northwnd.svc/")
                    .Adaptor(AdaptorType.ODataAdaptor)
                )
                .TableName("Products")
                .Id("ProductID")
                .ParentId("CategoryID")
                .Text("ProductName")
            )
        )
    )
    
    {% endhighlight %}
    
    
    
N>**Note: You can use above code until OData service version 3. For OData Service version 4 End Point, we have created a separate adaptor [ej.ODataV4Adaptor](http://helpjs.syncfusion.com/js/datamanager/data-binding#odata-v4) for databinding.**
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource(data =>
                data.URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Categories")
                .Adaptor(AdaptorType.ODataV4Adaptor)
            )
            .Query("ej.Query().from('Categories').select('CategoryID,CategoryName').take(3)")
            .Id("CategoryID")
            .Text("CategoryName")
            .Child(childField =>
                childField.Datasource(data =>
                    data.URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Products")
                    .Adaptor(AdaptorType.ODataV4Adaptor)
                )
                .TableName("Products")
                .Id("ProductID")
                .ParentId("CategoryID")
                .Text("ProductName")
            )
        )
    )
    
    {% endhighlight %}
    
    
    
### WebApi

Using [ej.WebApiAdaptor](http://helpjs.syncfusion.com/js/datamanager/data-adaptors#webapi-adaptor), you can bind WebApi service data to TreeView as shown in below code example.
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource(data =>
                data.URL("http://mvc.syncfusion.com/OdataServices/treeView/TreeViewData/GetAllData")
                .Adaptor(AdaptorType.WebApiAdaptor)
                .CrossDomain(true)
            )
            .Id("id")
            .Text("name")
            .ParentId("pid")
        )
    )
    
    {% endhighlight %}
    
    
    
### Other Restful web services

The Custom Adaptor concept of [ej.DataManager](http://helpjs.syncfusion.com/js/api/ejdatamanager#) allow you to customize or generate your own adaptor which is used to process query and result data. 

[http://helpjs.syncfusion.com/js/datamanager/data-adaptors#custom-adaptor](http://helpjs.syncfusion.com/js/datamanager/data-adaptors#custom-adaptor)

When using remote data binding, the adaptor of [ej.DataManager](http://helpjs.syncfusion.com/js/api/ejdatamanager#) plays vital role in processing queries to make them suitable to sends along with data request and also process the response data from the server.

In the controller page, create a data list that contains the details about tree nodes.
    
    
    
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
    
    
    
In the view page, add TreeView helper and specify the custom Adaptor as shown below.
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("tree")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
        )
        .ClientSideEvents(events =>
            events.Create("onCreate")
        )
    )
    
    <script type="text/javascript">
        function onCreate() {
            var treeObj = $("#tree").ejTreeView("instance");
            var treeData = treeObj.model.fields.dataSource;
            var customAdaptor = new ej.Adaptor().extend({
                insert: function (dm, data) {
                    return dm.dataSource.json.push(data);
                },
                processQuery: ej.JsonAdaptor.prototype.processQuery
            });
            var dataManager = new ej.DataManager(treeData);
            dataManager.adaptor = new customAdaptor();
            dataManager.insert({ Id: 7, Text: "CustomData", Parent: 0 });
            treeObj.option("fields", { dataSource: dataManager });
        }
    </script>
    
    {% endhighlight %}
    
    
    
## Load on demand

Load on demand is a technique (Lazy load) that is used to reduce the bandwidth size of consuming huge data. You can load data on demand in TreeView by using “**LoadOnDemand**” property when you’re going to use huge data. Refer below code example to load data on demand from local data source.

In the controller page, create a data list that contains the details about tree nodes.
    
    
    
    {% highlight c# %}
    
        public partial class TreeViewController : Controller
        {
            List<LoadData> treeData = new List<LoadData>();
            public ActionResult TreeViewFeatures()
            {
                treeData.Add(new LoadData
                {
                    Id = 1,
                    Parent = 0,
                    Text = "Item 1",
                    HasChild= true
                });
                treeData.Add(new LoadData
                {
                    Id = 2,
                    Parent = 0,
                    Text = "Item 2"                
                });
                treeData.Add(new LoadData
                {
                    Id = 3,
                    Parent = 0,
                    Text = "Item 3",
                    HasChild = true
                });
                treeData.Add(new LoadData
                {
                    Id = 4,
                    Parent = 0,
                    Text = "Item 4"                
                });
                treeData.Add(new LoadData
                {
                    Id = 5,
                    Parent = 1,
                    Text = "Item 1.1",
                    HasChild = true
                });
                treeData.Add(new LoadData
                {
                    Id = 6,
                    Parent = 1,
                    Text = "Item 1.2"
                });
                treeData.Add(new LoadData
                {
                    Id = 7,
                    Parent = 1,
                    Text = "Item 1.3"
                });
                treeData.Add(new LoadData
                {
                    Id = 8,
                    Parent = 3,
                    Text = "Item 3.1"
                });
                treeData.Add(new LoadData
                {
                    Id = 9,
                    Parent = 3,
                    Text = "Item 3.2"
                });
                treeData.Add(new LoadData
                {
                    Id = 10,
                    Parent = 5,
                    Text = "Item 1.1.1"
                });
                ViewBag.datasource = treeData;
                return View();
            }
        }
        
    {% endhighlight %}
    
    
    
In the view page, add TreeView helper and map the properties defined in to the corresponding fields in “Datasource” with that enable load on demand option.
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
            .HasChild("HasChild")
        )
        .LoadOnDemand(true)
    )
    
    {% endhighlight %}
    
    
    
Refer below code example to load data on demand from remote data source.
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeView")
        .TreeViewFields(field =>
            field.Datasource(data =>
                data.URL("http://mvc.syncfusion.com/OdataServices/treeView/TreeViewData/GetTreeData")
            )
            .Id("id")
            .Text("name")
            .ParentId("pid")
        )
        .LoadOnDemand(true)
    )
    
    {% endhighlight %}
    
    
    