---
layout: post
title: Swimlanes | Kanban | ASP.NET MVC | Syncfusion
description: Swimlanes
documentation: ug
control: Kanban
platform: ejmvc
---

# Swim lanes

Swim lanes are a horizontal categorization of issues in the Kanban control which brings transparency to the workflow. This can be enabled by mapping the `SwimlaneKey` to appropriate column name in the `DataSource`.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
                    .DataSource((IEnumerable<object>)ViewBag.datasource)
                    .Columns(col =>
                    {
                        col.HeaderText("Backlog").Key("Open").Add();
                        col.HeaderText("In Progress").Key("InProgress").Add();
                        col.HeaderText("Done").Key("Close").Add();
                    })
                    .KeyField("Status")
                    .Fields(field =>
                    {
                        field.Content("Summary")
                            .SwimlaneKey("Assignee")
                            .ImageUrl("ImgUrl")         
                            .PrimaryKey("Id");
                    })
                    
                    
    )

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            //
            // GET: /Kanban/
            public ActionResult KanbanFeatures()
            {
                var DataSource = new NorthwindDataContext().Tasks.Take(30).ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }
              
{% endhighlight  %}

{% endtabs %}  

The following output is displayed as a result of the above code example.

![](Swimlane_images/swimlane_img1.png)

# Drag And Drop between swim lanes

You can set 'AllowDragAndDrop' property of 'SwimlaneSettings' as true to enable Drag and Drop between the swim lanes.

If a card is to be dragged in the same swim lane, only a droppable target cell is added to the dotted line border.If a card is dragged from one swim lane to another, all the Kanban cells will be added to the dotted line borders, except the dragged card cell.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
                    .DataSource((IEnumerable<object>)ViewBag.datasource)
                    .Columns(col =>
                    {
                        col.HeaderText("Backlog").Key("Open").Add();
                        col.HeaderText("In Progress").Key("InProgress").Add();
                        col.HeaderText("Done").Key("Close").Add();
                    })
                    .KeyField("Status")
                     .SwimlaneSettings(swimSettings =>
                           {
                               swimSettings.AllowDragAndDrop(true);
                           })
                    .Fields(field =>
                    {
                        field.Content("Summary")
                            .SwimlaneKey("Assignee")
                            .ImageUrl("ImgUrl")         
                            .PrimaryKey("Id");
                    })                                      
    )
  
{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            // GET: /Kanban/
            public ActionResult KanbanFeatures()
            {
                var DataSource = new NorthwindDataContext().Tasks.Take(30).ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }
              
{% endhighlight  %}

{% endtabs %}  

The following output is displayed as a result of the above code example.

![](Swimlane_images/swimlane_img2.png)

# Unassigned swim lane group

Kanban cards which have null,undefined, empty string("") swimlane key values or user specified swimlane key values in the `Keys(SwimlaneSettings.UnassignedGroup.Keys)` collection will be grouped under the Unassigned swimlane group.You can enable and disble this behavior using the property `Enable(SwimlaneSettings.UnassignedGroup.Enable)` and the default value is `true`.
  
Default values in the `Keys(SwimlaneSettings.UnassignedGroup.Keys)` collection are null,undefined,empty string("").You can also add your own(user-defined) swim-lane key values in the `Keys(SwimlaneSettings.UnassignedGroup.Keys)` collection.
  
## Unassigned swim lane group with default values

Kanban cards which have null,undefined, empty string("") swimlane key values will be grouped under the Unassigned swimlane group when Unassigned swim lane group is enabled.(set `true` to `Enable(SwimlaneSettings.UnassignedGroup.Enable)` property and the default value is `true`).

Default values in the `Keys(SwimlaneSettings.UnassignedGroup.Keys)` collection are null,undefined,empty string("").

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
                    .DataSource((IEnumerable<object>)ViewBag.datasource)
                    .Columns(col =>
                    {
                        col.HeaderText("Backlog").Key("Open").Add();
                        col.HeaderText("In Progress").Key("InProgress").Add();
                        col.HeaderText("Done").Key("Close").Add();
                    })
                    .KeyField("Status")
                    .Fields(field =>
                    {
                        field.Content("Summary")
                            .SwimlaneKey("Assignee")
                            .ImageUrl("ImgUrl")
                            .PrimaryKey("Id");
                    })


    )

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            //
            // GET: /Kanban/
         public ActionResult KanbanFeatures()
          {
            List<Tasks> Task = new List<Tasks>();
            Task.Add(new Tasks(1, "Open", "Analyze the new requirements gathered from the customer.", "Story", "Low", "Analyze,Customer", 3.5, "Andrew Fuller", "../content/images/kanban/2.png", 1));
            Task.Add(new Tasks(2, "InProgress", "Improve application performance", "Improvement", "Normal", "Improvement", 6, "Andrew Fuller", "../content/images/kanban/2.png", 1));
            Task.Add(new Tasks(3, "Open", "Arrange a web meeting with the customer to get new requirements.", "Others", "Critical", "Meeting", 5.5, "", "", 2));
            Task.Add(new Tasks(4, "InProgress", "Fix the issues reported in the IE browser.", "Bug", "Release Breaker", "IE", 2.5, null, "", 2));
            Task.Add(new Tasks(5, "Close", "Fix the issues reported by the customer.", "Bug", "Low", "Customer", 3.5, "", "", 1));
            ViewBag.datasource = Task;
            return View();
         }
        }
    }
              
