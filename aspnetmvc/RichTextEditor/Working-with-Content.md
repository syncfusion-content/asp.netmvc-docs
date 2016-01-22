---
layout: post
title: Working with content related operation in RichTextEditor widget for Syncfusion Essential ASP.NET MVC
description: Working with Content related changes in RichTextEditor widget
platform: ASP.NET MVC
control: RTE
documentation: ug

---
# Working with Content

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

## Editing and Formatting 

The editor’s [toolbar](/js/richtexteditor/user-interface#toolbar) contains buttons and dropdowns that allow you to editing and formatting in your content.
 
* Font name, Font size, and color
* Bold, Italic, Underline, and Strikethrough
* Text Alignment – left, right, center, and justify
* Indent – left and right
* Styles – quotation, normal,  headings, and sub-headings
* Superscript and Subscript
* Casing – convert to lower case and upper case
* List – create ordered and unordered list

{% highlight html %}

    
    @{List<String> toolsList = new List<string>() { "formatStyle", "font", "style", "effects", "alignment", "lists", "indenting", "clipboard", "doAction", "clear", "links", "images", "media", "tables", "casing", "customTool", "view" };
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
    List<String> effects = new List<string>() { "superscript", "subscript" };
    List<String> casing = new List<string>() { "upperCase", "lowerCase" };
    List<String> formatStyle = new List<string>() { "format" };
    List<String> view = new List<string>() { "fullScreen" };
    }
    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
    .ToolsList(toolsList)
    .Tools(tool => tool.Clear(clear).FormatStyle(formatStyle).Tables(tables).Links(links).Images(images).Effects(effects).Casing(casing).Font(font).Styles(style).Media(media).Alignment(alignment).Lists(lists).Clipboard(clipboard).DoAction(doAction).Indenting(indenting).View(view))
    .Render();}
    <br />

{% endhighlight %}

## Undo and Redo 

Undo and Redo buttons allow you to editing the text by disregard/cancel the recently made changes and restore it to previous state. It is a useful tool to restore the performed action which got changed by mistake. Up to 50 actions can be undo/redo in the editor by default. 

To undo and redo operations, do one of the following:

* Press the undo/redo button on the toolbar
* Press the <kbd> Ctrl </kbd> + <kbd> Z </kbd> ,  <kbd>Ctrl </kbd> + <kbd> Y </kbd> combination on the keyboard


{% highlight html %}

    @{
        List<String> toolsList = new List<string>() { "doAction" };
        List<String> doAction = new List<string>() { "undo", "redo" };

    }
    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
            .ToolsList(toolsList).Tools(tool => tool.DoAction(doAction))
            .Render();}
    <br />

{% endhighlight %}

## Clipboard Operations

The editor provides support for the clipboard operations (cut, copy, and paste) in all text and images using the toolbar buttons and the keyboard shortcuts. Toolbar includes buttons through which the clipboard operations, such as Cut, Copy, and Paste can be accessed.

You can use the keyboard shortcuts to perform the clipboard operations.

* Cut - <kbd>CTRL</kbd> + <kbd>X</kbd>  
* Copy - <kbd>CTRL</kbd> + <kbd>C</kbd> 
* Paste - <kbd>CTRL</kbd> + <kbd>V</kbd> 

Some browsers block the clipboard access from JavaScript. If you want to use the Cut, Copy, and Paste buttons on the toolbar, you need to allow JavaScript to use the clipboard. If you don’t want to do this configuration, use CTRL+C, CTRL+X, and CTRL+V keyboard commands.

{% highlight html %}

    @{
        List<String> toolsList = new List<string>() { "clipboard" };
        List<String> clipboard = new List<string>() { "cut", "copy", "paste" };

    }
    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
            .ToolsList(toolsList).Tools(tool => tool.Clipboard(clipboard))
            .Render();}

{% endhighlight %}

## Persistence

The editor is capable to persist its content with HTML format. By default, the persistence support is disabled in the editor. When you set the EnablePersistence property to true, the persistence will be enabled in the editor.

N>  [localstorage](http://www.w3schools.com/html/html5_webstorage.asp#) is not supported below ie9 version, therefore persistence support is fallback to [cookie](http://www.w3schools.com/js/js_cookies.asp#).

{% highlight html %}

    @{Html.EJ().RTE("rteSample").Width("800px")
        .EnablePersistence(true)
        .Render();}
    <br/>
    
{% endhighlight %}

## Change the Font

By default, the editor’s &lt; iframe &gt; is initialized with “Segoe UI” font. To change it, select a different font from the drop-down in the editor’s toolbar. To apply different font for particular section of the content, select the text that you would like to change, and select a required font from the drop-down to apply the changes to the selected text.

### Set Default Font

* Set a default font to the font drop-down programmatically.

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
        }
    
    </script>

{% endhighlight %}

* You can set default font for &lt; iframe &gt;’s body tag using [IFrameAttributes](user-interface#iframe-attributes) property.

{% highlight html %}

    @{Html.EJ().RTE("rteSample").Width("800px").ContentTemplate(@<div>
        The Rich Text Editor
        (RTE) control is an easy to render in client side. Customer easy to edit the contents
        and get the HTML content for the displayed content. A rich text editor control provides
        users with a toolbar that helps them to apply rich text formats to the text entered
        in the text area.
    </div>)
    .IFrameAttributes(new Dictionary<string,object>{{"style", "font-family:Arial;"}})
    .Render();
    
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

### Adding Fonts

If you want to add additional fonts to font drop-down, pass the font information as JSON data and bind it with instance of drop-down. 

{% highlight html %}

    @{List<String> toolsList = new List<string>() { "font" };
    List<String> font = new List<string>() { "fontName", "fontSize", "fontColor", "backgroundColor" };}


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
            editor.defaults.fontName.push({ text: "Calibri Light", value: "CalibriLight" }, { text: "Calibri", value: "Calibri" });
            var ddl = editor._fontStyleDDL.ejDropDownList("instance");
            ddl.option({ "dataSource": editor.defaults.fontName });
            ddl.selectItemByValue("CalibriLight");
        }

    </script>

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

## Validation 

You can validate the RichTextEditor’s value on form submission by applying ValidationRules and ValidationMessage to the RichTextEditor.

N> [jquery.validate.min](http://cdn.syncfusion.com/js/assets/external/jquery.validate.min.js) script file should be referred for validation, for more details, refer [here](http://jqueryvalidation.org/documentation).


### Validation Rules

The validation rules help you to verify the content by adding validation attributes to the text area. This can be set by using ValidationRules property.


### Validation Messages 

You can set your own custom error message by using ValidationMessage property. To display the error message, specify the corresponding annotation attribute followed by the message to display.


N> jQuery predefined error messages to that annotation attribute will be shown when this property is not defined. The below given example explain this behavior of 'minWordCount’ attribute,


When you initialize the RichTextEditor widget, it creates a text area hidden element which is used to store the value. Hence, the validation is performed based on the value stored in this hidden element.

Required field and minWordCount values validation is demonstrated in the below given example.

{% highlight html %}

    @using (Html.BeginForm())
    {
        <br />
        @Html.EJ().RTE("RTE1").ValidationRules(new Dictionary<string, object> { { "required", "true" }, { "minWordCount", 15 } }).ValidationMessage(new Dictionary<string, object> { { "minWordCount", "Number of word count does not reach" }, { "Required", "Please enter the content" } })
        <br />
        @Html.EJ().Button("Btn1").Text("Validate")
    
    }
 
{% endhighlight %}

![](WorkingwithContent_images/validation.png)

