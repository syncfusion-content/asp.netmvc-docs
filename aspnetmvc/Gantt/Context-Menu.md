---
layout: post
title: Context Menu | Gantt | ASP.NET MVC | Syncfusion
description: context menu
platform: ejmvc
control: Gantt
documentation: ug
---

# Context Menu

## Default Context Menu

The default context menu contains the following options.

* Task Details
* Add New Task
* Indent
* Outdent
* Delete

The following code example shows you how to enable the default context menu in Gantt control.


{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")


 .EnableContextMenu(true)

 .Datasource(ViewBag.datasource)

 )

{% endhighlight %}


The following screenshot shows the Default Context Menu in Gantt control.



![](Context-Menu_images/Context-Menu_img1.png)

Default Context Menu
{:.caption}

## Custom Context Menu

You can add custom context menu option in Gantt control. The following code example shows you how to add the custom context menu option in Gantt control.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")


 .EnableContextMenu(true)

 .ClientSideEvents(options =>

 {

     options.ContextMenuOpen("contextMenuOpen");

 })

 .Datasource(ViewBag.datasource)

 )


@section ScriptSection{

   <script type="text/javascript">

       function contextMenuOpen(args) {

           args.contextMenuItems.push(

               {

                   headerText: "ExpandAll",

                   iconPath: "url(../images/Expand All.png)",

                   evenHandler: function () {

                       //event handler for custom menu items

                   }

               });
       }

     </script>


{% endhighlight %}



The screenshot of the Custom Context Menu items in Gantt control is as follows.


![](Context-Menu_images/Context-Menu_img2.png)

Custom Context Menu
{:.caption}
