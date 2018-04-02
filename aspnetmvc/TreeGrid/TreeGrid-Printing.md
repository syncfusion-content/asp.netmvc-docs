---
layout: post
title: Printing | TreeGrid | ASP.NET MVC | Syncfusion
description: printing
platform: ejmvc
control: TreeGrid
documentation: ug
---

# TreeGrid Printing

TreeGrid provides support to print the contents. To print the TreeGrid the print toolbar item must be added to [ToolbarSettings.ToolbarItems](/api/js/ejgantt#members:toolbarsettings-toolbaritems) property. The below code example shows how to enable print in TreeGrid.

{% highlight CSHTML %}
 
@(Html.EJ().TreeGrid("TreeGrid")
    .ToolbarSettings(tool => {
        tool.ShowToolbar(true);
        tool.ToolbarItems(new List<TreeGridToolBarItems>(){
            TreeGridToolBarItems.Print        
        });        
    })
    )

{% endhighlight %}

The print preview window will be opened by clicking on this toolbar icon. 

## Print Mode

It is possible to set the printMode in `PageSettings` property, to give printing preference, as to print current page alone or all the pages in case of paging enabled in TreeGrid. The following code example explains this.


{% highlight CSHTML %}
 
 @(Html.EJ().TreeGrid("TreeGrid")
    .AllowPaging(true)
    .PageSettings(pg=>pg.PrintMode(TreeGridPrintMode.CurrentPage))
    .ToolbarSettings(tool => {
        tool.ShowToolbar(true);
        tool.ToolbarItems(new List<TreeGridToolBarItems>(){
            TreeGridToolBarItems.Print        
        });        
    })
    )

{% endhighlight %}

In this case only the visible records in the current page will be send to printing.

## BeforePrint Event 

`BeforePrint` event will be triggered once after printing initiated in TreeGrid. This event contains the treegrid element which is going to be printing. The following code explains this.

{% highlight js %}
 
@(Html.EJ().TreeGrid("TreeGrid")
    .ClientSideEvents(cl => {
        cl.BeforePrint("beforePrint");
    })
    .ToolbarSettings(tool => {
        tool.ShowToolbar(true);
        tool.ToolbarItems(new List < TreeGridToolBarItems > () {
            TreeGridToolBarItems.Print
        });
    })
)
<script>
    function beforePrint(args) {
        //will be triggered before printing the TreeGrid
    }
</script>

{% endhighlight %}

[Click](https://mvc.syncfusion.com/demos/web/treegrid/treegridselfreference) here to view the online demo sample Printing.