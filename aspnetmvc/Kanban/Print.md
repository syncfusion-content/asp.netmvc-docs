---
layout: post
title: Print | Kanban | ASP.NET MVC | Syncfusion
description: This section explains how to perform printing feature using the Syncfusion ASP.NET MVC Kanban component.
documentation: ug
control: Kanban
platform: ejmvc
---

# Print

 Set ‘AllowPrinting’ as true, to enable Print icon in the Kanban toolbar.  You can use ‘print()’ method from Kanban instance to print the Kanban.

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
        .AllowTitle(true)
        .AllowPrinting(true)
        .Fields(field =>
        {
            field.Content("Summary")
                .Tag("Tags")
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

![Print in ASP NET MVC kanban control](Printing_images/print_img1.png)


