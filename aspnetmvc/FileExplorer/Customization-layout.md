---
layout: post
title: Customization layout | FileExplorer | ASP.NET MVC | Syncfusion
description: customization layout 
platform: ejmvc
control: FileExplorer
documentation: ug
---

# Customization layout 

You can easily customize the layout of the FileExplorer control, show or hide the sub control parts in FileExplorer as per your requirement. For example: show/ hide toolbar, tree view, layout, footer part.

1. To render FileExplorer in MVC with above customizing options, include the following code in your View page.


   ~~~ cshtml
	
	 @Html.EJ().FileExplorer("fileExplorer").Path("~/FileExplorerContent/").AjaxAction(@Url.Content("FileActionDefault")).ShowToolbar(false)

   ~~~
   

    There is no change in the controller part, the same controller part is used as mentioned above.

    
	![](Customization-layout_images/Customization-layout_img1.png)
    
	FileExplorer with toolbar disabled
    {:.caption}

2. To render FileExplorer in MVC with disable tree view and footer options, include the following code in your View page.


   ~~~ cshtml
	
    @Html.EJ().FileExplorer("fileExplorer").Path("~/FileExplorerContent/").AjaxAction(@Url.Content("FileActionDefault")).ShowTreeview(false).ShowFooter(false).Layout(LayoutType.Tile)

   ~~~
	

    There is no change in the controller part, the same controller part is used as mentioned above.

    ![](Customization-layout_images/Customization-layout_img2.png)

    FileExplorer with tree view and footer disabled
    {:.caption}
