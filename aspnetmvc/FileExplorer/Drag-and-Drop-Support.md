---
title: Drag and Drop Support | FileExplorer | ASP.NET MVC | Syncfusion
description: Drag and Drop option in FileExplorer
platform: ejmvc
control: FileExplorer
documentation: UG
keywords: Drag and drop option
---

# Drag and Drop Support

The FileExplorer allows files to be moved from one folder to another by using drag and drop. It also supports uploading a file by dragging it from Windows Explorer to a folder in the FileExplorer control.

You can enable or disable this support by using “**AllowDragAndDrop**” API of FileExplorer.

The [dragStart](https://help.syncfusion.com/api/js/ejfileexplorer#events:dragstart), [drag](https://help.syncfusion.com/api/js/ejfileexplorer#events:drag), [dragStop](https://help.syncfusion.com/api/js/ejfileexplorer#events:dragstop) and [drop](https://help.syncfusion.com/api/js/ejfileexplorer#events:drop) events occur in the mentioned order when a drag and drop operation is performed.

In the view page, add “FileExplorer” helper and specify the drag and drop option as specified below.


    {% highlight razor %}

    @(Html.EJ().FileExplorer("fileExplorer")
            .Layout(LayoutType.Tile)
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileAction"))
            .AllowDragAndDrop(true)
    )

    {% endhighlight %}

