---
title: Context Menu | FileExplorer | ASP.NET MVC | Syncfusion
description: Context Menu support in FileExplorer 
platform: ejmvc
control: FileExplorer
documentation: UG
keywords: FileExplorer,  Syncfusion, EJ MVC FileExplorer, UG document, Context Menu
---
# Context Menu

The context-menu has [list of items](#context-menu-items) which helps to perform FileExplorer operations, and it appears based on the target such as file or folder.

## Context menu items

The below table shows the context menu items corresponding to the location where it is opened:

<table>
<tr>
<td>
Context menu location
</td>
<td>
Context menu items
</td>
<td>
Screenshot
</td>
</tr>
<tr>
<td>
While right click on tree view nodes (from navigation pane)<br/><br/></td>
<td>
* New folder<br/>* Upload<br/>* Delete<br/>* Rename<br/>* Cut<br/>* Copy<br/>* Paste<br/>*Get info<br/><br/><br/></td>
<td>
<br/><br/><br/><br/></td>
</tr>
<tr>
<td>
While right click on File / Folder<br/><br/></td>
<td>
* Open<br/>* Download<br/>* Upload<br/>* Delete<br/>* Rename<br/>* Cut<br/>* Copy<br/>* Paste<br/>* Get info<br/>*Open folder location<br/><br/><br/><br/></td>
<td>
<br/><br/><br/><br/></td>
</tr>
<tr>
<td>
While right click on layout (content pane)<br/><br/></td>
<td>
* Refresh<br/>* Paste<br/>* Sort by<br/>* New folder<br/>* Upload <br/>* Get info <br/><br/><br/><br/></td>
<td>
<br/><br/><br/><br/></td>
</tr>
</table>
The below table explains the behavior of each context menu item:
<table>
<tr>
<td>
Open<br/><br/></td>
<td>
It opens the selected folder. When an image file selected it opens the preview of the image. For the remaining files this option becomes disabled.<br/><br/></td>
</tr>
<tr>
<td>
Download<br/><br/></td>
<td>
It downloads the selected file. When a file or number of files selected at that time only download option enabled.<br/><br/>If multiple files selected then it downloads all the files in a zip format.<br/><br/></td>
</tr>
<tr>
<td>
Cut<br/><br/></td>
<td>
It makes the copy of the selected files or folders into the clipboard. When the user paste the files in any location, the files are removed from the source location.<br/><br/></td>
</tr>
<tr>
<td>
Copy<br/><br/></td>
<td>
It makes the copy of the selected files or folders into the clipboard. When the user paste the files, the copy of the files only pasted in the target location.<br/><br/></td>
</tr>
<tr>
<td>
Paste<br/><br/></td>
<td>
It paste the files from the clipboard into the current selected folder. Note that when the files are copied into the clipboard at that time only it enabled.<br/><br/></td>
</tr>
<tr>
<td>
Delete<br/><br/></td>
<td>
It deletes the current selected file or folder. When you select any file or folder at that time only this option gets enabled.<br/><br/>If multiple files selected then it deletes all the selected items.<br/><br/></td>
</tr>
<tr>
<td>
Rename<br/><br/></td>
<td>
This is used to rename the current selected file or folder. When you select any file or folder at that time only this option gets enabled.<br/><br/>Even multiple files selected it renames the single file only.<br/><br/></td>
</tr>
<tr>
<td>
New Folder<br/><br/></td>
<td>
It creates a new folder on the current directory.<br/><br/>While click on the “NewFolder” item a dialog appears to get the folder name. Based on the user input, a new folder create on the current directory.<br/><br/></td>
</tr>
<tr>
<td>
Upload<br/><br/></td>
<td>
It uploads a file or list of files into the current directory.<br/><br/></td>
</tr>
<tr>
<td>
Get info<br/><br/></td>
<td>
It displays the details of the current selected file or folder.<br/><br/></td>
</tr>
<tr>
<td>
Sort By<br/><br/></td><td>
It's used to sorting the files and folders from the current directory.The sorting can be done based on the columns available from grid,in both ascending and descending order.<br/><br/></td>
</tr>
<tr>
<td>
Open folder location
</td>
<td>
It helps to open a file location from the filtered list.
</td>
</tr>
</table>

## Context menu Visibility

The presence of the context menu can be controlled by the “[ShowContextMenu](http://help.syncfusion.com/js/api/ejfileexplorer#members:showcontextmenu)” property. This was enabled by default, and by disabling this property you can prevent our built-in context menu.

In the view page, add FileExplorer helper and specify the context menu visibility as false.
    
{% highlight razor %}
    
    @(Html.EJ().FileExplorer("fileExplorer")
        .Path("~/FileExplorerContent/")
        .AjaxAction(@Url.Content("FileActionDefault"))
        .ShowContextMenu(false)
    )
        
{% endhighlight %}
    
## Enable / Disable the Context menu Item

The context menu items can be enabled or disabled through the client side public methods. It enables or disables the item from all the context menu where it is present.

For example, if you disable the “Upload” item, it disables in all places wherever it appears such as open the context menu on “TreeView”, open on file/folder, and open on layout.

* [enableMenuItem](http://help.syncfusion.com/js/api/ejfileexplorer#methods:enablemenuitem)

* [disableMenuItem](http://help.syncfusion.com/js/api/ejfileexplorer#methods:disablemenuitem)

These methods only accepts the context menu item name as the parameter.
    
    {% highlight javascript %}
    
            $(function () {
                var fileExpObj = $("#fileExplorer").data("ejFileExplorer");
                // this disables the New Folder item
                fileExpObj.disableMenuItem("New folder");
                // this disables the Download item
                fileExpObj.disableMenuItem("Download");
            });
            
    {% endhighlight %}


## Context Menu Customization

You can customize the ContextMenu of FileExplorer control by using [ContextMenuSettings](https://help.syncfusion.com/api/js/ejfileexplorer#members:contextmenusettings) property. 

You can add your own context menu items and its action along with default context menu items of FileExplorer control. You can also remove the default context menu items in FileExplorer control. 

To add/remove/re-arrange context menu items, you need to use [ContextMenuSettings.items](https://help.syncfusion.com/api/js/ejfileexplorer#members:contextmenusettings-items) property and to bind required actions for newly added menu items and add sub menu items, use [ContextMenuSettings.CustomMenuFields](https://help.syncfusion.com/api/js/ejfileexplorer#members:contextmenusettings-custommenufields) property. 

Add the following code example to the corresponding controller page.

{% highlight c# %}

public ActionResult FileActionContextMenu(FileExplorerParams args)
{
    FileExplorerOperations opeartion = new FileExplorerOperations();
    switch (args.ActionType)
    {
        case "Read":
            return Json(opeartion.Read(args.Path, args.ExtensionsAllow));
        case "CreateFolder":
            return Json(opeartion.CreateFolder(args.Path, args.Name));
        case "Paste":
            return Json(opeartion.Paste(args.LocationFrom, args.LocationTo, args.Names, args.Action, args.CommonFiles));
        case "Remove":
            return Json(opeartion.Remove(args.Names, args.Path));
        case "Rename":
            return Json(opeartion.Rename(args.Path, args.Name, args.NewName, args.CommonFiles));
        case "GetDetails":
            return Json(opeartion.GetDetails(args.Path, args.Names));
        case "Download":
            opeartion.Download(args.Path, args.Names);
            break;
        case "Upload":
            opeartion.Upload(args.FileUpload, args.Path);
            break;
        case "Search":
            return Json(opeartion.Search(args.Path, args.ExtensionsAllow, args.SearchString, args.CaseSensitive));
    }
    return Json("");
}

{% endhighlight %}

In the view page, add FileExplorer helper and specify the **ContextMenuSettings** property.

{% highlight razor %}

@* removed the "NewFolder" item from NavigationPane ContextMenu *@
@{List<String> navbar = new List<string>() { "Upload", "|", "Delete", "Rename", "|", "Cut", "Copy", "Paste", "|", "Getinfo" }; }
@* added the custom ContextMenu item (View) to Current working directory ContextMenu *@
@{List<String> cwd = new List<string>() { "Refresh", "Paste", "|", "SortBy", "View", "|", "NewFolder", "Upload", "|", "Getinfo" };}
@* removed "Upload" item from Selected files/ folder's ContextMenu *@
@{List<String> files = new List<string>() { "Open", "Download", "|", "Delete", "Rename", "|", "Cut", "Copy", "Paste", "|", 
        "OpenFolderLocation", "Getinfo" }; }


@Html.EJ().FileExplorer("fileExplorer").Path("~/FileExplorerContent/").ContextMenuSettings(
    settings => settings.Items(
        item => item.Navbar(navbar).Cwd(cwd).Files(files)
    ).CustomMenuFields(fields =>
    {
        fields.Add().Id("View").Text("View by").SpriteCssClass("custom-grid").Child(child =>
        {
            child.Add().Id("tile").Text("Tile view").Action("onLayout");
            child.Add().Id("grid").Text("Grid view").Action("onLayout");
            child.Add().Id("largeicons").Text("Large icons view").Action("onLayout");
        });
    })
    ).AjaxAction(@Url.Content("FileActionContextMenu")).ClientSideEvents(
    e => e.MenuOpen("onMenuOpen").LayoutChange("onLayoutChange")
).Width("100%").IsResponsive(true).MinWidth("150px")

{% endhighlight %}

Icons of context menu items can be customized by overriding the default context menu item style. The following code example illustrates how to customize the icon of context menu items.

{% highlight css %}

<style>
    .fe-context-menu .custom-grid:before {
        content: "\e7b9";
    }

    .fe-context-menu .custom-largeicons:before {
        content: "\e7bb";
    }

    .fe-context-menu .custom-tile:before {
        content: "\e7be";
    }
</style>

{% endhighlight %}

The following screenshot displays the customization of context menu in FileExplorer control.

![](Context-Menu_images/Context-Menu_img1.png)

## Context Menu Events

You would be notified with events when you try to open the context menu items (**MenuBeforeOpen**), after context menu items is opened (**MenuOpen**) and when you click the menu items (**MenuClick**). The following code example illustrates how to define those events.

{% highlight razor %}

@Html.EJ().FileExplorer("fileExplorer").Path("~/FileExplorerContent/").AjaxAction(@Url.Content("FileActionContextMenu")).ClientSideEvents(e => e.MenuBeforeOpen("menuBeforeOpen").MenuOpen("menuOpen").MenuClick("menuClick"))

{% endhighlight %}

{% highlight js %}

function menuBeforeOpen(args) {
    //you add/remove the context menu items in run time
    //do your custom action here.
    args.dataSource.pop();
}
function menuOpen(args) {
    //you can also idendify which context menu is opened by 
    if (args.contextMenu == "cwd") {
        //do your custom action here.
    }
}
function menuClick(args) {
    switch (args.text) {
        case "largeicons":
            //do your custom action here.
            break;
    }
}

{% endhighlight %}
