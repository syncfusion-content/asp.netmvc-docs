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

Based on the datasource, Relational, bound to the PivotGrid control, PivotTable Field List will be automatically populated with Cube Information or Field Names. PivotTable Field List provides an Excel like appearance and behavior.

In-order to initialize PivotTable Field List, first you need to define a “div” tag with an appropriate “id” attribute which acts as a container for the control. Then you need to initialize the PivotTable Field List by using the **"PivotSchemaDesigner"** method.

### Client Mode

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad").RenderSuccess("loadSchemaDesigner")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); rows.FieldName("State").FieldCaption("State").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Add(); values.FieldName("Quantity").Add(); }))
@Html.EJ().Pivot().PivotSchemaDesigner("PivotSchemaDesigner")

<script type="text/javascript">
        function onLoad(args) {
            args.model.dataSource.data = pivot_dataset;//Array of data
        }

        function loadSchemaDesigner(args) {
            $("#PivotSchemaDesigner").ejPivotSchemaDesigner({ pivotControl: this, layout: ej.PivotSchemaDesigner.Layouts.Excel });
            args.model.renderSuccess = null;
        }
</script>


{% endhighlight %}

![](PivotTable-Field-List_images/relationalclientfeildlsit.png)


### Server Mode 

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("/RelationalService")).ClientSideEvents(events => events.AfterServiceInvoke("OnAfterServiceInvoke"))
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

![](PivotTable-Field-List_images/relationalserverside.png)

## Layout

The top portion of the layout shows Field or Cube items in a categorized way. They can be dynamically added into the report either by drag and drop option or through simple check box selection.
 
On item(s) selection they will be placed in Row section by default except numeric based item(s) or measures, which will alone be placed in the Value section by default.

The bottom portion of the layout is segregated as below.

* Report Filter: Exclusively designed to filter an item(s) placed in this particular position of the layout. 
* Value Section: The value label usually displays the numeric value item(s) present in the report.
* Column Section: It is used to display item(s) as column header and values in the PivotGrid control. 
* Row Section: It is used to display item(s) as row header and values in the PivotGrid control.
 
## UI Interactions 

### By Drag and Drop

You can alter the report on fly through drag-and-drop operation. You can drag any item from Field List and drop into column, row, value or filter section available at the bottom of the Field List.

![](PivotTable-Field-List_images/relationaldragndrop.png)

### By Drag and Drop to Grid Headers

You can also drag and drop elements from fieldlist to grid headers.

![](PivotTable-Field-List_images/HeaderDrop.png)

![](PivotTable-Field-List_images/HeaderDrop1.png)

![](PivotTable-Field-List_images/HeaderDrop2.png)

### By Treeview Selection

You can also alter the report on fly through check and uncheck option as an alternate. By default, fields will be added to the Row Axis when checked.

![](PivotTable-Field-List_images/relationalchecknuncheck.png)

 ### By Context Menu
 
You can also alter the report by using context menu.

![](PivotTable-Field-List_images/Pivotbutton_Context.png)

![](PivotTable-Field-List_images/Treeview_Context.png)

## Searching Values
Search option available in Field List allows you to search a specific value that needs to be filtered from the list of values inside the filter pop-up window.

![](PivotTable-Field-List_images/relationalfiltering.png)

![](PivotTable-Field-List_images/relationaldialogsearch.png)

## Filtering
Values can be filtered by checking/unchecking the check box besides them, inside the filter pop-up window. At least one value needed to be checked state while filtering otherwise “Ok” button will be disabled.

![](PivotTable-Field-List_images/relationalfiltering.png)

![](PivotTable-Field-List_images/relationalfitlerdialog.png)


