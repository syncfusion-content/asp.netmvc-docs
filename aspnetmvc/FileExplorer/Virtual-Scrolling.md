---
title: Virtual Scrolling | FileExplorer | ASP.NET MVC | Syncfusion
description: Virtual Scrolling support in FileExplorer control
platform: ejmvc
control: FileExplorer
documentation: UG
keywords: FileExplorer,  Syncfusion, EJ MVC FileExplorer, UG document, Virtual Scrolling
---

# Virtual Scrolling

Virtual Scrolling is introduced to provide support for loading files and folders on demand in order to improve performance in FileExplorer when large amount of files are present.

Virtual Scrolling can be enabled by using [VirtualItemCount](https://help.syncfusion.com/api/js/ejfileexplorer#members:virtualitemcount) API. It specifies the total files to be loaded initially, and on each scroll the next set of files are loaded. For eg- If [VirtualItemCount](https://help.syncfusion.com/api/js/ejfileexplorer#members:virtualitemcount) value is given as ”20”, then 20 items are loaded initially and on each scroll the next/previous 20 items are loaded. If the value of [VirtualItemCount](https://help.syncfusion.com/api/js/ejfileexplorer#members:virtualitemcount) is 0, virtual scrolling will be disabled.

N>  Default value of `VirtualItemCount` is 0.


{% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))        
            .VirtualItemCount(40)
        )

{% endhighlight %}

