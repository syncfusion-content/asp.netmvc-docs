---
layout: post
title: Zoom and Print related operation in RichTextEditor widget for Syncfusion Essential ASP.NET MVC
description: Working with zoom and printrelated changes in RichTextEditor widget
platform: ASP.NET MVC
control: RTE
documentation: ug
keywords: RichTextEditor, Zoom, Print 
---

# Zoom

The editor provides zoom tools which enlarges the view of an editor's object enabling you to see more detail. You can continuous zoomIn and zoomOut either using zoom tools or keyboard.

You can assign Increases and decreases of zooming range using [zoomStep](http://help.syncfusion.com/js/api/ejrte#members:zoomStep) property

{% highlight html %}
  
@{
    List<String> toolsList = new List<string>() { "view" };
    List<String> view = new List<string>() { "zoomIn","zoomOut" };
}
@{Html.EJ().RTE("rteSample").Width("800px").ZoomStep("0.05").ContentTemplate(@<div>
    The Rich Text Editor
    (RTE) control is an easy to render in client side. Customer easy to edit the contents
    and get the HTML content for the displayed content. A rich text editor control provides
    users with a toolbar that helps them to apply rich text formats to the text entered
    in the text area.
</div>)
.ToolsList(toolsList)
.Tools(tool => tool.View(view))
.Render();}
<br />

{% endhighlight %}

![](ZoomandPrint_images/zoom.png)

# Print

The editor provides print tools which use to print the contents of the editor.


{% highlight html %}

@{
    List<String> toolsList = new List<string>() { "print" };
    List<String> print = new List<string>() { "print" };
}
@{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
    The Rich Text Editor
    (RTE) control is an easy to render in client side. Customer easy to edit the contents
    and get the HTML content for the displayed content. A rich text editor control provides
    users with a toolbar that helps them to apply rich text formats to the text entered
    in the text area.
</div>)
.ToolsList(toolsList)
.Tools(tool => tool.Print(print))
.Render();}
<br />

{% endhighlight %}

![](ZoomandPrint_images/print.png)

