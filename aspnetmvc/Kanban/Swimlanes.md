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
                            .ImageUrl("Image")         
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

## Customized swimlane header text

You can change the swimlane row header text using the swimlane `Headers` property.  In this property, the text is changed using the `Text` property and the corresponding value is mapped into the `Key` property based on `SwimlaneKey` datasource mapping.

Refer to the following code example.

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
                  .AllowTitle(true)
                    .KeyField("Status")
                  .Fields(field => 
                   {
                      field.Content("Summary")
                           .SwimlaneKey("Assignee")
                           .PrimaryKey("Id");
                   })
                   .SwimlaneSettings(swim =>
                   {
                      swim.Headers(header => {
                          header.Text("Andrew").Key("Andrew Fuller").Add();
                          header.Text("Janet").Key("Janet").Add(); 
                         });
                   })
)
  
{% endhighlight  %}

{% highlight c# %}

    public partial class KanbanController : Controller
    {
        List<Tasks> Task = new List<Tasks>();
        
        // GET: /Kanban/
        public ActionResult KanbanFeatures()
        {
            Task.Add(new Tasks(6, "Close", "Arrange a web meeting with the customer to get the login page requirements.", "Others", "Low", "Meeting", 2, "Janet", "../content/images/kanban/3.png", 1));
            Task.Add(new Tasks(7, "Validate", "Validate new requirements", "Improvement", "Low", "Validation", 1.5, "Janet", "../content/images/kanban/3.png", 4));
            Task.Add(new Tasks(8, "Close", "Login page validation", "Story", "Release Breaker", "Validation,Fix", 2.5, "Andrew Fuller", "../content/images/kanban/1.png", 2));
            Task.Add(new Tasks(9, "Testing", "Fix the issues reported in Safari browser.", "Bug", "Release Breaker", "Fix,Safari", 1.5, "Janet", "../content/images/kanban/3.png", 2));
            Task.Add(new Tasks(10, "InProgress", "Test the application in the IE browser.", "Story", "Low", "Testing,IE", 5.5, "Andrew Fuller", "../content/images/kanban/1.png", 3));
            ViewBag.datasource = Task;
            return View();
        }
    }
    public class Tasks
    {
        public Tasks()
        {
        }
        public Tasks(int Id, string Status, string Summary, string Type, string Priority, string Tags, double Estimate, string Assignee, string Image, int RankId)
        {
            this.Id = Id;
            this.Status = Status;
            this.Summary = Summary;
            this.Type = Type;
            this.Priority = Priority;
            this.Tags = Tags;
            this.Estimate = Estimate;
            this.Assignee = Assignee;
            this.Image = Image;
            this.RankId = RankId;
        }
        public int Id { get; set; }
        public string Status { get; set; }
        public string Summary { get; set; }
        public string Type { get; set; }
        public string Priority { get; set; }
        public string Tags { get; set; }
        public double Estimate { get; set; }
        public string Assignee { get; set; }
        public string Image { get; set; }
        public int RankId { get; set; }
    }
              
{% endhighlight  %}

{% endtabs %}

The following output is displayed as a result of the above code example.

![](Swimlane_images/swimlane_img6.png)

## Empty swimlane row on Kanban board

You can create an empty swimlane row by enabling the `ShowEmptySwimlane` property based on swimlane headers `Key` value mapping.  If no data is present, then the empty swimlane row is rendered on the Kanban board based on the specified swimlane headers `Key`.

Refer to the following code.

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
                  .AllowTitle(true)
                    .KeyField("Status")
                  .Fields(field => 
                   {
                      field.Content("Summary")
                           .SwimlaneKey("Assignee")
                           .PrimaryKey("Id");
                   })
                   .SwimlaneSettings(swim =>
                   {
                      swim.ShowEmptySwimlane(true)
                          .Headers(header => {
                                   header.Text("Andrew").Key("Andrew Fuller").Add();
                                   header.Text("Janet").Key("Janet Leverling").Add(); 
                           });
                   })
)

{% endhighlight  %}

{% highlight c# %}

public partial class KanbanController : Controller
    {
        List<Tasks> Task = new List<Tasks>();
        
        // GET: /Kanban/
        public ActionResult KanbanFeatures()
        {
            Task.Add(new Tasks(8, "Close", "Login page validation", "Story", "Release Breaker", "Validation,Fix", 2.5, "Andrew Fuller", "../content/images/kanban/1.png", 2));
            Task.Add(new Tasks(9, "Testing", "Fix the issues reported in Safari browser.", "Bug", "Release Breaker", "Fix,Safari", 1.5, "Janet", "../content/images/kanban/3.png", 2));
            Task.Add(new Tasks(10, "InProgress", "Test the application in the IE browser.", "Story", "Low", "Testing,IE", 5.5, "Andrew Fuller", "../content/images/kanban/1.png", 3));
            ViewBag.datasource = Task;
            return View();
        }
    }
    public class Tasks
    {
        public Tasks()
        {
        }
        public Tasks(int Id, string Status, string Summary, string Type, string Priority, string Tags, double Estimate, string Assignee, string Image, int RankId)
        {
            this.Id = Id;
            this.Status = Status;
            this.Summary = Summary;
            this.Type = Type;
            this.Priority = Priority;
            this.Tags = Tags;
            this.Estimate = Estimate;
            this.Assignee = Assignee;
            this.Image = Image;
            this.RankId = RankId;
        }
        public int Id { get; set; }
        public string Status { get; set; }
        public string Summary { get; set; }
        public string Type { get; set; }
        public string Priority { get; set; }
        public string Tags { get; set; }
        public double Estimate { get; set; }
        public string Assignee { get; set; }
        public string Image { get; set; }
        public int RankId { get; set; }
    }

{% endhighlight  %}

{% endtabs %}

The following output is displayed as a result of the above code example.

![](Swimlane_images/swimlane_img7.png)

## Drag And Drop between swim lanes

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
                            .ImageUrl("Image")         
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

## Unassigned swim lane group

Unassigned swim lane feature provides option to group some common swim lane key values as separate swim lane group. You can enable and disable this behavior using the property `Enable`.
User can use default common key values or user defined key values. 

    *	Using default values
    * 	Using user defined values

N> By default, given common keys are grouped under the swim lane name `Unassigned`, user can customize the name using localization.

### Using default values

By default, the swim lane keys of card which is having null, undefined, empty string ("") values will be grouped as unassigned category when `Enable` property is set as true. 
Default values in the `Keys` collection are null, undefined, empty string ("").

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
                            .ImageUrl("Image")
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

The output of the above code example.

![](Swimlane_images/swimlane_img3.png)

### Using user defined values

You can override default values for unassigned swim lane group using the property `Keys`.

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
                            .ImageUrl("Image")
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
            Task.Add(new Tasks(1, "Open", "Analyze the new requirements gathered from the customer.", "Story", "Low", "Analyze,Customer", 3.5, "Nancy", "../content/images/kanban/1.png", 1));
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

The output of the above code example.

![](Swimlane_images/swimlane_img4.png)
