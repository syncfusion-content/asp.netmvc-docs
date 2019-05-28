---
layout: post
title: Responsive | Kanban | ASP.NET MVC | Syncfusion
description: This section explains the responsive behavior of the Syncfusion ASP.NET MVC Kanban component based on the client browser width and height.
documentation: ug
control: Kanban
platform: ejmvc
---

# Responsive

The Kanban control has support for responsive behavior based on client browser’s width and height. To enable responsive, `IsResponsive` property should be true.There are two modes of responsive layout is available in Kanban based on client width. They are.

* Mobile(<480px)
* Desktop(>480px)

You can check the image representation of touch actions from the below image.

![](Responsive_images/KanbanOverlayImage.png)

## Mobile Layout

If client width is less than 480px, the Kanban will render in mobile mode. In which, you can see that kanban user interface is customized and redesigned for best view in small screens.To enable responsive, `IsResponsive` property should be true. 

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
                   .DataSource((IEnumerable<object>)ViewBag.datasource)
                   .IsResponsive(true)
                   .AllowSelection(false)
                   .AllowKeyboardNavigation(true)
                   .AllowTitle(true)
                   .Columns(col =>
                   {
                       col.HeaderText("Backlog").Key("Open").ShowAddButton(true).Add();
                       col.HeaderText("In Progress").Key("InProgress").Add();
                       col.HeaderText("Testing").Key("Testing").Add();
                       col.HeaderText("Done").Key("Close").Add();
                   })
                  .KeyField("Status")
                   .EditSettings(edit =>
                          {
                              edit.AllowAdding(true)
                                  .AllowEditing(true)
                                  .EditItems(e =>
                                  {
                                      e.Field("Id").ValidationRules(rule => { rule.AddRule("required", true).AddRule("number", true); }).Add();
                                      e.Field("Status").EditType(KanbanEditingType.Dropdown).Add();
                                      e.Field("Assignee").EditType(KanbanEditingType.Dropdown).Add();
                                      e.Field("Estimate").EditType(KanbanEditingType.Numeric).NumericEditOptions(new EditorProperties() { DecimalPlaces = 2 }).ValidationRules(rule => { rule.AddRule("range", "[0,1000]"); }).Add();
                                      e.Field("Summary").EditType(KanbanEditingType.TextArea).ValidationRules(rule => { rule.AddRule("required", true); }).Add();
                                  }).EditMode(KanbanEditMode.Dialog);
                          })
                          .AllowSearching(true)
                           .FilterSettings(filter =>
                           {
                               filter.Text("Janet Issues").Query("new ej.Query().where('Assignee', 'equal', 'Janet')").Description("Displays issues which matches the assignee as 'Janet").Add();
                               filter.Text("Testing Issues").Query("new ej.Query().where('Status', 'equal', 'Testing')").Description("Display the issues of 'Testing'").Add();
                           })
                  .Fields(field =>
                  {
                      field.Color("Type")
                           .PrimaryKey("Id")
                           .Content("Summary")
                           .ImageUrl("Image");
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

![](Responsive_images/Responsive_img2.png)


W> IE8 and IE9 does not support responsive kanban. `ej.responsive.css` should be referred to display Responsive Kanban.

![](Responsive_images/Responsive_img3.png)
{:caption}
CRUD in mobile layout

![](Responsive_images/Responsive_img4.png)
{:caption}
Filtering in mobile layout

![](Responsive_images/Responsive_img5.png)
{:caption}
Searching in mobile layout

![](Responsive_images/Responsive_img6.png)

![](Responsive_images/Responsive_img7.png)
{:caption}
Kanban with Swim-lane


## Width

By default, the Kanban is adaptable to its parent container. It can adjust its width of columns based on parent container width. You can also assign width of `Columns` in percentage. 

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
        .DataSource((IEnumerable<object>)ViewBag.datasource)
        .IsResponsive(true)
        .Columns(col =>
        {
            col.HeaderText("Backlog").Key("Open").Width(10).Add();
            col.HeaderText("In Progress").Key("InProgress").Width(10).Add();
            col.HeaderText("Done").Key("Close").Width(10).Add();
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

N>  `AllowScrolling` should be false while defining width in percentage.

## Min Width

Min Width is used to maintain minimum width for the Kanban. If the Kanban width is less than `MinWidth` then the scrollbar will be displayed to maintain minimum width.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
     .DataSource((IEnumerable<object>)ViewBag.datasource)
     .IsResponsive(true)
     .MinWidth(700)
     .Columns(col =>
     {
         col.HeaderText("Backlog").Key("Open").Width(120).Add();
         col.HeaderText("In Progress").Key("InProgress").Width(110).Add();
         col.HeaderText("Done").Key("Close").Width(110).Add();
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

![](Responsive_images/responsive_img1.png)