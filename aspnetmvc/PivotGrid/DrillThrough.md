---
layout: post
title:  Drill Through | PivotGrid | ASP.NET MVC | Syncfusion
description:  This document explains that how to define drill through feature with respective to the modes in ASP.NET MVC PivotGrid control
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Drill Through

Drill-through retrieves the raw items that are used to create a specific cell. To enable drill-through support, set `EnableDrillThrough` property to true. Raw items are obtained through the [`DrillThrough`] event, using which user can bind them to an external widget for precise view.

## OLAP

N> Drill-through is supported in PivotGrid only when we configure and enable drill-through action at the Cube.

![Drill through support in ASP NET MVC pivot grid control](DrillThrough_images/pivotgrid.png)

On clicking any value cell, the "Drill Through Information" dialog will be opened.  It consists of a Grid with data which are associated with the measure values of clicked value cell. In this example, the measure behind the respective cell is “Sales Amount” and the values of the dimensions which are associated with this measure are alone displayed in the Grid.

![Drill through data in ASP NET MVC pivot grid control](DrillThrough_images/DrillThroughData.png)

On clicking the "Hierarchy Selector" button which is displayed below the Grid, the Hierarchy Selector dialog will be opened. It consists of the dimensions which are associated with the measure of the clicked value cell. In this example, the measure behind the respective cell is “Sales Amount” and the dimensions associated with this measure are alone displayed in the dialog.

![Hierarchy selector in ASP NET MVC pivot grid control](DrillThrough_images/hierarchy_selector.png)

By dragging and dropping the respective hierarchies and finally clicking “OK”, drill through MDX query will be framed and executed internally and provides back the raw items through "DrillThrough" event. In this example, we have bound the raw items obtained to our ejGrid widget. Please refer the code sample and screen-shot below.

## Client Mode

