---
layout: post
title: Data Binding | Gantt | ASP.NET MVC | Syncfusion
description: data binding
platform: ejmvc
control: Gantt
documentation: ug
---

# Data Binding

Data binding is the process that establishes a connection between the application and different kinds of data sources such as business objects. And it is possible to bind local data and remote data in Gantt.
You can set the data source for Gantt control by using `DataSource` property.

## Local Data Binding

In Local Data Binding, datasource for rendering the Gantt control is retrieved from the same application locally.

Two types of Data Binding are possible with Gantt control, 

* Hierarchical datasource binding
* Self-referential data binding (Flat data)

### Hierarchical data-source binding

In hierarchical data binding subtasks or child tasks collections are identified by using `ChildMapping` property.
The following code example explains how to bind the hierarchical data in Gantt.

{% tabs %}
  
{% highlight C# %}

 public class GanttController : Controller
    {
        //
        // GET: /Default/
        public ActionResult Default()
        {
            var DataSource = GanttDefaultData.GetData();
            ViewBag.datasource = DataSource;
            return View();
        }
        public class GanttDefaultData
        {
            public static List<DefaultData> GetData()
            {
                List<DefaultData> list = new List<DefaultData>();
                list.Add(new DefaultData()
                {
                    Id = 1,
                    Name = "Design",
                    StartDate = "02/10/2014",
                    EndDate = "02/14/2014",
                    Duration = 5,
                    PercentDone = 40,
                    Children = (new List<DefaultData>()
                    {
                        new DefaultData()
                        {
                            Id = 2,
                            Name = "Software Specification",
                            StartDate = "02/10/2014",
                            EndDate="02/12/2014",
                            Duration = 5,
                            PercentDone = 40
                        },
                        new DefaultData()
                        {
                            Id = 3,
                            Name = "Develop Prototype",
                            StartDate = "02/10/2014",
                            EndDate="02/12/2014",
                            Duration = 4,
                            PercentDone = 40,
                            Predecessor = "2"
                        },
                       //..
                    })
                });
                
                return list;
            }
        }

        public class DefaultData
        {
            public string StartDate { get; set; }
            public string EndDate { get; set; }
            public int Id { get; set; }
            public string Name { get; set; }
            public int Duration { get; set; }
            public int PercentDone { get; set; }
            public List<DefaultData> Children { get; set; }
            public string Predecessor { get; set; }

        }
    }
{% endhighlight %}

{% highlight CSHTML %}

@using Syncfusion.JavaScript
@using Syncfusion.MVC.EJ

<!DOCTYPE html>    
<html>
<head>
         @*Add script reference and style reference here*@
</head>
<body>			 
 @(Html.EJ().Gantt("ganttsample2")
              .TaskIdMapping("Id")
              .TaskNameMapping("Name")
              .StartDateMapping("StartDate")
              .DurationMapping("Duration")
              .ProgressMapping("PercentDone")              
              .TreeColumnIndex(1)
              .ChildMapping("Children")              
              .Datasource(ViewBag.datasource)
    )@(Html.EJ().ScriptManager())  
</body>
</html>
{% endhighlight %}
{% endtabs %}

The output of the above steps is as follows.

![](Data-Binding_images/Data-Binding_img1.png)

## Self-Referential Data Binding (Flat Data)

Gantt can be rendered from self-referential data structures, by mapping the task ID and parent task ID fields.

* Task ID field- This field must contain unique values to identify the nodes. It should be mapped to the `TaskIdMapping` property.
* Parent task ID field- This field must contain values to identify the parent nodes. It should be mapped to the `ParentTaskIdMapping` property.

{% tabs %}

{% highlight C# %}

public class GanttController : Controller
    {
        //
        // GET: /GanttSelfReference/

        public ActionResult GanttSelfReference()
        {
            var DataSource = GanttSelfData.GetData();
            ViewBag.datasource = DataSource;
            return View();
        }
        public class GanttSelfData
        {
            public static List<SelfData> GetData()
            {
                List<SelfData> data = new List<SelfData>();
                data.Add(new SelfData()
                {
                    Id = 1,
                    Name = "Task 1",
                    StartDate = "02/03/2014",
                    Duration = 5,
                    PercentDone = 40,
                    ParentId = null
                });
                data.Add(new SelfData()
                {
                    Id = 2,
                    Name = "Child Task 1",
                    StartDate = "02/03/2014",
                    Duration = 5,
                    PercentDone = 40,
                    ParentId = 1
                });
                data.Add(new SelfData()
                {
                    Id = 3,
                    Name = "Child Task 2",
                    StartDate = "02/03/2014",
                    Duration = 5,
                    PercentDone = 40,
                    ParentId = 1
                });
                data.Add(new SelfData()
                {
                    Id = 22,
                    Name = "Sub Child Task 1",
                    StartDate = "02/03/2014",
                    Duration = 5,
                    PercentDone = 40,
                    ParentId = 2
                });
                data.Add(new SelfData()
                {
                    Id = 23,
                    Name = "Sub Child Task 2",
                    StartDate = "02/03/2014",
                    Duration = 5,
                    PercentDone = 40,
                    ParentId = 2
                });
                data.Add(new SelfData()
                {
                    Id = 12,
                    Name = "Inner Child Task 1",
                    StartDate = "02/03/2014",
                    Duration = 5,
                    PercentDone = 40,
                    ParentId = 5
                });   
                 //..				
                return data;
            }
        }
        public class SelfData
        {
            public string StartDate { get; set; }
            public int Id { get; set; }
            public string Name { get; set; }
            public int Duration { get; set; }
            public int PercentDone { get; set; }
            public string Predecessor { get; set; }
            public int? ParentId { get; set; }

        }
    }
{% endhighlight %}

{% highlight CSHTML %}

 @(Html.EJ().Gantt("ganttsample2")
              .TaskIdMapping("Id")
              .TaskNameMapping("Name")
              .StartDateMapping("StartDate")
              .DurationMapping("Duration")
              .ProgressMapping("PercentDone")              
              .ParentTaskIdMapping("ParentId")              
              .Datasource(ViewBag.datasource)
    )@(Html.EJ().ScriptManager())
	
{% endhighlight %}
{% endtabs %}  

The following screenshot shows the output of the above steps.

![](Data-Binding_images/Data-Binding_img2.png)

You can find the online demo sample for binding self-referential data [here](https://mvc.syncfusion.com/demos/web/gantt/ganttselfreference)

## Remote data

### OData

OData is a standardized protocol for creating and consuming data. You can provide the OData service URL directly to the ej.DataManager class and then you can assign it to Gantt dataSource.

The following code example describes the above behavior.

{% highlight CSHTML %}

@(Html.EJ().Gantt("GanttContainer")
      .TaskIdMapping("TaskID")
      .TaskNameMapping("TaskName")
      .ParentTaskIdMapping("ParentID")      
      .StartDateMapping("StartDate")
      .EndDateMapping("EndDate")
      .Datasource(ds => ds.URL("http://js.syncfusion.com/demos/ejServices/Wcf/TreeGridGantt/TreeGantt.svc/SelfReferenceDatas"))
)@(Html.EJ().ScriptManager())

{% endhighlight %}

The following output is displayed for the code above,

![](Data-Binding_images/Data-Binding_img3.png)
![](Data-Binding_images/Data-Binding_img4.png)

### WebAPI

You can bind WebApi service data to Gantt. The data from WebApi service must be returned as object that has property Items with its value as datasource and this object can be pass to dataSource property of Gantt control.

The following code example describes the above behavior.

{% tabs %}
{% highlight CSHTML %}

@(Html.EJ().Gantt("GanttContainer")
      .TaskIdMapping("TaskID")
      .TaskNameMapping("TaskName")
      .ParentTaskIdMapping("ParentID")      
      .StartDateMapping("StartDate")
      .EndDateMapping("EndDate")
      .Datasource(ds => ds.URL("api/Home/GetGanttData"))
)@(Html.EJ().ScriptManager())

{% endhighlight %}

{% highlight C# %}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Net;
using System.Net.Http;
using System.Web.Http;
using GanttExportService.Models;
namespace GanttExportService {
    public class HomeController: ApiController {
        GanttDataEntities data = new GanttDataEntities();
        public object GetGanttData() {
            var Data = data.Table1.ToList();
            return Data;
        }
    }
}

{% endhighlight %}
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](Data-Binding_images/Data-Binding_img5.png)
![](Data-Binding_images/Data-Binding_img6.png)

## Virtualization mode in Gantt

Virtualization support was used to render large number tasks in Gantt with effective performance, in this mode all the tasks are fetched from data source initially then some of the records are rendered in DOM which are compact to the current viewport area. 
While scrolling tasks are updated in DOM as per current viewport position. 
This mode can be enabled by setting `EnableVirtualization` property as `true`. 
The below code example shows how to use this property.

{% highlight CSHTML %}

@(Html.EJ().Gantt("GanttContainer")
      .EnableVirtualization(true)
      //..
)@(Html.EJ().ScriptManager())

{% endhighlight %}

You can find the online demo sample of Gantt with virtualization mode [here](https://mvc.syncfusion.com/demos/web/gantt/virtualization).