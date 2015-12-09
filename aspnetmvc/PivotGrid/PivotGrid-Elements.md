---
layout: post
title: PivotGrid Elements | PivotGrid | ASP.NET MVC | Syncfusion
description: pivotGrid elements
platform: ejmvc
control: PivotGrid
documentation: ug
---

# PivotGrid: Elements

## Hyperlink

The PivotGrid control supports **hyperlink** option to link data for each individual cells. Hyperlink can be enabled separately for row, column, value and summary cells. Following are the respective properties:

* EnableColumnHeaderHyperlink - Enables hyperlink for column header.
* EnableRowHeaderHyperlink - Enables hyperlink for row header.
* EnableSummaryCellHyperlink - Enables hyperlink for summary cell.
* EnableValueCellHyperlink - Enables hyperlink for value cell.

Also hyperlink option provides separate event for row, column, value and summary cells as mentioned below.
 
* ColumnHeaderHyperlinkClick - Returns column header information through event on hyperlink click.
* RowHeaderHyperlinkClick - Returns row header information through event on hyperlink click.
* SummaryCellHyperlinkClick - Returns column header information through event on hyperlink click.
* ValueCellHyperlinkClick - Returns value cell information through event on hyperlink click.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("~/wcf/PivotGridService.svc")).ClientSideEvents(events => events.ValueCellHyperlinkClick("CellClickEvent").RowHeaderHyperlinkClick("CellClickEvent").ColumnHeaderHyperlinkClick("CellClickEvent").SummaryCellHyperlinkClick("CellClickEvent")).HyperlinkSettings(hypLink => hypLink.EnableColumnHeaderHyperlink(true).EnableRowHeaderHyperlink(true).EnableValueCellHyperlink(true).EnableSummaryCellHyperlink(true))

<script type="text/javascript">
    CellClickEvent = function(evt) {
        alert("Cell Click event is fired");
    }
</script>

{% endhighlight %}

![](PivotGrid-Elements_images/hyperlink.png)

## Selection

You can select a particular range of value cells from PivotGrid and manipulate/display them. Cell selection is applicable only for values cells and you can enable this functionality by setting `EnableCellSelection` property to true.
The **"CellSelection"** event would be triggered as soon as the selection process is over, that is, when the mouse left click is released. The event argument contains a collection of JSON records and header values, which contains information about the selected cells.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("~/wcf/PivotGridService.svc")).EnableCellSelection(true).ClientSideEvents(events => events.CellSelection("valueCellClick"))

<script type="text/javascript">
    valueCellClick = function(evt) {
        // The event lets you to perform required operation with the selected set of cells. The details of the selected range can be obtained in the parameter of the event.
        cellvalue = evt.JSONRecords;
        rowheaders = evt.rowHeader;
        colheaders = evt.columnHeader;
    }
</script>

{% endhighlight %}

![](PivotGrid-Elements_images/cellselection.png)

## Cell Context

**Cell context** allows user to perform any custom operation on cell right-click. For example, you can create and display content menu on cell right-click.

Cell context is enabled by setting the `EnableCellContext` property to true. The **"CellContext"** event would be raised as soon as right-click is done providing cell information through event argument.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("~/wcf/PivotGridService.svc")).EnableCellContext(true).ClientSideEvents(events=>events.CellContext("cell_RightClick"))

<script type="text/javascript">
    cell_RightClick = function(evt) {
        //Write your Cell Context code here
    }
</script>

{% endhighlight %}

## Conditional Formatting

**Conditional formatting** in PivotGrid allows user to highlight particular cells with certain color, font-style, font-family etc. Based on the condition it has met.
  
Conditional formatting is enabled by setting `EnableConditionalFormatting` property to true and the formatting dialog is launched when **"createConditionalDialog"** method is invoked.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("~/wcf/PivotGridService.svc")).EnableConditionalFormatting(true)
@Html.EJ().Button("Button1").Size(ButtonSize.Normal).Text("Conditional").ShowRoundedCorner(true).ClientSideEvents(events => events.Click("btnClick"))

<script type="text/javascript">
    function btnClick(e) {
        var pivotGridObj = $('#PivotGrid1').data("ejPivotGrid");
        if (pivotGridObj.model.enableConditionalFormatting) {
            pivotGridObj.createConditionalDialog();
        }
    }
</script>

{% endhighlight %}

![](PivotGrid-Elements_images/conditional.png)