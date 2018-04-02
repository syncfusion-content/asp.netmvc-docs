---
layout: post
title: Data Binding | TreeGrid | ASP.NET MVC | Syncfusion
description: data binding
platform: ejmvc
control: TreeGrid
documentation: ug
---

# Data Binding

Data Binding is the process that establishes a connection between the application and different kinds of data sources such as business objects.

## Local Data Binding

In Local Data Binding, datasource for rendering the TreeGrid control is retrieved from the same application locally.

Two types of Data Binding are possible with TreeGrid control, 

* Hierarchical Datasource Binding
* Self-Referential Data Binding (Flat Data)

### Hierarchical Datasource Binding

The `ChildMapping` property is used to map the child records in hierarchy data source.

The following code example shows you how to bind the Hierarchical local data into the TreeGrid control.

{% tabs %}

{% highlight C# %}

public class TreeGridController : Controller
    {
        public ActionResult Index()
        {
            ViewBag.datasource = this.GetData();
            return View();
        }
        private List<BusinessObject> GetData()
        {
            List<BusinessObject> dataCollection = new List<BusinessObject>();

            BusinessObject Record1 = new BusinessObject()
            {
                TaskId = 1,
                TaskName = "Planning",
                StartDate = "02/03/2017",
                Duration = 5,
                Children = new List<BusinessObject>(),
            };

            BusinessObject Child1 = new BusinessObject()
            {
                TaskId = 2,
                TaskName = "Plan timeline",
                StartDate = "02/03/2017",
                Duration = 5
            };

            BusinessObject Child2 = new BusinessObject()
            {
                TaskId = 3,
                TaskName = "Plan budget",
                StartDate = "02/03/2017",
                Duration = 5
            };

            BusinessObject Child3 = new BusinessObject()
            {
                TaskId = 4,
                TaskName = "Allocate resources",
                StartDate = "02/03/2017",
                Duration = 5
            };

            BusinessObject Child4 = new BusinessObject()
            {
                TaskId = 5,
                TaskName = "Planning complete",
                StartDate = "02/07/2017",
                Duration = 0
            };

            Record1.Children.Add(Child1);
            Record1.Children.Add(Child2);
            Record1.Children.Add(Child3);
            Record1.Children.Add(Child4);

            BusinessObject Record2 = new BusinessObject()
            {
                TaskId = 6,
                TaskName = "Design",
                StartDate = "02/10/2017",
                Duration = 3,
                Children = new List<BusinessObject>(),
            };

            BusinessObject Child5 = new BusinessObject()
            {
                TaskId = 7,
                TaskName = "Software Specification",
                StartDate = "02/10/2017",
                Duration = 3
            };

            BusinessObject Child6 = new BusinessObject()
            {
                TaskId = 8,
                TaskName = "Develop prototype",
                StartDate = "02/10/2017",
                Duration = 3
            };

            BusinessObject Child7 = new BusinessObject()
            {
                TaskId = 9,
                TaskName = "Get approval from customer",
                StartDate = "02/13/2017",
                Duration = 2
            };

            BusinessObject Child8 = new BusinessObject()
            {
                TaskId = 10,
                TaskName = "Design complete",
                StartDate = "02/14/2017",
                Duration = 0
            };

            Record2.Children.Add(Child5);
            Record2.Children.Add(Child6);
            Record2.Children.Add(Child7);
            Record2.Children.Add(Child8);
            dataCollection.Add(Record1);
            dataCollection.Add(Record2);
            return dataCollection;
        }
        public class BusinessObject
        {
            public int TaskId { get; set; }
            public string TaskName { get; set; }
            public string StartDate { get; set; }
            public int Duration { get; set; }
            public List<BusinessObject> Children { get; set; }
        }
    }

{% endhighlight  %}

{% highlight CSHTML %}

@using Syncfusion.JavaScript
@using Syncfusion.MVC.EJ
@using Syncfusion.JavaScript.Models

<!DOCTYPE html>
<html>
<head>
         @*Add script reference and style reference here*@
</head>
<body>
@(Html.EJ().TreeGrid("TreeGridContainer")
    .ChildMapping("Children")            
    .Columns(co =>
    {
        co.Field("TaskId").HeaderText("Task Id").EditType(TreeGridEditingType.Numeric).Add();
        co.Field("TaskName").HeaderText("Task Name").EditType(TreeGridEditingType.String).Add();
        co.Field("StartDate").HeaderText("Start Date").EditType(TreeGridEditingType.Datepicker).Add();
        co.Field("Duration").HeaderText("Duration").EditType(TreeGridEditingType.Numeric).Add();
    })
    .Datasource(ViewBag.datasource)
    )
    @(Html.EJ().ScriptManager())
</body>
</html>

{% endhighlight %}
{% endtabs %}  


The output of the above steps is as follows:

![](Data-Binding_images/Data-Binding_img1.png)

[Click](https://mvc.syncfusion.com/demos/web/treegrid/treegridlocalbinding) here to view the online demo sample for Hierarchical Data Binding.

### Self-Referential Data Binding (Flat Data)

TreeGrid is rendered from Self-Referential data structures by providing two fields, **ID** field and **Parent ID** field.

* **ID Field**: This field contains unique values used to identify nodes. Its name is assigned to the `IdMapping` property.
* **Parent ID Field**: This field contains values that indicate parent nodes. Its name is assigned to the `ParentIdMapping` property.

{% tabs %}

{% highlight C# %}

 public class TreeGridController : Controller
    {
        public ActionResult Index()
        {
            ViewBag.datasource = this.GetSelfDataSource();
            return View();
        }
        
        private List<BusinessObject> GetSelfDataSource()
        {
            List<BusinessObject> BusinessObjectCollection = new List<BusinessObject>();
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 1,
                TaskName = "Parent Task 1",
                StartDate = "10/23/2017",
                Duration = 10,               
                ParentId = null
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 2,
                TaskName = "Child task 1",
                StartDate = "10/23/2017",
                Duration = 4,               
                ParentId = 1
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 3,
                TaskName = "Child Task 2",
                StartDate = "10/24/2017",
                Duration = 5,               
                ParentId = 1
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 4,
                TaskName = "Child task 3",
                StartDate = "10/25/2017",
                Duration = 6,                
                ParentId = 1
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 5,
                TaskName = "Parent Task 2",
                StartDate = "10/23/2017",
                Duration = 10,                
                ParentId = null
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 6,
                TaskName = "Child task 1",
                StartDate = "10/23/2017",
                Duration = 4,               
                ParentId = 5
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 7,
                TaskName = "Child Task 2",
                StartDate = "10/24/2017",
                Duration = 5,              
                ParentId = 5
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 8,
                TaskName = "Child task 3",
                StartDate = "10/25/2017",
                Duration = 6,             
                ParentId = 5
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 9,
                TaskName = "Child task 4",
                StartDate = "10/25/2017",
                Duration = 6,          
                ParentId = 5
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 10,
                TaskName = "Parent Task 3",
                StartDate = "10/23/2017",
                Duration = 10,              
                ParentId = null
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 11,
                TaskName = "Child task 1",
                StartDate = "10/23/2017",
                Duration = 4,
             
                ParentId = 10
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 12,
                TaskName = "Child Task 2",
                StartDate = "10/24/2017",
                Duration = 5,
               
                ParentId = 10
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 13,
                TaskName = "Child task 3",
                StartDate = "10/25/2017",
                Duration = 6,
                
                ParentId = 10
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 14,
                TaskName = "Child task 4",
                StartDate = "10/25/2017",
                Duration = 6,
              
                ParentId = 10
            });
            BusinessObjectCollection.Add(new BusinessObject()
            {
                TaskId = 15,
                TaskName = "Child task 5",
                StartDate = "10/25/2017",
                Duration = 6,
              
                ParentId = 10
            });

            return BusinessObjectCollection;
        }
        public class BusinessObject
        {
            public int TaskId { get; set; }
            public string TaskName { get; set; }
            public string StartDate { get; set; }
            public int Duration { get; set; }
            public int? ParentId { get; set; }            
        }
    }


{% endhighlight  %}

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")          
    .IdMapping("TaskId")
    .ParentIdMapping("ParentId")
    .Columns(co =>
        {
            co.Field("TaskId").HeaderText("Task Id").EditType(TreeGridEditingType.Numeric).Add();
            co.Field("TaskName").HeaderText("Task Name").EditType(TreeGridEditingType.String).Add();
            co.Field("StartDate").HeaderText("Start Date").EditType(TreeGridEditingType.Datepicker).Add();
            co.Field("Duration").HeaderText("Duration").EditType(TreeGridEditingType.Numeric).Add();
                    
        })        
    .Datasource(ViewBag.datasource)
    )