{% highlight cshtml %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(.....).EnableDrillThrough(true).ClientSideEvents(events => events.DrillThrough("drilledData"))

<script type="text/javascript">
    function drilledData(args) {
        $(".e-dialog, .e-clientDialog, .e-tableDlg").remove();
        gridData = JSON.parse(args.data);
        var dialogContent = ej.buildTag("div#" + this._id + "_tableDlg.tableDlg", $("<div id=\"Grid1\"></div>"))[0].outerHTML;
        var dialogFooter = ej.buildTag("div", ej.buildTag("button#btnOK.e-dialogBtnOK", "Hierarchy Selector")[0].outerHTML, { "float": "right", "margin": "-5px 0 6px" })[0].outerHTML
        ejDialog = ej.buildTag("div#clientDialog.e-clientDialog", dialogContent + dialogFooter, { "opacity": "1" }).attr("title", "Drill Through Information")[0].outerHTML;
        $(ejDialog).appendTo("#" + this._id);
        $("#btnOK").ejButton().css({ margin: "30px 0 20px 0" });
        $("#Grid1").ejGrid({
            dataSource: gridData,
            allowPaging: true,
            allowTextWrap: true,
            pageSettings: { pageSize: 8 }
        });
        this.element.find(".e-clientDialog").ejDialog({ width: "70%", content: "#" + this._id, enableResize: false, close: ej.proxy(ej.Pivot.closePreventPanel, this) });
        var pivotGrid = $("#" + this._id).data("ejPivotGrid");
        $("#btnOK").click(function () {
            ej.Pivot.openHierarchySelector(pivotGrid);
        });
    }
</script>

{% endhighlight %}

## Server Mode

{% highlight cshtml %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("/OLAPService")).EnableDrillThrough(true).ClientSideEvents(events => events.DrillThrough("drilledData"))

<script type="text/javascript">
    function drilledData(args) {
        $(".e-dialog, .e-clientDialog, .e-tableDlg").remove();
        gridData = ej.isNullOrUndefined(args.data.d) ? JSON.parse(args.data.DrillDataTable) : JSON.parse(args.data.d[1].Value);
        var dialogContent = ej.buildTag("div#" + this._id + "_tableDlg.e-tableDlg", $("<div id=\"Grid1\"></div>"))[0].outerHTML;
        var dialogFooter = ej.buildTag("div", ej.buildTag("button#btnOK.e-dialogBtnOK", "Hierarchy Selector")[0].outerHTML, { "float": "right", "margin": "-5px 0 6px" })[0].outerHTML
        ejDialog = ej.buildTag("div#clientDialog.e-clientDialog", dialogContent + dialogFooter, { "opacity": "1" }).attr("title", "Drill Through Information")[0].outerHTML;
        $(ejDialog).appendTo("#" + this._id);
        $("#btnOK").ejButton().css({ margin: "30px 0 20px 0" });
        $("#Grid1").ejGrid({
            dataSource: gridData,
            allowPaging: true,
            allowTextWrap: true,
            pageSettings: { pageSize: 8 }
        });
        this.element.find(".e-clientDialog").ejDialog({ width: "70%", content: "#" + this._id, enableResize: false, close: ej.proxy(ej.Pivot.closePreventPanel, this) });
        var pivotGrid = this;
        $("#btnOK").click(function () {
            $(".e-dialog, .e-clientDialog, .tableDlg").remove();
            if (pivotGrid.model.operationalMode == ej.PivotGrid.OperationalMode.ServerMode) {
                pivotGrid._waitingPopup.show()
                pivotGrid.doAjaxPost("POST", pivotGrid.model.url + "/" + pivotGrid.model.serviceMethodSettings.drillThroughHierarchies, JSON.stringify({ "currentReport": JSON.parse(pivotGrid.getOlapReport()).Report, "layout": pivotGrid.model.layout, "cellPos": "", "customObject": JSON.stringify(pivotGrid.model.customObject) }), function (args) {
                    ej.Pivot.openHierarchySelector(pivotGrid, args);
                })
            }
        });
    }
</script>

{% endhighlight %}

When PivotGrid is rendered in server mode, below service methods need to be added in WCF/WebAPI for drill through operation.

For WebAPI controller, the below methods need to be added.

{% highlight c# %}

[System.Web.Http.ActionName("DrillThroughHierarchies")]
[System.Web.Http.HttpPost]
public string DrillThroughHierarchies(Dictionary<string, object> jsonResult)
{
    OlapDataManager DataManager = new OlapDataManager(connectionString);
    DataManager.SetCurrentReport(OLAPUTILS.Utils.DeserializeOlapReport(jsonResult["currentReport"].ToString()));
    return htmlHelper.DrillthroughHierarchies(DataManager, jsonResult["layout"].ToString(), jsonResult["cellPos"].ToString());
}

[System.Web.Http.ActionName("DrillThroughDataTable")]
[System.Web.Http.HttpPost]
public Dictionary<string, object> DrillThroughDataTable(Dictionary<string, object> jsonResult)
{
    OlapDataManager DataManager = new OlapDataManager(connectionString);
    DataManager.SetCurrentReport(OLAPUTILS.Utils.DeserializeOlapReport(jsonResult["currentReport"].ToString()));
    return htmlHelper.DrillthroughDataTable(DataManager, jsonResult["layout"].ToString(), jsonResult["cellPos"].ToString(), jsonResult["selector"].ToString());
}

{% endhighlight %}

For WCF service, the below methods need to be added.

{% highlight c# %}

public string DrillThroughHierarchies(string currentReport, string layout, string cellPos)
{
    OlapDataManager DataManager = new OlapDataManager(connectionString);
    DataManager.SetCurrentReport(OLAPUTILS.Utils.DeserializeOlapReport(currentReport));
    return htmlHelper.DrillthroughHierarchies(DataManager, layout, cellPos);
}

public Dictionary<string, object> DrillThroughDataTable(string currentReport, string layout, string cellPos, string selector)
{
    OlapDataManager DataManager = new OlapDataManager(connectionString);
    DataManager.SetCurrentReport(OLAPUTILS.Utils.DeserializeOlapReport(currentReport));
    return htmlHelper.DrillthroughDataTable(DataManager, layout, cellPos, selector);
}

{% endhighlight %}


![Drill through data in ASP NET MVC pivot grid OLAP server mode](DrillThrough_images/drill_data.png)

## Relational

To enable drill-through support, set `EnableDrillThrough` property to true. Raw items are obtained through the `DrillThrough` event.

{% highlight cshtml %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(.....).EnableDrillThrough(true).ClientSideEvents(events => events.DrillThrough("drillData"))

<script type="text/javascript">
    function drillData(args) {
            gridData = args.selectedData;
            var dialogContent = ej.buildTag("div#Grid", { height: "50px" })[0].outerHTML;
            ejDialog = ej.buildTag("div#clientDialog.e-clientDialog", dialogContent, { "opacity": "1", "overflow": "auto" }).attr("title", "Drill Through Information")[0].outerHTML;
            $(ejDialog).appendTo("#" + this._id);
            this.element.find(".e-clientDialog").ejDialog({ width: "70%", height: "100%", content: "#" + this._id, enableResize: false, close: ej.proxy(ej.Pivot.closePreventPanel, this) });

            $("#Grid").ejGrid({
                dataSource: gridData,
            });
        }
</script>

{% endhighlight %}

![Drill through data in ASP NET MVC pivot grid relational mode](DrillThrough_images/DrillThroughRelational.png)