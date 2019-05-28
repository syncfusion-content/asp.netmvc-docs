---
layout: post
title: Scrolling | Kanban | ASP.NET MVC | Syncfusion
description: This section explains how to achieve the scrolling behavior of the Syncfusion ASP.NET MVC Kanban component.
documentation: ug
control: Kanban
platform: ejmvc
---

# Scrolling

Scrolling can be enabled by setting `AllowScrolling` as true. The height and width can be set to Kanban by using the properties `ScrollSettings.Height` and `ScrollSettings.Width `respectively.

N> The height and width can be set in percentage and pixel. The default value for `Height` and `Width` in `ScrollSettings` is 0 and auto respectively.

## Set width and height in pixel

To specify the `ScrollSettings.Width` and `ScrollSettings.Height` in pixel, by set the pixel value as integer.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
        .DataSource((IEnumerable<object>)ViewBag.datasource)
        .AllowScrolling(true)
        .ScrollSettings(scroll=>scroll.Width(900).Height(450))
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

![](Scrolling_images/scroll_img1.png)

## Set height and width in percentage

To specify the `ScrollSettings.Width` and `ScrollSettings.Height` in percentage, by set the percentage value as string.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
        .DataSource((IEnumerable<object>)ViewBag.datasource)
        .AllowScrolling(true)
                .ScrollSettings(scroll => scroll.Width("70%").Height("70%"))
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

![](Scrolling_images/scroll_img2.png)

## Set width as auto

Specify `Width` property of `ScrollSettings` as auto, then the scrollbar is rendered only when the Kanban width exceeds the browser window width.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
        .DataSource((IEnumerable<object>)ViewBag.datasource)
        .AllowScrolling(true)
        .ScrollSettings(scroll => scroll.Width("auto").Height("500"))
        .Columns(col =>
        {
            col.HeaderText("Backlog").Key("Open").Add();
            col.HeaderText("In Progress").Key("InProgress").Add();
            col.HeaderText("Testing").Key("Testing").Add();
            col.HeaderText("Done").Key("Close").Add();
        })
        .KeyField("Status")
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

![](Scrolling_images/scroll_img3.png)

## Enabling freeze swim lane

Set `AllowFreezeSwimlane` as true. This enables scrolling with freezing of swim lane until you scroll to the next Swim lane, which helps user to aware of current swim lane target.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
     .DataSource((IEnumerable<object>)ViewBag.datasource)
     .AllowScrolling(true)
     .ScrollSettings(scroll => scroll.Width("auto").Height("500").AllowFreezeSwimlane(true))
     .Columns(col =>
     {
         col.HeaderText("Backlog").Key("Open").Add();
         col.HeaderText("In Progress").Key("InProgress").Add();
         col.HeaderText("Testing").Key("Testing").Add();
         col.HeaderText("Done").Key("Close").Add();
     })
     .KeyField("Status")
     .Fields(field =>
     {
         field.Content("Summary")
             .Tag("Tags")
             .SwimlaneKey("Assignee")
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

![](Scrolling_images/scroll_img4.png)

N> `AllowFreezeSwimlane` is applicable when swim lane grouping enabled by setting `SwimlaneKey`.