{% endhighlight  %}

{% endtabs %}  

The following output is displayed as a result of the above code example.

![](Swimlane_images/swimlane_img3.png)

## Unassigned swim lane group with user specified values

User specified swimlane key values in the `Keys(SwimlaneSettings.UnassignedGroup.Keys)` collection will be grouped under the Unassigned swimlane group when Unassigned swim lane group is enabled.(set `true` to `Enable(SwimlaneSettings.UnassignedGroup.Enable)` propertyproperty and the default value is `true`).

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

     @(Html.EJ().Kanban("Kanban")
                    .DataSource((IEnumerable<object>)ViewBag.datasource)
                    .Columns(col =>
                    {
                        col.HeaderText("Backlog").Key("Open").Add();
                        col.HeaderText("In Progress").Key("InProgress").Add();
                        col.HeaderText("Done").Key("Close").Add();
                    })
                    .KeyField("Status")
                    .Fields(field =>
                    {
                        field.Content("Summary")
                            .SwimlaneKey("Assignee")
                            .ImageUrl("ImgUrl")
                            .PrimaryKey("Id");
                    })
                    .SwimlaneSettings(ss =>
                       ss.UnassignedGroup(ug =>
                         ug.Keys(key =>
                         {
                             key.Add("Andrew Fuller");
                             key.Add("");
                             key.Add("null");
                         }
                         )
                       )
                    )

    )

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            //
            // GET: /Kanban/
        public ActionResult KanbanFeatures()
        {
            List<Tasks> Task = new List<Tasks>();
            Task.Add(new Tasks(1, "Open", "Analyze the new requirements gathered from the customer.", "Story", "Low", "Analyze,Customer", 3.5, "Nancy Davloio", "../content/images/kanban/1.png", 1));
            Task.Add(new Tasks(2, "InProgress", "Improve application performance", "Improvement", "Normal", "Improvement", 6, "Andrew Fuller", "../content/images/kanban/2.png", 1));
            Task.Add(new Tasks(3, "Open", "Arrange a web meeting with the customer to get new requirements.", "Others", "Critical", "Meeting", 5.5, "", "", 2));
            Task.Add(new Tasks(4, "InProgress", "Fix the issues reported in the IE browser.", "Bug", "Release Breaker", "IE", 2.5, null, "", 2));
            Task.Add(new Tasks(5, "Close", "Fix the issues reported by the customer.", "Bug", "Low", "Customer", 3.5, "", "", 1));
            ViewBag.datasource = Task;
            return View();
        }
        }
    }
              
{% endhighlight  %}

{% endtabs %}  

The following output is displayed as a result of the above code example.

![](Swimlane_images/swimlane_img4.png)

## Enable/Disable unassigned swim lane group

You can enable and disble the unassigned swim lane group using the property `Enable(SwimlaneSettings.UnassignedGroup.Enable)` and the default value is `true`.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

      @(Html.EJ().Kanban("Kanban")
                    .DataSource((IEnumerable<object>)ViewBag.datasource)
                    .Columns(col =>
                    {
                        col.HeaderText("Backlog").Key("Open").Add();
                        col.HeaderText("In Progress").Key("InProgress").Add();
                        col.HeaderText("Done").Key("Close").Add();
                    })
                    .KeyField("Status")
                    .Fields(field =>
                    {
                        field.Content("Summary")
                            .SwimlaneKey("Assignee")
                            .ImageUrl("ImgUrl")
                            .PrimaryKey("Id");
                    })
                    .SwimlaneSettings(ss =>
                       ss.UnassignedGroup(ug =>
                         ug.Enable(false)
                       )
                    )

    )

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            //
            // GET: /Kanban/
        public ActionResult KanbanFeatures()
        {
            List<Tasks> Task = new List<Tasks>();
            Task.Add(new Tasks(1, "Open", "Analyze the new requirements gathered from the customer.", "Story", "Low", "Analyze,Customer", 3.5, "Andrew Fuller", "../content/images/kanban/2.png", 1));
            Task.Add(new Tasks(2, "InProgress", "Improve application performance", "Improvement", "Normal", "Improvement", 6, "Andrew Fuller", "../content/images/kanban/2.png", 1));
            Task.Add(new Tasks(3, "Open", "Arrange a web meeting with the customer to get new requirements.", "Others", "Critical", "Meeting", 5.5, null, "", 2));
            Task.Add(new Tasks(4, "InProgress", "Fix the issues reported in the IE browser.", "Bug", "Release Breaker", "IE", 2.5, null, "", 2));
            Task.Add(new Tasks(5, "Close", "Fix the issues reported by the customer.", "Bug", "Low", "Customer", 3.5, null, "", 1));
            ViewBag.datasource = Task;
            return View();
        }
        }
    }
              
{% endhighlight  %}

{% endtabs %}  

The following output is displayed as a result of the above code example.

![](Swimlane_images/swimlane_img5.png)