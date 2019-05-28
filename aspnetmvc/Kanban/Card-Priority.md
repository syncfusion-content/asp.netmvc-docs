---
layout: post
title:  Prioritization of cards | Kanban | ASP.NET MVC | Syncfusion
description: The priority property is used to reorder the cards position in any desired place by dropping the card in Syncfusion ASP.NET MVC Kanban component.
documentation: ug
control: Kanban
platform: ejmvc
keywords: card priority
---

# Prioritization of cards

Prioritizing cards is easy with drag-and-drop re-ordering that helps you to categorize most important work at the top. Cards can be categorized with priority by mapping specific database field into `Priority` property.

`RankId` defined in the dataSource which is consist priority of cards. The `RankId` will be changed while card ordering changes through `Drag and Drop` and `Editing`.

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
                            .Priority("RankId")           
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

![Card Priority](Card_Priority_images/card_priority_img1.png)

N> For Drag and Drop event handling, please refer this [API](https://help.syncfusion.com/api/js/ejkanban#events:carddrag).

N> If the [`Priority`](https://help.syncfusion.com/api/js/ejkanban#members:fields-priority) property is not set in the Kanban fields, the cards are dropped based on the specifying JSON data orders in a particular column.  If not set, drop the card in a particular position based on the previous card `Priority` value and the next card’s `Priority` values will change dynamically.