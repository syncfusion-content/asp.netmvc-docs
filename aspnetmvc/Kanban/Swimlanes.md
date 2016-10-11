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