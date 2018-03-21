---
layout: post
title: Context Menu | Gantt | ASP.NET MVC | Syncfusion
description: context menu
platform: ejmvc
control: Gantt
documentation: ug
---

# Context Menu

## Default Menu Items

Context menu in Gantt has the following default menu items.

* Task Details
* Add New Task
* Indent
* Outdent
* Delete

Context menu in Gantt can be enabled by using `EnableContextMenu` property.
The following code example explains how to enable the context menu in Gantt control.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
  //.
 .EnableContextMenu(true)
 )@(Html.EJ().ScriptManager())

{% endhighlight %}

The following screenshot shows the default context menu in Gantt control.

![](Context-Menu_images/Context-Menu_img1.png)

## Custom Menu Item

It is possible to add a custom context menu item in Gantt control by using `ContextMenuOpen` event. The following code example explains on how to add the custom context menu item.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
  //..
 .EnableContextMenu(true)
 .ClientSideEvents(eve=>
		  {
				  eve.ContextMenuOpen("contextMenuOpen");
		  })
 )@(Html.EJ().ScriptManager()) 
<script type="text/javascript">
     function contextMenuOpen(args) {
            args.contextMenuItems.push({
                headerText: "Expand/Collapse",
                menuId: "expand",
                iconPath: "url(Expand-02-WF.png)",
                eventHandler: function () {
                    //event handler for custom menu items
                }
            })
        }
</script>

{% endhighlight %}

The screenshot of the custom context menu items in Gantt control is as follows.

![](Context-Menu_images/Context-Menu_img2.png)

### Custom menu item with sub menu item

It is possible to create a custom menu item with a sub menu, by mapping the parentMenuId property from the contextMenuItems argument in the `ContextMenuOpen` event.

The following code example explains on how to add sub context menu for custom menu items.

{% highlight CSHTML %}

@(Html.EJ().Gantt("Gantt")
  //..
 .EnableContextMenu(true)
 .ClientSideEvents(eve=>
		  {
				  eve.ContextMenuOpen("contextMenuOpen");
		  })
 )@(Html.EJ().ScriptManager()) 
 <script type="text/javascript">
           args.contextMenuItems.push({
                headerText: "Expand/Collapse",
                menuId: "expand",
                iconPath: "url(Navigation-Up-02-WF.png)",
                eventHandler: function () {
                    //event handler for custom menu items
                }
            });

            args.contextMenuItems.push({
                headerText: "ExpandAll",
                menuId: "expandAll",
                parentMenuId: "expand",
                iconPath: "url(Expand-02-WF.png)",
                eventHandler: function () {
                    //event handler for custom menu items
                }
            });

            args.contextMenuItems.push({
                headerText: "CollapseAll",
                menuId: "collapseAll",
                parentMenuId: "expand",
                iconPath: "url(shrink2.png)",
                eventHandler: function () {
                    //event handler for custom menu items
                }
            });
	}
</script>

{% endhighlight %}

The screenshot of the custom context menu items in Gantt control is as follows.

![](Context-Menu_images/Context-Menu_img3.png)

[Click](https://mvc.syncfusion.com/demos/web/gantt/ganttcontextmenu) here to view the online demo sample for custom context menu in Gantt.
