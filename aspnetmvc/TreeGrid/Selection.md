---
layout: post
title: Selection | TreeGrid | ASP.NET MVC | Syncfusion
description: selection
platform: ejmvc
control: TreeGrid
documentation: ug
---

# Selection

The TreeGrid control provides support for row and cell selections using `SelectionSettings` property. 

## Row selection

You can enable or disable the row selection in TreeGrid, using the `AllowSelection` property. By default row selection is enabled in TreeGrid.
The following code example shows, how to disable the row selection in TreeGrid.


{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //...
        .AllowSelection(true)
        )        
@(Html.EJ().ScriptManager()) 

{% endhighlight %}

The output of the TreeGrid with row selection is as follows.

![](Selection_images/Selection_img1.png)

### Selecting a row at initial load

You can select a row at initial load by setting the index of the row to the `SelectedRowIndex` property.

Find the following code for selecting a row at initial load.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //...
        .SelectedRowIndex(3)
        )        
@(Html.EJ().ScriptManager())

{% endhighlight %}

### Multiple row selection

It is also possible to select multiple rows by setting the `SelectionType` as `Multiple`. You can select more than one row by holding down **CTRL** key and to click on the rows. 
The following code example explains how to enable multiple selection in TreeGrid.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //...
        .SelectionSettings(ss=>
        {
             ss.SelectionMode(TreeGridSelectionMode.Row);
             ss.SelectionType(TreeGridSelectionType.Multiple);
        }))        
@(Html.EJ().ScriptManager())

{% endhighlight %}

The output of the TreeGrid with multiple row selection is as follows.

![](Selection_images/Selection_img2.png)


### Selecting a row programmatically 

You can select a row programmatically by setting the row index value to the `SelectedRowIndex` property. 
The following code shows on how to select a row programmatically with button click action.

{% highlight CSHTML %}    
        
<button id="selectRow">SelectRow</button>      

@(Html.EJ().TreeGrid("TreeGridContainer")
   //..
   )        
@(Html.EJ().ScriptManager())

$("#selectRow").click(function (args) {
    $("#TreeGridContainer").ejTreeGrid("option", "selectedRowIndex", 4);           
})

{% endhighlight %}

### Customize row selection action

While selecting a row in TreeGrid, `RowSelecting` and `RowSelected` event will be triggered. Row selecting event will be triggered on initialization of row selection action. In `RowSelecting` event we can get the previously selected row and current selecting row’s information, using this information we can prevent selection of particular row. The `RowSelected` event will be triggered on completion of row selection action, in this event we can get the current selected row’s information. 

The following code example shows how to prevent the selection of particular row using `RowSelecting` event.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //...
        .ClientSideEvents(cs =>
        {
            cs.RowSelecting("rowSelecting");
        }))
@(Html.EJ().ScriptManager())

<script type="text/javascript">
function rowSelecting(args) {
    if(args.data.taskID == 5) // prevent selection of Task id 5
            args.cancel = true;
  }
</script>

{% endhighlight %}

## Get record details

In TreeGrid, It is possible to get the record detail when **click** and **dblClick** the row using `RecordClick` and `RecordDoubleClick` event, using this method we can get the record details even `AllowSelection` is `false`.

The below code example show, how to get record details when **click** the row.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //...
        .ClientSideEvents(cs =>
        {
            cs.RecordClick("recordClick");
        }))
@(Html.EJ().ScriptManager())

<script type="text/javascript">

function recordClick(args) {
   // Perform action for recordClick
  }
</script>

{% endhighlight %}

## Cell selection

You can select cells in TreeGrid by setting the `SelectionMode` property as `Cell`. 
And you can able to get the selected cell information using the `SelectedCellIndexes` property from the TreeGrid object. 
The `SelectedCellIndexes` is an object collection, which has the `CellIndex` and `RowIndex` information of the selected cells.

Find the code example below to enable the cell selection in TreeGrid.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //...
        .SelectionSettings(ss=>
        {
             ss.SelectionMode(TreeGridSelectionMode.Cell);            
        }))        
@(Html.EJ().ScriptManager())

{% endhighlight %}

The output of the TreeGrid with cell selection is as follows.

![](Selection_images/Selection_img3.png)

It is possible to get the list of HTML elements of the selected cells at run-time using the [`getSelectedCells`](https://help.syncfusion.com/api/js/ejtreegrid#methods:getselectedcells "getSelectedCells") method.

### Select cells dynamically

You can select the cells programmatically using the [`selectCells`](/api/js/ejtreegrid#methods:selectcells "selectCells(indexes,preservePreviousSelectedCell)") public method. Find the code example below for details.

{% highlight CSHTML %}

<button id="selectCells">Select Cells</button>

@(Html.EJ().TreeGrid("TreeGridContainer")
        //...
        .SelectionSettings(ss=>
        {
             ss.SelectionMode(TreeGridSelectionMode.Cell);
             ss.SelectionType(TreeGridSelectionType.Multiple);
        }))        
@(Html.EJ().ScriptManager())

$("#selectCells").click(function () {
         var treegridObj = $("#TreeGridContainer").ejTreeGrid("instance");
         var cellIndex = [{
            rowIndex: 2,
            cellIndex: 1
        }, {
            rowIndex: 3,
            cellIndex: 1
        }];       
        treegridObj.selectCells(cellIndex);    
     })

{% endhighlight %}

![](Selection_images/Selection_img8.png)

### Disabling cell selection for specific column

It is possible to disable cell selection for a specific column by setting `AllowCellSelection` as `false` in the column definition.

The below code snippet explains how to disable cell selection for specific column in tree grid

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //...        
        .Columns(co =>
        {
            //..
            co.Field("TaskId").AllowCellSelection(false).Add();            
        }))        
@(Html.EJ().ScriptManager())

{% endhighlight %}

### Multiple cell selection

You can also select multiple cell by setting the `SelectionType` property as `Multiple`. 
Multiple selection can be done by holding the **CTRL** key and to click the required cells. 
The following code example shows you to select multiple cells.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //...
        .SelectionSettings(ss=>
        {
             ss.SelectionMode(TreeGridSelectionMode.Cell);
             ss.SelectionType(TreeGridSelectionType.Multiple);
        }))        
