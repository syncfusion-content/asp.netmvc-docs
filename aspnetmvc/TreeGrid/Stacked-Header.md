---
layout: post
title: Stacked Header | TreeGrid | ASP.NET MVC | Syncfusion
description: stacked header
platform: ejmvc
control: TreeGrid
documentation: ug
---

# Stacked Headers

The stacked headers helps you to group the logical columns in treegrid. It can be shown by setting `ShowStackedHeader` as `true` and by defining `StackedHeaderRows`.

## Adding Stacked header columns

To stack columns in stacked header, you need to define `Column` property in `StackedHeaderColumns` with field names of visible columns.

{% highlight CSHTML %}
     @(Html.EJ().TreeGrid("TreeGridContainer")
                //
	   .Columns(co =>
               {
                   co.Field("ID").HeaderText("S.No").Width(45).Add();
                   co.Field("Name").HeaderText("Shipment Name").Add();
                   co.Field("Category").HeaderText("Category").Add();
                   co.Field("Units").HeaderText("Units").Add();
                   co.Field("UnitPrice").HeaderText("Unit Price($)").Add();
                   co.Field("Price").HeaderText("Price($)").Add();
               }
             )
            .ShowStackedHeader(true)
            .StackedHeaderRows(row => {
                row.StackedHeaderColumns(stack =>
                {
                    stack.HeaderText("Shipment Details").Column(col =>
                    {
                        col.Add("ID");
                        col.Add("Name");
                        col.Add("Category");
                        col.Add("Units");
                    }).Add();
                    stack.HeaderText("Price Details").Column(col =>
                    {
                        col.Add("UnitPrice");
                        col.Add("Price");
                    }).Add();
                }).Add();
            })
        )    

{% endhighlight %}

![](Stacked-header_images/Stacked-Header-img1.png)

## Stacked header column customization

we can customize the stacked header cells with more options as described below.

### CSS Class

You can provide external CSS styles to the stacked header with the help of `CssClass` property.

{% highlight CSHTML %}
     @(Html.EJ().TreeGrid("TreeGridContainer")
                //
	    .ShowStackedHeader(true)
            .StackedHeaderRows(row => {
                row.StackedHeaderColumns(stack =>
                {
                    stack.HeaderText("Shipment Details").Column(col =>
                    {
                        col.Add("ID");
                        col.Add("Name");
                        col.Add("Category");
                        col.Add("Units");
                    }).CssClass("stackhead").Add();
                    stack.HeaderText("Price Details").Column(col =>
                    {
                        col.Add("UnitPrice");
                        col.Add("Price");
                    }).Add();
                }).Add();
            })
        )    
<style>
  .stackhead {
            background-color: #ffb3b3; 
        }
</style>
{% endhighlight %}
![](Stacked-header_images/Stacked-Header-img2.png)

### Text Align

There is an option to align the stacked header text inside the header cell using `TextAlign` property as follows.

{% highlight CSHTML %}
     @(Html.EJ().TreeGrid("TreeGridContainer")
                //		   
            .ShowStackedHeader(true)
            .StackedHeaderRows(row => {
                row.StackedHeaderColumns(stack =>
                {
                    stack.TextAlign(TextAlign.Right).HeaderText("Shipment Details").Column(col =>
                    {
                        col.Add("ID");
                        col.Add("Name");
                        col.Add("Category");
                        col.Add("Units");
                    }).Add();
                    stack.TextAlign(TextAlign.Left).HeaderText("Price Details").Column(col =>
                    {
                        col.Add("UnitPrice");
                        col.Add("Price");
                    }).Add();
                }).Add();
            })
        )    

{% endhighlight %}

![](Stacked-header_images/Stacked-Header-img4.png)

### Tooltip

We can have the customized tooltip for the stacked header text with the help of `ToolTip` property. JsRender template script id can be assigned to this property to get tooltip.

{% highlight CSHTML %}
     @(Html.EJ().TreeGrid("TreeGridContainer")
                //
			.ShowGridCellTooltip(true)             
            .ShowStackedHeader(true)
            .StackedHeaderRows(row => {
                row.StackedHeaderColumns(stack =>
                {
                    stack.HeaderText("Shipment Details").Column(col =>
                    {
                        col.Add("ID");
                        col.Add("Name");
                        col.Add("Category");
                        col.Add("Units");
                    }).Add();
                    stack.HeaderText("Price Details").Column(col =>
                    {
                        col.Add("UnitPrice");
                        col.Add("Price");
                    }).Tooltip("#tooltip").Add();
                }).Add();
            })
        )    

<script id="tooltip" type="text/x-jsrender">
        <div>Custom Tooltip</div>
</script> 

{% endhighlight %}

![](Stacked-header_images/Stacked-Header-img3.png)

N>
To enable stacked header tooltip we need to set `ShowGridCellTooltip` as `true`.

[Click](http://mvc.syncfusion.com/demos/web/treegrid/treegridstackedheader) here to view the demo sample for stacked header.