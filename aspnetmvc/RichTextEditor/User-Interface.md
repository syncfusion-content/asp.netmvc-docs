---
layout: post
title: User Interface for the RichTextEditor widget for Syncfusion Essential ASP.NET MVC
description: User Interface for RichTextEditor widget (toolbar, content area, and footer)
platform: ASP.NET MVC
control: RTE
documentation: ug

---
# User Interface

The editor user interface (UI) is designed with the toolbar, content area (iframe), and footer elements.

## Toolbar

The editor’s toolbar contains buttons and dropdowns that help you to format your content.

### Toolbar Items

The following table lists the available buttons and dropdowns on the toolbar:

<table>
    <tr>
        <td colspan=1 rowspan=1>
        Name<br/></td><td colspan=1 rowspan=1>
        Summary<br/></td><td colspan=1 rowspan=1>
        Initialization<br/></td><td colspan=1 rowspan=1>
        isDefault?<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Font <br/></td><td colspan=1 rowspan=1>
        Applies font type, size, and color to the content<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() { " font"};<br/>List<String> font = new List<string>() { "fontName", "fontSize", "fontColor", "backgroundColor" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool. Font(font)).Render();}<br/></td><td colspan=1 rowspan=1>
        No<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Font style<br/></td><td colspan=1 rowspan=1>
        Applies bold, italic, underline, and strikethrough formatting to the content<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() { " style"};<br/>List<String> style = new List<string>() { "bold", "italic", "underline", "strikethrough" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool. Styles(style)).Render();}<br/></td><td colspan=1 rowspan=1>
        yes<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Alignment<br/></td><td colspan=1 rowspan=1>
        Align the content with left, center, and right margin.<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() { " alignment"};<br/>List<String> alignment = new List<string>() { "justifyLeft", "justifyCenter" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool. Alignment (alignment)).Render();}<br/></td><td colspan=1 rowspan=1>
        yes<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        List<br/></td><td colspan=1 rowspan=1>
        Create a new list item (bulleted/numbered).<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() { "lists"};<br/>List<String> lists = new List<string>() { "unorderedList", "orderedList" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool. Lists(lists)).Render();}<br/></td><td colspan=1 rowspan=1>
        yes<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Indents<br/></td><td colspan=1 rowspan=1>
        Allows to increase/decrease the indent level of the content.<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() { "indenting"};<br/>List<String> indenting = new List<string> { "outdent", "indent" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool. Indenting(indenting)).Render();}<br/></td><td colspan=1 rowspan=1>
        yes<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Undo/Redo Action<br/></td><td colspan=1 rowspan=1>
        Allows to undo/redo the actions<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() {"doAction"};<br/>List<String> doAction = new List<string>() { "undo", "redo" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool. DoAction (doAction)).Render();}<br/></td><td colspan=1 rowspan=1>
        yes<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Hyperlink<br/></td><td colspan=1 rowspan=1>
        Creates a hyperlink to a text or image to a specific location in the content.<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() {"links"};<br/>List<String> links = new List<string>() { "createLink", "removeLink" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool. Links (links)).Render();}<br/></td><td colspan=1 rowspan=1>
        yes<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Images<br/></td><td colspan=1 rowspan=1>
        Inserts an image from an online source or local computer.<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() {"images"};<br/>List<String> images = new List<string>() { "image" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool. Images (images)).Render();}<br/></td><td colspan=1 rowspan=1>
        yes<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Media<br/></td><td colspan=1 rowspan=1>
        Allows to embed a video into the document.<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() {"media"};<br/>List<String> media = new List<string>() { "video" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool.Media (media)).Render();}<br/></td><td colspan=1 rowspan=1>
        yes<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Table<br/></td><td colspan=1 rowspan=1>
        Allows to add or modify Tables<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() {"tables"};<br/>List<String> tables = new List<string>() { "createTable", "addRowAbove", "addRowBelow", "addColumnLeft", "addColumnRight", "deleteRow", "deleteColumn", "deleteTable" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool. Tables(tables)).Render();}<br/></td><td colspan=1 rowspan=1>
        yes<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Casing<br/></td><td colspan=1 rowspan=1>
        Change the case of selected text in the content<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() {"casing"};<br/>List<String> casing = new List<string>() { "upperCase", "lowerCase" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool. Casing(casing)).Render();}<br/></td><td colspan=1 rowspan=1>
        no<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Scripts<br/></td><td colspan=1 rowspan=1>
        Makes the selected text as superscript (higher) or subscript (lower).<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() {"effects"};<br/>List<String> effects = new List<string>() { "superscript", "subscript" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool. Effects(effects)).Render();}<br/></td><td colspan=1 rowspan=1>
        no<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Format<br/></td><td colspan=1 rowspan=1>
        Clears the formatting options like bold, italic, underline and more.<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() {"formatStyle"};<br/>List<String> formatStyle = new List<string>() { "format" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool.FormatStyle(formatStyle)).Render();}<br/></td><td colspan=1 rowspan=1>
        yes<br/></td></tr>
    <tr>
        <td colspan=1 rowspan=1>
        Clipboard Actions<br/></td><td colspan=1 rowspan=1>
        Controls the clipboard actions by applying specific action on the selected content.<br/></td><td colspan=1 rowspan=1>
        List<String> toolsList = new List<string>() {"clipboard"};<br/>List<String> clipboard = new List<string>() { "cut", "copy", "paste" };<br/>@{Html.EJ().RTE("rteSample"). .ToolsList(toolsList).Tools(tool => tool.Clipboard(clipboard)).Render();}<br/></td><td colspan=1 rowspan=1>
        no<br/></td></tr>
