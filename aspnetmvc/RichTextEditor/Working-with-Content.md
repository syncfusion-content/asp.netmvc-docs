---
layout: post
title: Working with content related operation in RichTextEditor widget for Syncfusion Essential ASP.NET MVC
description: Working with Content related changes in RichTextEditor widget
platform: ASP.NET MVC
control: RTE
documentation: ug
keywords: RichTextEditor, Submit Content, Refresh

---
# Working with Content

The editor creates the iframe element as the content area on control initialization, it is used to display and editing the content. In Content Area, the editor displays only the body tag of a &lt; iframe &gt; document. To set or modify details in the &lt; head &gt; tag, use [Source view](#footer#source-view) of the editor.

## IFrame Attributes

The editor allows to passing an additional attributes to body tag of a &lt; iframe &gt; element using IFrameAttributes property. The property contains name/value pairs in string format, it is used to override the default appearance of the content area. 

N> The content area’s font, color, margins, and background can be overridden using iframeAttributes property. You can specifies the editable behavior (content editable) of the content also in this property.

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

N> Background image for the RTE control : {{'[Link](http://jsplayground.syncfusion.com/Sync_cpaoqshs)'| markdownify }} <BR>
Set default font for the Iframe : {{'[Link](http://jsplayground.syncfusion.com/Sync_k2uwsibi)'| markdownify }}

## Adding CSS File

The editor offers to add external CSS file to style the &lt; iframe &gt; element.  Easily change the appearance of editor’s content using an external CSS file. For example, apply default styles for headings (h1, h2, etc.) and lists (bulleted or numbered) of the editor’s content. 

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

N> Our RTE control editor section is an iframe. An iframe has another scope, so we can't access it to style using class which is defined in main document. To set the styles for the contents that kept inside the editor(iframe) we have to append the styles link in iframe head section.

## Content Editable

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

## Submit Content

The editor allows you to process its content before it is being submitted to the server on form submit event. You can use this option to validate content on the client side to prevent invalid data from being submitted to the server.

This example shows how to encode the HTML content before form submit event.

{% highlight html %}

<form>
    @{Html.EJ().RTE("rteSample").Width("100%").ContentTemplate(@<p>
            The Rich Text Editor
            (RTE) control is an easy to render in client side. Customer easy to edit the contents
            and get the HTML content for the displayed content. A rich text editor control provides
            users with a toolbar that helps them to apply rich text formats to the text entered
            in the text area.
        </p>)
            .ShowFooter(true)
            .ShowHtmlSource(true)
            .Render();}
    <br />
    @{Html.EJ().Button("Submit").Text("Submit").Type(ButtonType.Submit).Render();}
    
</form>
    
<script type="text/javascript">
    $("form").on("submit", function () {

        var editor = $("#rteSample").data("ejRTE");
        var encoded = $('<div />').text(editor.model.value).html();
        $("#rteSample").val(encoded);

    });
</script>
    
{% endhighlight %}

## Refresh

When you move the editor’s wrapper element into another DOM element, the editor needs to be reinitialized by the [refresh](http://help.syncfusion.com/js/api/ejrte#methods:refresh) method to retain its content. The method reload the content area and rebind the events of the editor. 

{% highlight html %}

@{Html.EJ().RTE("rteSample").Width("100%").ContentTemplate(@<p>
    The Rich Text Editor
    (RTE) control is an easy to render in client side. Customer easy to edit the contents
    and get the HTML content for the displayed content. A rich text editor control provides
    users with a toolbar that helps them to apply rich text formats to the text entered
    in the text area.

</p>)
    .Render();}
<br />
@{Html.EJ().Dialog("Target").Width("600px").Render();}
@{Html.EJ().Button("Append").Text("Append").ClientSideEvents(e => e.Click("appendTo")).Render();}
@{Html.EJ().Button("Refresh").Text("Refresh").ClientSideEvents(e => e.Click("refresh")).Render();}

<script type="text/javascript">
    var editor;
    function appendTo() {
        editor = $("#rteSample").ejRTE("instance");
        editor._rteWapper.appendTo($("#Target"))
    }
    function refresh() {
        editor = $("#rteSample").ejRTE("instance");
        editor.refresh()
    }
</script>

{% endhighlight %}

## Persistence

The editor is capable to persist its content with HTML format. By default, the persistence support is disabled in the editor. When you set the EnablePersistence property to true, the persistence will be enabled in the editor.

N>  [local storage](http://www.w3schools.com/html/html5_webstorage.asp#) is not supported below ie9 version, therefore persistence support is fallback to [cookie](http://www.w3schools.com/js/js_cookies.asp#).

{% highlight html %}

@{Html.EJ().RTE("rteSample").Width("800px")
    .EnablePersistence(true)
    .Render();}
<br/>
    
{% endhighlight %}

## Set Default Font Name and Size

* Set a default font name and font size to the font name and size drop-down programmatically.

N> •	By default, the editor’s < iframe > is initialized with “Segoe UI” font name and 3(12pt) font size. <BR> 
•	To change it, select a different font name and font size from the drop-down in the editor’s toolbar. <BR>
•	To apply different font style for particular section of the content, select the text that you would like to change, and select a required font style from the drop-down to apply the changes to the selected text.<BR>

{% highlight html %}

@{
    List<String> toolsList = new List<string>() { "font" };
    List<String> font = new List<string>() { "fontName", "fontSize", "fontColor", "backgroundColor" };
}
@{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
    The Rich Text Editor
    (RTE) control is an easy to render in client side. Customer easy to edit the contents
    and get the HTML content for the displayed content. A rich text editor control provides
    users with a toolbar that helps them to apply rich text formats to the text entered
    in the text area.
</div>)
        .ClientSideEvents(e => e.Create("Oncreate"))
    .ToolsList(toolsList).Tools(tool => tool.Font(font))
    .Render();}
<br />

<script>
    function Oncreate() {
        var editor = $("#rteSample").ejRTE("instance");
        var ddl = editor._fontStyleDDL.ejDropDownList("instance");
        ddl.selectItemByIndex(7);
        var ddlSize = editor._fontSizeDDL.ejDropDownList("instance");
        ddlSize.selectItemByIndex(5);
    }

</script>

{% endhighlight %}

* Set default font name and size for &lt; iframe &gt;’s body tag using [IFrameAttributes](#iframe-attributes) property.

{% highlight html %}

@{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
    The Rich Text Editor
    (RTE) control is an easy to render in client side. Customer easy to edit the contents
    and get the HTML content for the displayed content. A rich text editor control provides
    users with a toolbar that helps them to apply rich text formats to the text entered
    in the text area.
</div>)
.IFrameAttributes(new Dictionary<string, object> { { "style", "font-family:Arial;;font-size:14px;" } })
.Render();
}
  
{% endhighlight %}

* If you want to override the default font from CSS, create a style tag with CSS styles and append it to the &lt; iframe &gt;’s head tag of the editor.

{% highlight html %}

@{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
    The Rich Text Editor
    (RTE) control is an easy to render in client side. Customer easy to edit the contents
    and get the HTML content for the displayed content. A rich text editor control provides
    users with a toolbar that helps them to apply rich text formats to the text entered
    in the text area. 
</div>)
.ClientSideEvents(e => e.Create("Oncreate"))
.Render();}
    <br />

<script>
    function Oncreate() {
        var css = "html,body{font-family:sans-serif;font-size:14px; }";
        var editorDoc = $("#rteSample").ejRTE("instance").getDocument();
        var styleTag = document.createElement("style");
        styleTag.type = "text/css";
        if (styleTag.styleSheet) 
            styleTag.styleSheet.cssText = css;
        else 
            styleTag.appendChild(document.createTextNode(css));
        editorDoc.head.appendChild(styleTag);
    }
</script>

{% endhighlight %}

## Adding Font names and size

If you want to add additional font names and sizes to font drop-down, pass the font information as JSON data and bind it with instance of drop-down. 

{% highlight html %}

@{List<String> toolsList = new List<string>() { "font" };
List<String> font = new List<string>() { "fontName", "fontSize", "fontColor", "backgroundColor" };}
    
    
@{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
    The Rich Text Editor
    (RTE) control is an easy to render in client side. Customer easy to edit the contents
    and get the HTML content for the displayed content. A rich text editor control provides
    users with a toolbar that helps them to apply rich text formats to the text entered
    in the text area.</div>)
    .ClientSideEvents(e => e.Create("Oncreate"))
    .ToolsList(toolsList).Tools(tool => tool.Font(font))
    .Render();}
