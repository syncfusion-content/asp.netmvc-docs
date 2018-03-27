---
layout: post
title: Selection | Gantt | ASP.NET MVC | Syncfusion
description: selection
platform: ejmvc
control: Gantt
documentation: ug
---
# Selection

## Row selection

The row selection in Gantt can be enabled or disabled, by using the  `AllowSelection` property. You can able to get the selected row object using the `selectedItem` property from the Gantt model. The following code example shows how to disable the row selection in Gantt.

{% highlight CSHTML %}
@(Html.EJ().Gantt("Gantt")
  //...
  .AllowSelection(true)
  )
 @(Html.EJ().ScriptManager())
{% endhighlight %}

### Selecting a row on initial load

You can select a row on load time by setting the index of the row to `SelectedRowIndex` property. Find the following code example for details.

{% highlight CSHTML %}
@(Html.EJ().Gantt("Gantt")
   //...
  .SelectedRowIndex(3)
  )
@(Html.EJ().ScriptManager())
{% endhighlight %}

![](Selection_images/Selection_img1.png)

### Selecting a row programmatically 

You can also select a row programmatically by setting index of the row value to [`SelectedRowIndex`](/api/js/ejgantt#members:selectedrowindex) property. The following code shows to select a row programmatically with a custom button click action,

{% highlight CSHTML %}
 <button onclick="selectRow()">SelectRow</button>
@(Html.EJ().Gantt("Gantt")
  //...
  )
 @(Html.EJ().ScriptManager())

<script type="text/javascript">     
    function selectRow() {         
            $("#Gantt ").ejGantt("option", "selectedRowIndex", 4);
        }
</script>
{% endhighlight %}

### Multiple row selection

It is also possible to select multiple rows by setting `SelectionType` as `Multiple`. You can select more than one row by holding down `CTRL` key while selecting multiple rows.
The following code example explains how to enable multiple selection in Gantt.

{% highlight CSHTML %}
@(Html.EJ().Gantt("Gantt")
  //...
  .AllowSelection(true)
  .SelectionType(GanttSelectionType.Multiple)
  .SelectionMode(GanttSelectionMode.Row)
  )
@(Html.EJ().ScriptManager())
{% endhighlight %}

The output of the Gantt with multiple row selection is as follows.

![](Selection_images/Selection_img5.png)


### Selecting multiple rows programmatically 

You can also select multiple rows programmatically  by using `selectMultipleRows` public method. The following code example explains how to enable multiple selection in Gantt.

{% highlight CSHTML %}
 <button onclick="selectMultipleRow()">selectMultipleRow</button>
@(Html.EJ().Gantt("Gantt")
  .SelectionType(GanttSelectionType.Multiple)
  .SelectionMode(GanttSelectionMode.Row)
  )
 @(Html.EJ().ScriptManager())

<script type="text/javascript">     
function selectMultipleRow() {         
    var ganttObj = $("#Gantt").data("ejGantt"),
        multipleRowIndex = [1,0,5,7];  		    
  ganttObj.selectMultipleRows(multipleRowIndex);
    }
<script>
{% endhighlight %}

### Customize row selection action

While selecting a row in Gantt, `RowSelecting` and `RowSelected` event will be triggered. Row selecting event will be triggered on initialization of row selection action. In `RowSelecting` event we can get the previously selected row and current selecting row's information, using this information we can prevent selection of particular row. The `RowSelected` event will be triggered on completion of row selection action, in this event we can get the current selected row's information. The following code example shows how to prevent the selection of particular row using `RowSelecting` event.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
    //
  .AllowSelection(true)
  .SelectionType(GanttSelectionType.Multiple)
  .SelectionMode(GanttSelectionMode.Row)
  .ClientSideEvents(eve =>
  {
    eve.RowSelecting("rowSelecting");
  })
  )
@(Html.EJ().ScriptManager())