</table>

### Customize Toolbar

You can customize and rearrange items (buttons and dropdowns) by adding, removing, and enabling/disabling on the editor’s toolbar. 

#### Rearrange Group

The toolbar contains groups, which are similar or related functionalities of toolbar items for efficient access. By default, the groups are arranged using the following order:

{% highlight html %}

    List<String> toolsList = new List<string>() { "formatStyle", "font", "style", "effects", "alignment", "lists", "indenting", "clipboard", "doAction", "clear", "links", "images", "media", "tables", "casing", "customTool","view" };
	
{% endhighlight %}

The group can be rearranged on customization using the ToolsList property.

{% highlight html %}

 
    @{
        List<String> toolsList = new List<string>() { "style", "lists", "doAction", "links", "images" };
        List<String> style = new List<string>() { "bold", "italic", "underline", "strikethrough" };
        List<String> lists = new List<string>() { "unorderedList", "orderedList" };
        List<String> doAction = new List<string>() { "undo", "redo" };
        List<String> links = new List<string>() { "createLink" };
        List<String> images = new List<string>() { "image" };

    }
    @{Html.EJ().RTE("rteSample").Width("100%").ContentTemplate(@<p>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </p>)
        .ShowFooter(true)
        .ToolsList(toolsList)
        .Tools(tool => tool.Links(links).Images(images).Styles(style).Lists(lists).DoAction(doAction)).Render();}
  

{% endhighlight %}

N> If you are not specifying any group in **ToolsList** property, the editor will create the toolbar with default group.

#### Add Toolbar item

The editor’s toolbar can be extended through the **CustomTools** option, which renders the custom toolbar items along with the built-in toolbar items. 

{% highlight html %}
   
    @{
        List<String> toolsList = new List<string>() { "customTools" };
    }

    @{Html.EJ().RTE("rteSample").Width("100%").ContentTemplate(@<p>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </p>).ShowFooter(true).ToolsList(toolsList).Tools(tool => tool.CustomTools(customTools => customTools.Text("insertcode").Tooltip("Insert code snippets").Css("e-rte-toolbar-icon insertcode").Action("Onclick").Add())).Render();}

    <script>
        function Onclick() {
            var rte = $("#rteSample").data("ejRTE");
            // handle the execute action on click the custom tool
        }
    </script>

{% endhighlight %}

Define the CSS that will be applied to the custom tool.

{% highlight html %}

    <style>
        .e-rte-toolbar-icon.insertcode::before  {
            content: "\e780";
            font-size: 18px;
            margin: 3px;
        }
    </style>

{% endhighlight %}

N> The CSS class that defined for custom tool is directly applies to the newly added toolbar item. 

#### Remove Toolbar item

