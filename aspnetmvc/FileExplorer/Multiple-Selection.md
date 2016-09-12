---
title: Multiple Selection | FileExplorer | ASP.NET MVC | Syncfusion
description: Multi selection support in FileExplorer
platform: ejmvc
control: FileExplorer
documentation: UG
keywords: FileExplorer,  Syncfusion, EJ MVC FileExplorer, UG document, Multiple selection
---
# Multiple Selection

The FileExplorer allows the user to select multiple files by enabling the “[AllowMultiSelection](http://help.syncfusion.com/js/api/ejfileexplorer#members:allowmultiselection)” property. The multiple selection can be done by pressing the “**Ctrl”** key or “**Shift”** key. You can select all the files in the directory by pressing “**Ctrl + A**”. The multiple selection is useful on copy pasting multiple files, deleting multiple files and downloading multiple files.

In the view page, add FileExplorer helper and specify the multi selection as true
    
    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))        
            .AllowMultiSelection(false)
        )
        
    {% endhighlight %}
    
## Checkbox option

You can enable or disable the checkbox using “ShowCheckbox” API of FileExplorer

In the view page, add FileExplorer helper and disable the checkbox as shown below

    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))        
            .ShowCheckbox(false)
        )
        
    {% endhighlight %}

