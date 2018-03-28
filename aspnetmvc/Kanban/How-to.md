---
layout: post
title: How to
description: How to
platform: ejmvc
control: Kanban
documentation: ug
---
# How to

## Render Kanban from Code behind

Kanban can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side.

The following code illustrates the initialization of Kanban properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (Kanban) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class KanbanController: Controller
    {
        public ActionResult KanbanFeatures()
        {

             // Initialize data for Kanban

            List<Tasks> Task = new List<Tasks>();

            Task.Add(new Tasks(1, "Open", "Analyze the new requirements gathered from the customer.", "Story", "Low", "Analyze,Customer", 3.5, "Andrew Fuller", "../content/images/kanban/1.png", 1));
            Task.Add(new Tasks(2, "InProgress", "Improve application performance", "Improvement", "Normal", "Improvement", 6, "Andrew Fuller", "../content/images/kanban/2.png", 1));
            Task.Add(new Tasks(3, "Open", "Arrange a web meeting with the customer to get new requirements.", "Others", "Critical", "Meeting", 5.5, "Janet", "../content/images/kanban/3.png", 2));
            Task.Add(new Tasks(4, "InProgress", "Fix the issues reported in the IE browser.", "Bug", "Release Breaker", "IE", 2.5, "Janet", "../content/images/kanban/3.png", 2));
            Task.Add(new Tasks(5, "Testing", "Fix the issues reported by the customer.", "Bug", "Low", "Customer", 3.5, "Andrew Fuller", "../content/images/kanban/5.png", 1));


            //Initializing the kanban model

            KanbanProperties kanbanObj = new KanbanProperties();


            //Initializing the datasource and columns 

             kanbanObj.DataSource = Task;

             kanbanObj.Columns.Add(new KanbanColumn() { HeaderText = "Backlog", Key = new List<string> { "Open" } });
             kanbanObj.Columns.Add(new KanbanColumn() { HeaderText = "In Progress", Key = new List<string> { "InProgress" } });
             kanbanObj.Columns.Add(new KanbanColumn() { HeaderText = "Done", Key = new List<string> { "Close" } });

            //Define the fields

            kanbanObj.KeyField = "Status";

            kanbanObj.Fields.Color = "Type";
            kanbanObj.Fields.Content = "Summary";
            kanbanObj.Fields.PrimaryKey = "Id";

          //Passing kanban properties using the ViewData

            ViewData["KanbanModel"] = kanbanObj;

            return View();
        }
    }
}

{% endhighlight %}

Binding the Kanban properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().Kanban("Kanban", (Syncfusion.JavaScript.Models.KanbanProperties)ViewData["KanbanModel"]).Render();
}

{% endhighlight %}