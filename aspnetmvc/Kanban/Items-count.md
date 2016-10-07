---
layout: post
title: Items Count | Kanban | ASP.NET MVC | Syncfusion
description: Items Count
documentation: ug
control: Kanban
platform: ejmvc
---

# Items Count

You can show total cards count in each column's header using the property `EnableTotalCount` and the default value is `false`.

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
                    .EnableTotalCount(true)
                    .Fields(field =>
                    {
                        field.Content("Summary")  
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

![](Items_count_images/Items_count_img1.png)