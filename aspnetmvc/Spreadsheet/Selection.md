---
title: Selection with Spreadsheet widget for Syncfusion Essential ASP.NET MVC
description: How to perform Selection and configure its properties like selection type, selection mode etc.
platform: ejmvc
control: Spreadsheet
documentation: ug
---
# Selection

Selection provides an interactive support to highlight cell, row, or column that you select. Selection can be done through Mouse, Touch or Keyboard interaction. To enable selection, set `AllowSelection` as `true`.

## Selection Modes

The mode of selection can be single or range selection. The default selection mode can be set using `SelectionUnit` in `SelectionSettings`.
The two types of selection mode are as follows

* Single - `SpreadsheetSelectionUnit.Single`
* Range - `SpreadsheetSelectionUnit.Range`

## Selection Type

There are four types of selection in Spreadsheet

1. Cell Selection
2. Row Selection
3. Column Selection
4. Sheet Selection

You can set default `SelectionType` in `SelectionSettings`.

### Cell Selection 

Cell selection is used to select a single or multiple cells. It can be performed using [`selectRange`](http://help.syncfusion.com/api/js/ejspreadsheet#methods:xlselection-selectrange "selectRange") method. 
The following code example describes the above behavior,

{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .SelectionSettings(selectionOption =>
    {
        selectionOption.SelectionUnit(SpreadsheetSelectionUnit.Range);
    })
    .ClientSideEvents(events => events.LoadComplete("loadComplete"))
)

<script type="text/javascript">
    function loadComplete(args) {
        if(!this.isImport) {
            this.XLSelection.selectRange("A1:C3");
            this.XLDragFill.positionAutoFillElement();
        }
    }
</script>
    
{% endhighlight %}

The following output is displayed as a result of the above code example.
![](Selection_images/Selection_img1.png)

### Row Selection 

Row selection is used to select a single or multiple rows. It can be performed using [`selectRows`](http://help.syncfusion.com/api/js/ejspreadsheet#methods:xlselection-selectrows "selectRows") method.
The following code example describes the above behavior,

{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .ClientSideEvents(events => events.LoadComplete("loadComplete"))
)

<script type="text/javascript">
    function loadComplete(args) {
        if(!this.isImport) {
            this.XLSelection.selectRows(0,2);
            this.XLDragFill.positionAutoFillElement();
        }
    }
</script>
    
{% endhighlight %}

The following output is displayed as a result of the above code example.
![](Selection_images/Selection_img2.png)

N> This type can be set as default by setting `SelectionType` property in `SelectionSettings` as `SpreadsheetSelectionType.Row`

### Column Selection

Column selection is used to select a single or multiple columns. It can be performed using [`selectColumns`](http://help.syncfusion.com/api/js/ejspreadsheet#methods:xlselection-selectcolumns "selectColumns") method.
The following code example describes the above behavior,

{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .ClientSideEvents(events => events.LoadComplete("loadComplete"))
)

<script type="text/javascript">
    function loadComplete(args) {
        if(!this.isImport) {
            this.XLSelection.selectColumns(0,2);
            this.XLDragFill.positionAutoFillElement();
        }
    }
</script>
    
{% endhighlight %}

The following output is displayed as a result of the above code example.
![](Selection_images/Selection_img3.png)

N> This type can be set as default by setting `SelectionType` property in `SelectionSettings` as `SpreadsheetSelectionType.Column`

### Sheet Selection

Sheet selection is used to select all cells in a worksheet.  It can be performed using [`selectSheet`](http://help.syncfusion.com/api/js/ejspreadsheet#methods:xlselection-selectsheet "selectSheet") method.
The following code example describes the above behavior,

{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .ClientSideEvents(events => events.LoadComplete("loadComplete"))
)

<script type="text/javascript">
    function loadComplete(args) {
        if(!this.isImport) 
            this.XLSelection.selectSheet(); 
    }
</script>

{% endhighlight %}

The following output is displayed as a result of the above code example. 
![](Selection_images/Selection_img4.png)