@(Html.EJ().ScriptManager())

{% endhighlight %}
{% endtabs %}  

The following screenshot shows the output of the above steps,

![](Data-Binding_images/Data-Binding_img2.png)

[Click](https://mvc.syncfusion.com/demos/web/treegrid/treegridselfreference) here to view the online demo sample for Self-Referential Data Binding.

## Remote data binding

### Load on demand

TreeGrid provides `Load on Demand` support for rendering remote data. Load on demand is considered in TreeGrid for the following actions, 

* Expanding root nodes.
* Navigating pages, with paging enabled in TreeGrid.

When load on demand is enabled, all the root nodes are rendered in collapsed state at initial load.

When load on demand support is enabled in TreeGrid with paging, the current or active page’s root node alone will be rendered in collapsed state. On expanding the root node, the child nodes will be loaded from the remote server. 

When a root node is expanded, its child nodes are rendered and are cached locally, such that on consecutive expand/collapse actions on root node, the child nodes are loaded from the cache instead from the remote server.

Similarly, if the user navigates to a new page, the root nodes of that specific page, will be rendered with request to the remote server.

N> 1. Load on demand support in TreeGrid can be enabled only for remote data.
N> 2. For better initial load time performance, we need to define the “HasChildMapping” property.

Load on demand support in TreeGrid can be enabled by the following ways,

1. By enabling `EnableLoadOnDemand` property of TreeGrid control
2. By enabling `CrossDomain` property while binding data source using ejDataManager control.

The following code explains how to use Load on Demand in TreeGrid Control,

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
    .IdMapping("TaskID")
    .ParentIdMapping("ParentID")
    .HasChildMapping("isParent")
    .EnableVirtualization(true)
    .Columns(co =>
    {
        co.Field("TaskID").HeaderText("Task Id").Width(45).Add();
        co.Field("TaskName").HeaderText("Task Name").Add();
        co.Field("StartDate").HeaderText("Start Date").Add();
        co.Field("EndDate").HeaderText("End Date").Add();                 
        co.Field("Progress").HeaderText("Progress").Add();
    })
    .Datasource(dataSource => dataSource.URL("http://js.syncfusion.com/demos/ejServices/Wcf/TreeGridGantt/TreeGantt.svc/SelfReferenceDatas").CrossDomain(true))
    )
