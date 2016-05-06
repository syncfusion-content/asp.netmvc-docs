---
title: Resizing | FileExplorer | ASP.NET MVC | Syncfusion
description: Resize option in FileExplorer
platform: ASP.NET MVC
control: FileExplorer
documentation: UG
keywords: FileExplorer,  Syncfusion, EJ MVC FileExplorer, UG document, Resizing
---
# Resizing

The FileExplorer has the resize support through the resize handle which appears at right-bottom corner of footer. By clicking the resize handle the user can resize the FileExplorer through the UI. While resizing the dimension of the FileExplorer is automatically adjusted.

The resize behavior can be enabled through the “[EnableResize](http://help.syncfusion.com/js/api/ejfileexplorer#members:enableresize)” property.

In the view page, add FileExplorer helper with resizable option as shown below
    
    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            // it enables the resize functionality
            // and a resize handle added in the Footer element
            .EnableResize(true)
        )
        
    {% endhighlight %}
    
## Responsiveness

By enabling the “[IsResponsive](http://help.syncfusion.com/js/api/ejfileexplorer#members:isresponsive)” property, you can make the FileExplorer as responsive. While resizing the FileExplorer component, the inner content and toolbar items are automatically adjusted to equalize the size. The toolbar items are displayed within Dropdown on enabling the responsive. Otherwise it floated to the next line to equalize the space.

In the view page, add FileExplorer helper with responsive option
    
    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            // it enables the resize functionality
            // and a resize handle added in the Footer element
            .EnableResize(true)
            // it enables the control responsiveness
            .IsResponsive(true)
        )
        
    {% endhighlight %}
    
## Restriction on Resize

You can restrict the dimension of the FileExplorer by setting the “[MinHeight](http://help.syncfusion.com/js/api/ejfileexplorer#members:minheight)”, “[MaxHeight](http://help.syncfusion.com/js/api/ejfileexplorer#members:maxheight)”,  “[MinWidth](http://help.syncfusion.com/js/api/ejfileexplorer#members:minwidth)” and “[MaxWidth](http://help.syncfusion.com/js/api/ejfileexplorer#members:maxwidth)” properties while resizing the FileExplorer.

In the view page, add FileExplorer helper and set resize option within particular region.
    
    {% highlight razor %}
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            .EnableResize(true)
            .IsResponsive(true)
            // restricts the dimensions for height and width
            .MinHeight("200px")
            .MaxHeight("400px")
            .MinWidth("300px")
            .MaxWidth("1200px")
        )
    {% endhighlight %}
    
