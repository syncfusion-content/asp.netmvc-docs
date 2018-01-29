---
layout: post
title: Editing | Gantt | ASP.NET MVC | Syncfusion
description: editing
platform: ejmvc
control: Gantt
documentation: ug
---

# Editing

The Gantt control provides in-built support to add, insert and update the tasks. The following are the types of editing available in Gantt.

* Cell Editing
* Normal Editing
* Taskbar Editing
* Dependency Editing

## Cell Editing

### Initialize cell edit mode

Update the task details through grid cell editing by setting `EditSettings.EditMode` as `cellEditing`.
The following code example shows you how to enable the `cellEditing` in Gantt control.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EditSettings(edit=>{
        edit.AllowEditing(true);
        edit.EditMode("cellEditing");
    })
    .Datasource(ViewBag.datasource)
)

{% endhighlight %}

The output of Gantt with cell editing is as follows.
![](Editing_images/Editing_img1.png)

### Save editing cell

Currently editing cell value can be saved by clicking the save toolbar icon or clicking on any other cell element in the grid and also editing cell can be saved by using [`saveEdit`](/api/js/ejgantt#methods:saveedit) method, using this method we can save the current editing cell dynamically on any action like external button click, please refer the following code example.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EditSettings(edit=>{
        edit.AllowEditing(true);
        edit.EditMode("cellEditing");
    })
    .Datasource(ViewBag.datasource)
);

<script>

$("#save_button").click(function () {
    $("#Gantt").ejGantt("instance").saveEdit();
});

</script>

{% endhighlight %}

### Cancel editing cell

Currently editing cell value can be restored with old value by using cancel toolbar icon or by pressing <kbd>Esc</kbd> key. And also this can be done by using [`cancelEdit`](/api/js/ejgantt#methods:canceledit) method on any other external actions like button click, please refer the following code example.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EditSettings(edit=>{
        edit.AllowEditing(true);
        edit.EditMode("cellEditing");
    })
    .Datasource(ViewBag.datasource)
);

<script>

$("#cancel_button").click(function () {
    $("#Gantt").ejGantt("instance").cancelEdit();
});

</script>

{% endhighlight %}

### Prevent Cell Editing

In cell editing action `BeginEdit` and `EndEdit` client side events are triggered before and after the editing action. Cell editing for particular column or specific cell can be prevented by using `BeginEdit` client side event, please refer following code example for this.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EditSettings(edit=>{
        edit.AllowEditing(true);
        edit.EditMode("cellEditing");
    })
    .ClientSideEvents(cs => cs.BeginEdit("beginEdit"))
    .Datasource(ViewBag.datasource)
);

<script>

function beginEdit(args) {
    if (args.columnIndex == 1)
        args.cancel = true;
}

</script>

{% endhighlight %}

## Normal Editing

### Initialize Normal edit mode

Update the task details through edit dialog by setting `EditMode` as `normal`. The following code example shows you how to enable normal editing in Gantt control.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EditSettings(edit=>{
        edit.AllowEditing(true);
        edit.EditMode("normal");
    })
    .Datasource(ViewBag.datasource)
);

{% endhighlight %}

The following screenshot shows the output of `normal` editing.

![](Editing_images/Editing_img2.png)

### Define required fields in add/edit dialog

In Gantt we can define the editing fields available in add and edit dialogs by using `AddDialogFields` and `EditDialogFields` properties. Each editing fields are defined with `Field` and `EditType` properties. The following code example shows how to define `EditDialogFields` property.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EditSettings(edit=>{
        edit.AllowEditing(true);
        edit.EditMode("normal");
    })
    .EditDialogFields(edf => 
    {
        edf.Field("TaskID").EditType("stringedit").Add();
        edf.Field("TaskName").EditType("stringedit").Add();
        edf.Field("StartDate").EditType("datepicker").Add();
        edf.Field("EndDate").EditType("datepicker").Add();
        edf.Field("Duration").EditType("stringedit").Add();
    })
    .Datasource(ViewBag.datasource)
);

{% endhighlight %}

The following screenshot show the output of above code example.
![](Editing_images/Editing_img4.png)