<br />

<script>
    function Oncreate() {
        var editor = $("#rteSample").ejRTE("instance");
        editor.defaults.fontName.push({ text: "Calibri Light", value: "CalibriLight" }, { text: "Calibri", value: "Calibri" });
        editor.defaults.fontSize.push({ text: "8 (42pt)", value: "8" });
        var ddl = editor._fontStyleDDL.ejDropDownList("instance");
        var ddlSize = editor._fontSizeDDL.ejDropDownList("instance");
        ddl.option({ "dataSource": editor.defaults.fontName });
        ddlSize.option({ "dataSource": editor.defaults.fontSize });
        ddl.selectItemByValue("CalibriLight");
        ddlSize.selectItemByValue("8");
    }

</script>

{% endhighlight %}

## Apply Font color and Background color

If you want to apply font  color or background color for a selected content of RTE you can use font color and background color tools. These tools contains a color palette with basic colors along with an option called **"More colors.."** in order to choose custom colors from color picker dialog.You can apply transparent background color for selected text through **transparent** button available in background color palette.

{% highlight html %}

   @{List<String> toolsList = new List<string>() { "font" };
     List<String> font = new List<string>() { "fontName", "fontSize", "fontColor", "backgroundColor" };}
    
    
   @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
    The Rich Text Editor
    (RTE) control is an easy to render in client side. Customer easy to edit the contents
    and get the HTML content for the displayed content. A rich text editor control provides
    users with a toolbar that helps them to apply rich text formats to the text entered
    in the text area.</div>)
    .ToolsList(toolsList).Tools(tool => tool.Font(font))
    .Render();}

{% endhighlight %}

## Insert the content at cursor

If you want to insert/paste the content at the current cursor position (or) to replace the selected content with some formatting, you can use pasteContent method in the editor.

{% highlight html %}

    
@{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
    The Rich Text Editor
    (RTE) control is an easy to render in client side. Customer easy to edit the contents
    and get the HTML content for the displayed content. A rich text editor control provides
    users with a toolbar that helps them to apply rich text formats to the text entered
    in the text area.
</div>)
    .Render();}
<br />
@{Html.EJ().Button("sample").Width("100px").Text("PasteContent").ClientSideEvents(e => e.Click("pasteContent")).Render();}

<script>
    function pasteContent() {
        var editor = $("#rteSample").ejRTE("instance");
        var selectedHtml = editor.getSelectedHtml();
        editor.pasteContent("<p style='background-color:yellow;color:skyblue'> " + selectedHtml + " </p>");
    }
</script>
    
{% endhighlight %}