@(Html.EJ().ScriptManager())

{% endhighlight %}

The output of the TreeGrid with multiple cell selection is as follows.

![](Selection_images/Selection_img4.png)

### Customize cell selection action

While selecting a cell in TreeGrid, `CellSelecting` and `CellSelected` event will be triggered. Cell selecting event will be triggered on initialization of cell selection action. In `CellSelecting` event we can get the current selecting cell information, using this information we can prevent selection of particular cell in particular row. The `CellSelected` event will be triggered on completion of cell selection action, in this event we can get the current selected cell's information. 

The following code example shows how to prevent the selection of particular cell using `CellSelecting` event.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //...
        .ClientSideEvents(cs =>
        {
            cs.CellSelecting("cellSelecting");
        }))
@(Html.EJ().ScriptManager())

<script type="text/javascript">
function cellSelecting(args) {
   if(args.data.taskID == 5 && args.cellIndex == 1) // prevent selection of Task Name cell of Task id 5
                args.cancel = true;
  }
</script>

{% endhighlight %}

## Checkbox selection

TreeGrid supports checkbox selection and to enable the checkbox selection, you need to set the `SelectionType` property to `Checkbox` and the `SelectionMode` property as `Row`. By default, checkbox column will be displayed as the left most column, on enabling the checkbox selection in TreeGrid.

### Column header checkbox

It is possible to select/unselect all the TreeGrid rows using column header checkbox. To enable this you need to set the `EnableSelectAll` property as `true`. The following code snippet explains how to enable the column header checkbox.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //..
        .SelectionSettings(ss=>
            {
                ss.SelectionMode(TreeGridSelectionMode.Row);
                ss.SelectionType(TreeGridSelectionType.Checkbox);
                ss.EnableSelectAll(true);
            })
       )
@(Html.EJ().ScriptManager())

{% endhighlight %}

The output of the TreeGrid with checkbox enabled in column header.

![](Selection_images/Selection_img5.png)

### Hierarchy selection
It is possible to select the rows hierarchically using checkboxes in TreeGrid by enabling the `EnableHierarchySelection` property.
In this selection the hierarchy between the records will be retained, where the child records will get selected on selecting its parent record’s checkbox and parent record checkbox will get selected on checking all of its child items. 

Following code snippet explains on enabling hierarchy selection in TreeGrid.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //..
        .SelectionSettings(ss=>
            {
                ss.SelectionMode(TreeGridSelectionMode.Row);               
                ss.SelectionType(TreeGridSelectionType.Checkbox);
                ss.EnableHierarchySelection(true);
            })
       )
@(Html.EJ().ScriptManager())

{% endhighlight %}

The output of the TreeGrid with hierarchy selection enabled.

![](Selection_images/Selection_img6.png)

### Checkbox column

It is possible to change the default index of the checkbox column and we can display the checkboxes in any of the existing column. And to enable the checkbox in any of the column, we need to set `Columns.ShowCheckbox` property as true in the column object.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //..
        .SelectionSettings(ss=>
            {
                ss.SelectionMode(TreeGridSelectionMode.Row);               
                ss.SelectionType(TreeGridSelectionType.Checkbox);                
            })
         .Columns(co =>
        {
            co.Field("taskName").HeaderText("Task Name").ShowCheckbox(true).Add();
        }) 
       )
@(Html.EJ().ScriptManager())

{% endhighlight %}

The output of the TreeGrid with checkbox enabled in task name column.

![](Selection_images/Selection_img7.png)

## MultiSelection – Touch Option

It is possible to select cells using touch action in TreeGrid. TreeGrid provides support for both single selection and multiple cell selection using touch action. For multiple cell selection, when we tap on a cell a helper icon will be displayed using that we can select multiple cells.

The following code example describes how to enable multiple selection in TreeGrid.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
        //...
        .SelectionSettings(ss=>
        {
             ss.SelectionType(TreeGridSelectionType.Multiple);
        }))        
@(Html.EJ().ScriptManager())

{% endhighlight %}

The following output is displayed the result of multiple selection in touch device environment.

![](Selection_images/multiselection.png)

## Clear selection using method

It is possible to clear the selection in TreeGrid at run-time using the [`clearSelection`](/api/js/ejtreegrid#methods:clearselection "clearSelection") method.

The specific row will be deselected when the row index is passed as the method parameter. If the index is not passed, then all the selected rows in tree grid will be deselected.

{% highlight CSHTML %}

<button id="clearSelection">Clear Selection</button>

@(Html.EJ().TreeGrid("TreeGridContainer")
        //...
      )        
@(Html.EJ().ScriptManager())

$("#clearSelection").click(function () {
         var treegridObj = $("#TreeGridContainer").data("ejTreeGrid");
             treegridObj.clearSelection(2);   
     })

{% endhighlight %}