N> Similarly we can define the required fields in add dialog with `AddDialogFields.Field` and `AddDialogFields.EditType` properties.

### Add custom column fields in General tab

By default custom column fields are included in add/edit dialog's custom field tab but we can display this column field in General tab by setting `DisplayInGeneralTab` property as `true` in `AddDialogFields` and `EditDialogFields` properties. The following code example shows how to add custom column field in General tab of edit dialog.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EditSettings(edit=>{
        edit.AllowEditing(true);
        edit.EditMode("normal");
    })
    .EditDialogFields(edf => 
    {
        edf.Field("TaskID").EditType("stringedit").Add();
        edf.Field("TaskName").EditType("stringedit").Add();
        edf.Field("StartDate").EditType("datepicker").Add();
        edf.Field("EndDate").EditType("datepicker").Add();
        edf.Field("Duration").EditType("stringedit").Add();
        edf.Field("CustomField").EditType("stringedit").DisplayInGeneralTab(true).Add();
    })
    .ClientSideEvents(cs => cs.Load("load"))
    .Datasource(ViewBag.datasource)
);

<script>

function load(args) {
    var column = { field: "CustomField", mappingName: "CustomField", headerText: "Custom Field" };
    this.getColumns().push(column); 
}

</script>

{% endhighlight %}

The following screenshot show the output of above code example.
![](Editing_images/Editing_img5.png)

N> Similarly we can include custom fields in add dialog's General tab by setting `DisplayInGeneralTab` as `true` in `AddDialogFields` collection.

N> Default columns predecessors, resources and notes are displayed in separate tabs, we can't include this in General tab of add/edit dialog.

### Open add/edit dialog dynamically

Gantt add and edit dialogs can be opened dynamically by using [`openAddDialog`](/api/js/ejgantt#methods:openadddialog) and [`openEditDialog`](/api/js/ejgantt#methods:openeditdialog) methods. The following code example shows how to open add and dialog on separate button click actions.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EditSettings(edit=>{
        edit.AllowEditing(true);
        edit.EditMode("normal");
    })
    .Datasource(ViewBag.datasource)
);

<script>
$("#openAddDialog").click(function(){
    $("#Gantt").ejGantt("instance").openAddDialog();
});

$("#openEditDialog").click(function(){
    $("#Gantt").ejGantt("instance").openEditDialog();
});
</script>

{% endhighlight %}

N> We should select any one of the row in Gantt to open the edit dialog.

## Taskbar Editing

Update the task details by interactions such as resizing and dragging the taskbar. Taskbar editing can be enabled by setting `AllowGanttChartEditing` as `true`. The following code example shows you how to enable taskbar resizing in Gantt control.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .AllowGanttChartEditing(true)
    .Datasource(ViewBag.datasource)
);

{% endhighlight %}

You can also enable or disable the progress bar resizing by using the `EnableProgressBarResizing`. The following code example shows how to disable this property.

@(Html.EJ().Gantt("Gantt")
    //...
    .EnableProgressBarResizing(false)
    .Datasource(ViewBag.datasource)
);

{% endhighlight %}

### Prevent taskbar editing for particular task

On taskbar edit action `TaskbarEditing` and `TaskbarEdited` client side event will be triggered. We can prevent the taskbar from editing by using `TaskbarEditing` event and we can revert taskbar edit action by using `TaskbarEdited` event. The following code example shows how to achieve this.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .AllowGanttChartEditing(true)
    .ClientSideEvents(cs => cs.TaskbarEditing("taskbarEditing").TaskbarEdited("taskbarEdited"))
    .Datasource(ViewBag.datasource)
);

<script>
function taskbarEditing(args) {
    if (args.rowData.taskId == 4) // We can't edit Task Id 4
        args.cancel = true;
}
function taskbarEdited(args) {
    if (args.data.taskId == 5) // We can edit task id 5 task but changes reverted on mouse up action
        args.cancel = true;
}
</script>

{% endhighlight %}

## Dependency Editing

In Gantt, we can add, edit, update the task dependencies by mouse interactions, edit dialog and public methods. The code example shows how to enable dependency editing in Gantt.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .AllowGanttChartEditing(true)
    .PredecessorMapping("Predecessors")
    .Datasource(ViewBag.datasource)
);