To remove a particular toolbar item, pass the id of a toolbar item to the [removeToolbarItem](http://help.syncfusion.com/js/api/ejrte#methods:removetoolbaritem) method.

{% highlight html %}


    @{
        List<String> toolsList = new List<string>() { "formatStyle", "font", "style", "effects", "alignment", "lists", "indenting", "clipboard", "doAction", "clear", "links", "images", "media" };
        List<String> font = new List<string>() { "fontName", "fontSize", "fontColor", "backgroundColor" };
        List<String> style = new List<string>() { "bold", "italic", "underline", "strikethrough" };
        List<String> alignment = new List<string>() { "justifyLeft", "justifyCenter" };
        List<String> lists = new List<string>() { "unorderedList", "orderedList" };
        List<String> indenting = new List<string> { "outdent", "indent" };
        List<String> clipboard = new List<string>() { "cut", "copy", "paste" };
        List<String> doAction = new List<string>() { "undo", "redo" };
        List<String> clear = new List<string>() { "clearFormat", "clearAll" };
        List<String> tables = new List<string>() { "createTable", "addRowAbove", "addRowBelow", "addColumnLeft", "addColumnRight", "deleteRow", "deleteColumn", "deleteTable" };
        List<String> links = new List<string>() { "createLink", "removeLink" };
        List<String> images = new List<string>() { "image" };
        List<String> media = new List<string>() { "video" };
    }

    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
    .ToolsList(toolsList)
    .Tools(tool => tool.Clear(clear).Tables(tables).Links(links).Images(images).Font(font).Styles(style).Media(media).Alignment(alignment).Lists(lists).Clipboard(clipboard).DoAction(doAction).Indenting(indenting))
    .ClientSideEvents(e => e.Create("Onclick"))
    .Render();}
    
    <script>
        function Onclick() {
            var rte = $("#rteSample").data("ejRTE");
            rte.removeToolbarItem("video");
        }
    </script>
    
{% endhighlight %}

N> This method completely removes the DOM element along with the events bounded to it.

#### Enable/Disable Toolbar item

The state of each toolbar item can be controlled by calling the client-side methods such as [enableToolbarItem](http://help.syncfusion.com/js/api/ejrte#methods:enabletoolbaritem) and [disableToolbatItem](http://help.syncfusion.com/js/api/ejrte#methods:disabletoolbaritem).

{% highlight js %}

    function Onclick() {
            var rte = $("#rteSample").data("ejRTE");
            rte.disableToolbarItem("video");
        }

{% endhighlight %}

{% highlight js %}

    function Onclick() {
            var rte = $("#rteSample").data("ejRTE");
            rte.enableToolbarItem("video");
        }

{% endhighlight %}

N> If a toolbar item is in disabled state, then it will not have any interactivity including mouse hover.

### Show/Hide Toolbar

The toolbar can be initially set to visible or hidden within the editor using ShowToolbar API. Default value is “true”.

{% highlight html %}
    
    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
    .ShowToolbar(false)
    .Render();}
    
{% endhighlight %}

## Content Area

The editor creates the iframe element as the content area on control initialization, it is used to display and editing the content. In Content Area, the editor displays only the body tag of a &lt; iframe &gt; document. To set or modify details in the &lt; head &gt; tag, use [Source view](#source-view) of the editor.

### IFrame Attributes

The editor allows you to passing an additional attributes to body tag of a &lt; iframe &gt; element using IFrameAttributes property. The property contains name/value pairs in string format, it is used to override the default appearance of the content area. For example, the content area’s font, color, margins, and background can be overridden using IFrameAttributes property. You can specifies the editable behavior (content editable) of the content also in this property. For more information about the content editable, see [content editable](#content-editable).

{% highlight html %}

    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
    .IFrameAttributes(new Dictionary<string, object> { { "style", "background-color:#e0ffff;color:#6495ed;" } })
    .Render();}
    
{% endhighlight %}

### Adding CSS File

The editor offers you to add external CSS file to style the &lt; iframe &gt; element.  You can change the appearance of editor’s content using an external CSS file. For example, apply default styles for headings (h1, h2, etc.) and lists (bulleted or numbered) of the editor’s content. 

{% highlight html %}

    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
    .ExternalCSS("/Content/Css/iframe-custom.css")
    .Render();}
    
{% endhighlight %}

The new file named iframe-custom.css is created and moved to the content folder with the following styles.

{% highlight html %}

    div {
    color:navy;
    margin-left:20px;
    }
    
    ul {
    display:block;
    list-style-type:square;
    margin-left:10px;
    }
    
    ol {
    display:block;
    list-style-type:circle;
    margin-right:10px;
    }

{% endhighlight %}

### Content Editable

The editor provides option to control the editable behavior using AllowEditing property. When the AllowEditing property is set to false, the editor disables its editing functionality. 

