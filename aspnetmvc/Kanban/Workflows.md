---
layout: post
title: Workflows | Kanban | ASP.NET MVC | Syncfusion
description: Workflows
documentation: ug
control: Kanban
platform: ejmvc
---

# Workflows 

Workflows can be defined to set the flow of card moving between the Kanban column statuses and it is applicable to drag and drop and context menu features.

You can set `Workflows` as array of Objects which consists of `Key` and `AllowedTransitions` properties. The `AllowedTransitions` accepts more than one transition of the specific column key mentioned in `Key` property.

If a card is to be dragged to not allowed transition columns , then not supported warning symbol will be displayed for denoting the error.
        
The following code example describes the above Workflow functionality.

{% highlight html %}

    <div id='Kanban'></div>

{% endhighlight %}

{% highlight javascript %}

     @(Html.EJ().Kanban("Kanban")
                    .DataSource((IEnumerable<object>)ViewBag.datasource)
                    .Workflows(workflow =>
                   {
                       workflow.Key("Open").AllowedTransitions("InProgress").Add();
                       workflow.Key("InProgress").AllowedTransitions("Testing,Close").Add();
                   })
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
                    })
    )

{% endhighlight %}

The following output is displayed as a result of the above code example.

![](WorkFlows_images/workflows1.png)