{% endhighlight %}

### Add Dependency

Task dependency can be added by mouse interactions by connecting connector points in predecessor and successor tasks. The following screen shot shows the add dependency action.

![](Editing_images/Editing_img3.png)

### Edit Dependency

Task dependency value can be edited by using edit dialog and [`updateDependency`](api/js/ejgantt#methods:updatedependency) method. Dependency edit dialog can be opened by double clicking on corresponding dependency line.

Client side `ActionBegin` client event will be triggered twice with different `requestType` argument values while opening of dependency dialog. First time, event will be triggered with `requestType` argument values as `beforeDependencyEditDialogOpen`, in this event we can get the current editing dependency line information, next `ActionBegin` client side event will be triggered with `requestType` argument value as `afterDependencyEditDialogOpen`, in this event we can get the information about current editing dependency line and editing elements in edit dialog. Using this event we can customize the dependency edit dialog elements.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .AllowGanttChartEditing(true)
    .PredecessorMapping("Predecessors")
    .ClientSideEvents(cs => cs.ActionBegin("actionBegin"))
    .Datasource(ViewBag.datasource)
);

<script>

function actionBegin(args) {
    if(args.requestType == "beforeDependencyEditDialogOpen") {

    }
    else if(args.requestType == "afterDependencyEditDialogOpen") {

    }
}

</script>
{% endhighlight %}

The following screen shot shows the dependency edit dialog.
![](Editing_images/Predecessor_Editing_Dialog.png)

### Delete Dependency

Task dependency can be deleted by using edit dialog and [`deleteDependency`](api/js/ejgantt#methods:deletedependency) method. The following screen shot shows the dependency edit dialog with delete option.

![](Editing_images/Predecessor_Editing_Dialog.png)

[Click](https://mvc.syncfusion.com/demos/web/gantt/ganttediting) here to view the online demo sample for editing in Gantt.

## Update Gantt record value dynamically

Gantt record's value can be dynamically updated by using [`updateRecordByTaskId`](/api/js/ejgantt#methods:updaterecordbytaskid "updateRecordByTaskId(data)") or [`updateRecordByIndex`](/api/js/ejgantt#methods:updaterecordbyindex "updateRecordByIndex(index, data)") method. [`updateRecordByTaskId`](/api/js/ejgantt#methods:updaterecordbytaskid "updateRecordByTaskId(data)") method used to update the Gantt record by using it's task id value and [`updateRecordByIndex`](/api/js/ejgantt#methods:updaterecordbyindex "updateRecordByIndex(index, data)") method was used to update Gantt record value by row index value. We can invoke this method on any external button click action, the following code example shows how to use this methods.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .Datasource(ViewBag.datasource)
);

<script>
$("#updateRecordByTaskId").click(function () {
    var ganttObj = $("#Gantt").ejGantt("instance"),
        data = {
                taskID: 4,
                taskName: "Updated by task id",
                startDate: new Date("02/10/2014"),
                endDate: new Date("02/14/2014"),
                duration: 5,
                progress: "80",
                resourceId: [2]
            };
    ganttObj.updateRecordByTaskId(data);
});

$("#updateRecordByRowIndex").click(function () {
    var ganttObj = $("#Gantt").ejGantt("instance"),
        data = {
                taskID: 5,
                taskName: "Updated by index value",
                startDate: new Date("02/10/2014"),
                endDate: new Date("02/14/2014"),
                duration: 3, progress: "100",
                predecessor: "4SS",
                resourceId: [2]
        };
    ganttObj.updateRecordByIndex(4, data);
});
</script>

{% endhighlight %}

You can find the JS playground sample for this [here](http://jsplayground.syncfusion.com/Sync_w5suulh5).

N> Using these methods we can't update the task id value.

## Delete confirmation message

Delete confirmation message is used to get the confirmation from the user before delete the record. This confirmation message can be enabled by setting `EditSettings.ShowDeleteConfirmDialog` property as `true`.

The following code snippet explains how to enable delete confirmation message in Gantt.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EditSettings(edit =>
    {
        edit.AllowDeleting(true);
        edit.ShowDeleteConfirmDialog(true);
    })
    .Datasource(ViewBag.datasource)
);

{% endhighlight %}

![](Editing_images/deleteConfirmation.png)

The above screen shot shows the appearance of delete confirmation message in Gantt.

## Task Indent

Task indent option in Gantt was enabled by setting `EditSettings.AllowIndent` as `true`. Tasks can be indented by clicking on indent toolbar item or by using [`indentItem`](/api/js/ejgantt#methods:indentitem) method. We can invoke this method dynamically on any action like external button click. The below code example shows how to enable indent option in Gantt.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EditSettings(edit =>
    {
        edit.AllowIndent(true);
    })
    .ToolbarSettings(toolbar =>
    {
    toolbar.ShowToolbar(true);
    toolbar.ToolbarItems(new List<GanttToolBarItems>()
        {
            //...
            GanttToolBarItems.Indent,
        });
    })
    .Datasource(ViewBag.datasource)
);

<script>

$("#indentTask").click(function () {
    var ganttObj = $("#Gantt").ejGantt("instance");
    if (ganttObj.selectedRowIndex() != -1)
        ganttObj.indentItem();
});

</script>

{% endhighlight %}

The following screenshots shows the output of above code example.

![](Editing_images/Editing_img6.png)

Before Indent
{:.caption}

![](Editing_images/Editing_img7.png)

After Indent
{:.caption}

N> We should select any one of the row in Gantt to perform task indent action.

## Task Outdent

Task outdent option in Gantt was enabled by setting `EditSettings.AllowIndent` as `true`. Tasks can be outdent by clicking on outdent toolbar item or by using [`outdentItem`](/api/js/ejgantt#methods:outdentitem) method. We can invoke this method dynamically on any action like external button click. The below code example shows how to enable outdent option in Gantt.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EditSettings(edit =>
    {
        edit.AllowIndent(true);
    })
    .ToolbarSettings(toolbar =>
    {
    toolbar.ShowToolbar(true);
    toolbar.ToolbarItems(new List<GanttToolBarItems>()
        {
            //...
            GanttToolBarItems.Outdent,
        });
    })
    .Datasource(ViewBag.datasource)
);

