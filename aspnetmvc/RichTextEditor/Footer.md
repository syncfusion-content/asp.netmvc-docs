---
layout: post
title: Footer in RichTextEditor widget for Syncfusion Essential ASP.NET MVC
description: Footer to format the RichTextEditor widget's content
platform: ejmvc
control: RTE
documentation: ug
keywords: RichTextEditor, Footer, Clear Format, Re-sizer, HTML Tag info, Characters Count, Word Count

---
# Footer

This option allows you to specify which footer elements should be shown at the bottom of the editor. The available footer elements are listed below:

1. HTML View
2. HTML Tag Info
3. Characters Count / Word Count 
4. Clear Format
5. Resizer

When the footer is enabled, it displays the HTML tag, word Count, character count, clear format, resize icon and clear all the content icons, by default.

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

## Source View

RichTextBox includes the ability for users to directly edit HTML code via “Source View” in a separate dialog. If you made any modification in Source view directly, click Update button to synchronize with Design view. This provides power users with more flexibility over the content they create.

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

## HTML Tag Info

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

## Characters Count/Word Count

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

## Clear Format

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

## Resize Handle

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

N>  1.	As resizable option will be added in the footer of RTE, so set the showFooter property also as “true”.   <BR>
2.	In order to showcase only the resizer, disable the other properties in the Footer such as showClearFormat,  showClearFormat,  showCharCount, showWordCount <BR> 
3.	When you set the enableRTL property to true, the resize handle will automatically positioned to the bottom-left corner of the editor. <BR>

#### Characters Count/Word Count

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

By clicking the Characters Count/Word Count labels in footer , The word and character count information dialog is opened. It contains the details of the number of words and characters with and without spacing.  

![](UserInterface_images/wordchar.png)

N> The editor counts the characters by including the space, and this validation occurs while pasting the content into the editor also.


