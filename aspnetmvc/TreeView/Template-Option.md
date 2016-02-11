---
title: Template Option  | TreeView | ASP.NET MVC | Syncfusion
description: Template Option
platform: ejmvc
control: TreeView
documentation: UG
keywords: TreeView,  Syncfusion, EJ MVC TreeView, UG Document, Template Option
---

# Template Option

Tree nodes can be customized by using **Template** property. Treeview template option requires addition JS library called **JsRender**, which helps to create the structured way of tree nodes with simple codes and increased performance. To know more about JsRender - [http://www.jsviews.com/](http://www.jsviews.com/#) .  

In the controller page, create a data list that contains the details about tree nodes.
    
    
    
    {% highlight c# %}
    
        public partial class TreeViewController : Controller
        {
            List<LoadData> treeData = new List<LoadData>();
            public ActionResult TreeViewFeatures()
            {
                treeData.Add(new LoadData { 
                    Id = 1,
                    Name = "UK",
                    Cls = "uk-style",
                    HasChild = true,
                    Expanded = true
                });
                treeData.Add(new LoadData { 
                    Id = 2,
                    PId = 1,
                    ImgId = "1",
                    Name = "Steven John",
                    City = "London",
                    Phone = "555-5665-2323"
                });
                treeData.Add(new LoadData { 
                    Id = 3,
                    Name = "USA",
                    Cls = "usa-style",
                    HasChild = true,
                    Expanded = true
                });
                treeData.Add(new LoadData { 
                    Id = 5,
                    PId = 3,
                    ImgId = "3",
                    Name = "Andrew",
                    City = "Capital way", 
                    Phone = "934-8374-2455"
                });
                treeData.Add(new LoadData {
                    Id = 4,
                    PId = 3,
                    ImgId = "2",
                    Name = "Angelica",
                    City = "Dayton",
                    Phone = "988-4243-0806"
                });
                ViewBag.datasource = treeData;
                return View();
            }
        }
        
    {% endhighlight %}
    
    
    
In the view page, specify template format and add TreeView helper.
    
    
    
    {% highlight razor %}
    
    <script id="treeTemplate" type="text/x-jsrender">
        {{if HasChild}}
        <div class={{>Cls}}>{{>Name}}</div>
        {{else}}
        <div class="cont-list">
            <img class="con-img" src="http://mvc.syncfusion.com/demos/web/images/treeview/template-image-{{>ImgId}}.png" />
            <div class="cont-del"></div>
            <b>{{>Name}}</b><br />
            <span>{{>City}}</span>
            <br />
            <span>{{>Phone}}</span>
        </div>
        <div class="treeFooter"></div>
        {{/if}}
    
    </script>
    
    <div style="width: 250px">
        @(Html.EJ().TreeView("treeview")
            .TreeViewFields(field =>
                field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
                .Id("Id")
                .ParentId("PId")
                .Text("Name")
                .HasChild("HasChild")
                .Expanded("Expanded")
            )
            .Template("#treeTemplate")
            .ClientSideEvents(events => 
                events.Create("oncreate")
            )
        )
    </div>
    <style class="cssStyles">
        .e-treeview .e-node-hover, .e-treeview .e-active {
            background: transparent;
            border-color: transparent;
        }
    
        .e-treeview .e-node-hover {
            opacity: 0.8;
        }
    
        .con-img {
            float: left;
        }
    
        .cont-list {
            background: none repeat scroll 0 0 white;
            border: 1px solid #BBBCBB;
            height: 85px;
            width: 200px;
            color: #5c5c5c;
            line-height: 17px;
        }
    
        .cont-details {
            margin-top: 12px;
            font-size: 13px;
        }
    
        .uk-style {
            background-color: #74A247 !important;
            color: #FFFFFF !important;
        }
    
        .usa-style {
            background-color: #12A99A !important;
            color: #FFFFFF !important;
        }
    
        .cont-del {
            background-image: url("http://mvc.syncfusion.com/demos/web/images/treeview/remove-icon.png");
            background-position: -6px -10px;
            background-repeat: no-repeat;
            float: right;
            height: 16px;
            width: 16px;
            cursor: pointer;
        }
    
        .cont-list .treeFooter {
            height: 5px;
            width: 100%;
            background-color: gray;
            margin-top: 17px;
        }
    </style>
    <script>
        function oncreate(args) {
            var treeObj = $("#treeview").data("ejTreeView");
            $("#treeview").find(".cont-del").bind("click", function (e) {
                e.preventDefault();
                treeObj.removeNode($(e.target).parents("li").first());
            });
        }
    </script>
    
    {% endhighlight %}
    
    
    
**Custom action in nodes**

You can able to perform custom action in TreeView template node. You can able to perform node delete operation while clicking delete icon by using [removeNode](http://help.syncfusion.com/js/api/ejtreeview#methods:removenode) method TreeView as shown in below code example.
    
    
    
    {% highlight javascript %}
    
    
        function oncreate(args) {
            var treeObj = $("#treeview").data("ejTreeView");
            $("#treeview").find(".cont-del").bind("click", function (e) {
                e.preventDefault();
                treeObj.removeNode($(e.target).parents("li").first());
            });
        }
    
    
    {% endhighlight %}
    
   