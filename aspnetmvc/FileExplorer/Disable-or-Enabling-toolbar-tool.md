---
layout: post
title: Disable-or-Enabling-toolbar-tool
description: disable or enabling toolbar tool
platform: ejmvc
control: FileExplorer
documentation: ug
---

# Disable or Enabling toolbar tool

In Toolbar, you can disable or enable the tools as per your requirement. For example when you want to disable the Add a new folder tool, you can achieve it using the following code.

1. To render FileExplorer in MVC with the Toolbar Tool Disabled option, include the following code in your View page.


   ~~~ js
	
		@Html.EJ().FileExplorer("fileExplorer").Path("~/FileExplorerContent/").AjaxAction(@Url.Content("FileActionDefault")).Layout(LayoutType.Tile)

   ~~~
	{:.prettyprint }
	
	In your script section please add following code to disable toolbar tool.

   ~~~ js
	
		<script>

			$(function () {          

				obj = $("#fileExplorer").data("ejFileExplorer");

				obj.disableToolbarItem("fileExplorerNewFolder");

			});
		
		</script>
	
   ~~~
   {:.prettyprint }
   
   There is no change in the controller part, it is the same controller part used as mentioned above.
   
   ![](Disable-or-Enabling-toolbar-tool_images/Disable-or-Enabling-toolbar-tool_img1.png)

   _Figure 12: In FileExplorer, adding new folder icon is in disabled state_