<script type="text/javascript">
function rowSelecting(args) {
if (args.data.taskId == 5) // prevent selection of Task id 5
  args.cancel = true;
      }
</script>

{% endhighlight %}

## Cell selection

You can select a cell in Gantt by setting `SelectionMode` property as `Cell`. And you can able to get the selected cell information using selectedCellIndexes property from the Gantt object. selectedCellIndexes is an object collection, which has the cell index and row index information of the selected cells.

Find the code example below to enable the cell selection in Gantt. 

{% highlight CSHTML %}
@(Html.EJ().Gantt("Gantt")
   //
 .SelectionMode(GanttSelectionMode.Cell)
  )
@(Html.EJ().ScriptManager()) 
{% endhighlight %}

The following screen shots shows you cell selection.

![](Selection_images/Selection_img2.png)

### Selecting multiple cells

You can also select multiple cells by setting `SelectionType` property as `Multiple` while `SelectionMode` property is set to `cell`. Multiple cells can be selected by holding the ctrl key and to click on the cells. The following code example shows you to select multiple cells.

{% highlight CSHTML %}
@(Html.EJ().Gantt("Gantt")
   //
 .SelectionType(GanttSelectionType.Multiple)
 .SelectionMode(GanttSelectionMode.Cell)
  )
@(Html.EJ().ScriptManager()) 
{% endhighlight %}

![](Selection_images/Selection_img3.png)

### Select cells programmatically 

You can select the cells programmatically using [`selectCells`](/api/js/ejgantt#methods:selectcells) public method. Find the code example below for details.

{% highlight CSHTML %}
 <button onclick="selectCells()">selectCells</button>
@(Html.EJ().Gantt("Gantt")
   .SelectionType(GanttSelectionType.Multiple)
   .SelectionMode(GanttSelectionMode.Cell)
  )
@(Html.EJ().ScriptManager()) 
<script type="text/javascript">     
function selectCells() {         
    var ganttObj = $("#GanttContainer").data("ejGantt");
        cellIndex = [{
                      rowIndex: 2,
                      cellIndex: 1
                      }, {
                      rowIndex: 3,
                      cellIndex: 1
                      }];
    ganttObj.selectCells(cellIndex);
}
<script>
{% endhighlight %}

![](Selection_images/Selection_img4.png)

### Customize cell selection action

While selecting a cell in Gantt, `CellSelecting` and `CellSelected` event will be triggered. 
Cell selecting event will be triggered on initialization of cell selection action. 
In `CellSelecting` event we can get the current selecting cell information, using this information we can prevent selection of particular cell in particular row. 
The `CellSelected` event will be triggered on completion of cell selection action, in this event we can get the current selected cell's information. The following code example shows how to prevent the selection of particular cell using `CellSelecting` event.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
   //
 .AllowSelection(true)
 .SelectionType(GanttSelectionType.Multiple)
 .SelectionMode(GanttSelectionMode.Row)
 .ClientSideEvents(eve =>
	{
		eve.CellSelecting("cellSelecting");
	})
  )
@(Html.EJ().ScriptManager())

<script type="text/javascript">
function cellSelecting(args) {
	if (args.data.taskId == 5 && args.cellIndex == 1) // prevent selection of Task Name cell of Task id 5
         args.cancel = true;
</script>

{% endhighlight %}

## MultiSelection – Touch Option

It is possible to select rows using touch action in Gantt. Gantt provides support for both single selection and multiple row selection using touch action. For multiple row selection, when we tap on a cell, a helper icon will be displayed using which we can select multiple rows.

The following code example describes how to enable multiple selection in Gantt.

{% highlight CSHTML %}
@(Html.EJ().Gantt("Gantt")
  //...
  .SelectionType(GanttSelectionType.Multiple)
  .SelectionMode(GanttSelectionMode.Row)
  )
@(Html.EJ().ScriptManager()) 
{% endhighlight %}

The following output is displayed the result of multiple selection in touch device environment.

![](Selection_images/Selection_img6.png)