---
layout: post
title: PivotTable Field List | PivotGrid | ASP.NET MVC | Syncfusion
description: pivotTable field list
platform: ejmvc
control: PivotGrid
documentation: ug
---

# PivotTable Field List

## Initialization  

Field List, also known as Pivot Schema Designer, allows user to add, rearrange, filter and remove fields to show data in PivotGrid exactly the way they want.

Based on the datasource, OLAP, bound to the PivotGrid control, PivotTable Field List will be automatically populated with Cube Information or Field Names. PivotTable Field List provides an Excel like appearance and behavior.

In-order to initialize PivotTable Field List, first you need to define a “div” tag with an appropriate “id” attribute which acts as a container for the control. Then you need to initialize the PivotTable Field List by using the **"PivotSchemaDesigner"** method.

### Client Mode

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").ClientSideEvents(clientSideEvents => clientSideEvents.RenderSuccess("loadSchemaDesigner")).DataSource(dataSource => dataSource.Values(values => { values.Axis(AxisName.Column).Measures(measures => { measures.FieldName("[Measures].[Internet Sales Amount]").Add(); }).Add(); }).Rows(rows => { rows.FieldName("[Customer].[Customer Geography]").Add(); }).Columns(columns=>{columns.FieldName("[Date].[Fiscal]").Add();}).Data("http://bi.syncfusion.com/olap/msmdpump.dll").Cube("Adventure Works").Catalog("Adventure Works DW 2008 SE"))
@Html.EJ().Pivot().PivotSchemaDesigner("PivotSchemaDesigner")

<script type="text/javascript">
    function loadSchemaDesigner(args) {
        var PivotSchemaDesigner = $("#PivotSchemaDesigner").data('ejPivotSchemaDesigner');
        if (PivotSchemaDesigner.model.pivotControl == null) {
            PivotSchemaDesigner.model.pivotControl = this;
            PivotSchemaDesigner.model.enableWrapper = true;
            PivotSchemaDesigner.model.layout = "excel";
            PivotSchemaDesigner._load();
        }
        args.model.renderSuccess = null;
    }
</script>

{% endhighlight %}

![](PivotTable-Field-List_images/OlapClientMode.png)

### Server Mode 

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("~/OLAPService")).ClientSideEvents(events => events.AfterServiceInvoke("OnAfterServiceInvoke"))
@Html.EJ().Pivot().PivotSchemaDesigner("PivotSchemaDesigner").Layout(PivotSchemaDesignerLayout.Excel)

<script type="text/javascript">
    OnAfterServiceInvoke = function(evt) {
        if (evt.action == "initialize") {
            var PivotSchemaDesigner = $("#PivotSchemaDesigner").data('ejPivotSchemaDesigner');
            if (PivotSchemaDesigner.model.pivotControl == null) {
                PivotSchemaDesigner.model.pivotControl = this;
                PivotSchemaDesigner.model.enableWrapper = true;
                PivotSchemaDesigner.model.layout = "excel";
                PivotSchemaDesigner._load();
            }
        }
    }
</script>

{% endhighlight %}

![](PivotTable-Field-List_images/schema1.png)

## Layout

The top portion of the layout shows Field or Cube items in a categorized way. They can be dynamically added into the report either by drag and drop option or through simple check box selection.
 
On item(s) selection they will be placed in Row section by default except numeric based item(s) or measures, which will alone be placed in the Value section by default.

The bottom portion of the layout is segregated as below.

* Report Filter: Exclusively designed to filter an item(s) placed in this particular position of the layout. 
* Value Section: The value label usually displays the numeric value item(s) present in the report.
* Column Section: It is used to display item(s) as column header and values in the PivotGrid control. 
* Row Section: It is used to display item(s) as row header and values in the PivotGrid control.
 
## UI Interactions 
You can alter the report on fly through drag-and-drop operation. You can drag any item from Field List and drop into column, row, value or filter section available at the bottom of the Field List.

![](PivotTable-Field-List_images/schema.png)

You can also alter the report on fly through check and uncheck option as an alternate. By default, fields will be added to the Row Label when checked.

![](PivotTable-Field-List_images/check-uncheck.png)

## Searching Values
Search option available in Field List allows you to search a specific value that needs to be filtered from the list of values inside the filter pop-up window.

![](PivotTable-Field-List_images/filter.png)

![](PivotTable-Field-List_images/search.png)

## Filtering
Values can be filtered by checking/unchecking the check box besides them, inside the filter pop-up window. At least one value needed to be checked state while filtering otherwise “Ok” button will be disabled.

![](PivotTable-Field-List_images/filter.png)

![](PivotTable-Field-List_images/filter1.png)