<script>

$("#outdentTask").click(function () {
    var ganttObj = $("#Gantt").ejGantt("instance");
    if (ganttObj.selectedRowIndex() != -1)
        ganttObj.outdentItem();
});

</script>

{% endhighlight %}

The following screenshots shows the output of above code example.

![](Editing_images/Editing_img6.png)

Before Outdent
{:.caption}

![](Editing_images/Editing_img8.png)

After Outdent
{:.caption}

N> We should select any one of the row in Gantt to perform task outdent action.

## Task Delete

Task delete option in Gantt was enabled by setting `EditSettings.AllowDeleting` as `true`. Tasks can be delete by clicking on delete toolbar item or by using [`deleteItem`](/api/js/ejgantt#methods:deleteitem) method. We can invoke this method dynamically on any action like external button click. The below code example shows how to enable delete option in Gantt.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .EditSettings(edit =>
    {
        edit.AllowDeleting(true);
    })
    .ToolbarSettings(toolbar =>
    {
    toolbar.ShowToolbar(true);
    toolbar.ToolbarItems(new List<GanttToolBarItems>()
        {
            //...
            GanttToolBarItems.Delete,
        });
    })
    .Datasource(ViewBag.datasource)
);

<script>

$("#deleteTask").click(function () {
    var ganttObj = $("#Gantt").ejGantt("instance");
    if (ganttObj.selectedRowIndex() != -1)
        ganttObj.deleteItem();
});

</script>

{% endhighlight %}

The following screenshots shows the output of above code example.

![](Editing_images/Editing_img6.png)
Before Delete
{:.caption}

![](Editing_images/Editing_img9.png)
After Delete
{:.caption}

N> We should select any one of the row in Gantt to perform task delete action.

## Read-only Gantt

In Gantt, all editing options can be disabled by setting `ReadOnly` property as `true`. The following code example shows how to make Gantt control as read-only.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //...
    .ReadOnly(true)
    .Datasource(ViewBag.datasource)
);

{% endhighlight %}