{% highlight html %}
    
    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
    .AllowEditing(false)
    .Render();}

{% endhighlight %}

The ContentEditable attribute allows you to make any element of HTML content to become editable or non-editable.  

{% highlight html %}

    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
        <p> Cannot Edit </p>
    </div>)
    .ClientSideEvents(e => e.Create("onCreate"))
    .Render();}
    
    <script>
        function onCreate() {
            var editor = $("#rteSample").ejRTE("instance");
            var iframeDoc = editor.getDocument();
            var paragraph = $("p", iframeDoc.body);
            $($(paragraph)[0]).attr("contenteditable", "false");
        }
    </script>

{% endhighlight %}

N> Content editable is fully compatible with latest browsers, to know more details, see [here](http://www.w3schools.com/tags/att_global_contenteditable.asp#).

## Footer

This option allows you to specify which footer elements should display at the bottom of the editor. The available footer elements are listed below:

1. HTML View
2. HTML Tag Info
3. Characters Count / Word Count 
4. Clear Format
5. Resizer

When the footer is enabled, it displays the html tag, word Count, character count, clear format, resize icon and clear all the content icons, by default.

{% highlight html %}

    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
    .ShowFooter(true)
    .Render();}
    
{% endhighlight %}

### Source View

Source view displays the HTML code of the content in a separate dialog. Source view allows you to view and edit the HTML Tags, scripts, and styles directly. If you made any modification in Source view directly, click **Update** button to synchronize with Design view.

You can paste HTML text into Source view. If you cut or copy from HTML source such as page source of Browser, paste as HTML (without escape characters) into Source view. 

{% highlight html %}

    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
       The Rich Text Editor
       (RTE) control is an easy to render in client side. Customer easy to edit the contents
       and get the HTML content for the displayed content. A rich text editor control provides
       users with a toolbar that helps them to apply rich text formats to the text entered
       in the text area.
    </div>)
          .ShowFooter(true)
          .ShowHtmlSource(true)
          .Render();}

{% endhighlight %}

N> Source view is useful for working directly with raw HTML text, so this tool is mainly used for advanced users who would like to have more control over the source of their content. 

### HTML Tag Info

The HTML tag info tool that shows the path of currently selected tag along with hierarchy of parent tags to which it belongs. The tag information is displayed at the bottom of the editor. It is used to determine which element has the focus in the editor’s content.

{% highlight html %} 

    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
    .ShowFooter(true)
    .ShowHtmlTagInfo(true)
    .Render();}

{% endhighlight %}

N> The outermost tag is the body tag of &lt; iframe &gt; element in design view, so it shows the path from currently selected path to the body tag.

### Characters Count/Word Count

The editor automatically counts the number of characters and words in the content while you type. The characters and words count displayed at the bottom of the editor. You can limit the number of characters in your content using MaxLength property. By default, the editor sets the characters limit value as 7000 characters.

{% highlight html %}

    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
    .ShowFooter(true)
    .ShowWordCount(true)
    .ShowCharCount(true)
    .Render();}
    
{% endhighlight %}

N> The editor counts the characters by including the space, and this validation occurs while pasting the content into the editor also.

### Clear Format

The clear format tool is useful to remove all formatting styles (such as bold, italic, underline, color, superscript, subscript, and more) from currently selected text. As a result, all the text formatting will be cleared and return to its default formatting styles. When you set the ShowClearFormat property to true, the clear format tool will be displayed at bottom of the editor.

{% highlight html %}

    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
    .ShowFooter(true)
    .ShowClearFormat(true)
    .Render();}
    
{% endhighlight %}

### Resize Handle

When you set the EnableResize property to true, resize handle will be displayed at bottom-right corner of the editor. You can drag the handle to change its size. On resizing, the editor will automatically adjust the toolbar, content area, and footer within it accordingly. Resize limits can be defined via MinHeight, MaxHeight, MinWidth, and MaxWidth properties. You can specify the size of the editor programmatically through the Height and Width properties. 

{% highlight html %}
    
    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
    .ShowFooter(true)
    .EnableResize(true)
    .MinWidth("250")
    .MinHeight("250")
    .MaxHeight("500")
    .MaxWidth("750")
    .Render();}
    
{% endhighlight %}

N> When you set the EnableRTL property to true, the resize handle will automatically positioned to the bottom-left corner of the editor.

