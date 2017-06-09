---
layout: post
title: Editing | TreeGrid | ASP.NET MVC | Syncfusion
description: editing
platform: ejmvc
control: TreeGrid
documentation: ug
---

# Editing

The TreeGrid control provides built-in support for Editing cell items. 

## Cell Editing

Update the task details through grid Cell Editing by setting EditMode as CellEditing.

The following code example shows you how to enable CellEditing in TreeGrid control.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")

.EditSettings(edit =>

       {

           edit.AllowEditing(true);

           edit.EditMode(TreeGridEditMode.CellEditing);

       })

)

{% endhighlight %}

The output of TreeGrid with CellEditing is as follows.



![](Editing_images/Editing_img1.png)


## Cell Edit Template

Edit template is used to create custom editor for editing the column values. It can be created by using `EditTemplate` property of `Columns`.

The following are the functions available for edit template,

* `create` - It is used to create the control at time of initialize.
* `read` - It is used to read the input value at time of save.
* `write` - It is used to assign the value to control at time of editing.

The following code example describes edit template behavior

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
      .Columns(co =>
            {
                  co.Field("TaskName").HeaderText("Task Name").EditTemplate(new TreeGridEditTemplate() { Create="create",Write="write",Read="read" }).Add();
            })
)

{% endhighlight %}

{% highlight js %}
<script>
var autocompleteData = ["Planning", "Plan Timeline", "Plan Budget", "Allocate Resources", "Planning Complete"];
function create()
{
      return "<input>";
}

function write(args)
{
      args.element.ejAutocomplete({ 
           width: "100%", 
           dataSource: autocompleteData,
           enableDistinct: true,
           value: args.rowdata !== undefined ? args.rowdata["taskName"] : "" 
      });
}

function read(args)
{
      args.ejAutocomplete('suggestionList').css('display', 'none');
      return args.ejAutocomplete("getValue");
}
</script>

{% endhighlight %}

The output of the TreeGrid width EditTemplate as follows

![](Editing_images/editTemplate.png)