@(Html.EJ().ScriptManager())

{% endhighlight %}

The output for load on demand support in TreeGrid:

![](Data-Binding_images/Data-Binding_img3.png)
![](Data-Binding_images/Data-Binding_img4.png)

The following code snippet shows on how to enable load on demand support using  [`EnableLoadOnDemand`](https://help.syncfusion.com/api/js/ejtreegrid#members:enableLoadOnDemand "enableLoadOnDemand") property.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
    .EnableLoadOnDemand(true)         
    .Datasource(dataSource => dataSource.URL("http://js.syncfusion.com/demos/ejServices/Wcf/TreeGridGantt/TreeGantt.svc/SelfReferenceDatas"))
    )
@(Html.EJ().ScriptManager())
{% endhighlight %}

The following output shows how load on demand works for expanding action

![](Data-Binding_images/Data-Binding_img5.png)

[Click](https://mvc.syncfusion.com/demos/web/treegrid/treegridloadondemand) here to view the online demo sample for Load on demand.

### Load at once:

On remote data binding, for every action such as paging, sorting, filtering, the data will be fetched from remote server each time. To avoid requesting the data from the remote server for each action, we can set TreeGrid to load all the data on initialization and make all the data operations in client side. To enable this, we can use Offline property of `ej.DataManager`. the following code example explains this.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
    .IdMapping("TaskID")
    .ParentIdMapping("ParentID")
    .HasChildMapping("isParent")
    .EnableVirtualization(true)
    .Columns(co =>
    {
        co.Field("TaskID").HeaderText("Task Id").Width(45).Add();
        co.Field("TaskName").HeaderText("Task Name").Add();
        co.Field("StartDate").HeaderText("Start Date").Add();
        co.Field("EndDate").HeaderText("End Date").Add();                 
        co.Field("Progress").HeaderText("Progress").Add();
    })
    .Datasource(dataSource => dataSource.URL("http://js.syncfusion.com/demos/ejServices/Wcf/TreeGridGantt/TreeGantt.svc/SelfReferenceDatas").Offline(true))
    )
@(Html.EJ().ScriptManager())

{% endhighlight %}

Please refer the [link](https://help.syncfusion.com/aspnetmvc/datamanager/advancedfunctionalities#offline-support "offline") for further reference on offline property

**Limitations**:

1. Mapping the expand state of a record using `ExpandStateMapping` property is not supported in load on demand feature.
2. If a root or parent node is in collapsed state (child nodes not yet loaded), then that parent node will not be expanded while inserting new child to that parent node using toolbar icon or drag and drop actions.

## Virtual rendering
Virtualization support is used to render large number of records in TreeGrid with effective performance. In this mode all the records are fetched from data source initially, but only few records will be displayed in the document object model (DOM) which should be visible to the user. While scrolling, the visible records are updated in DOM as per the scrolled position. This mode can be enabled by setting `EnableVirtualization` property as `true`. 

The below code example shows how to use this property.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")  
     //..        
    .EnableVirtualization(true)    
    )
@(Html.EJ().ScriptManager())

{% endhighlight %}

[Click](https://mvc.syncfusion.com/demos/web/treegrid/treegridvirtualization) here to view the online demo sample for Virtualization

