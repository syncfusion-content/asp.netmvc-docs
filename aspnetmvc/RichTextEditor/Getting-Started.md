---
layout: post
title: Getting started with RichTextEditor widget for Syncfusion Essential ASP.NET MVC
description: Getting started with RichTextEditor and configure the toolbar and other functionalities.
platform: ASP.NET MVC
control: RTE
documentation: ug

---
# Getting Started

This section helps to understand the getting started of RTE control with the step-by-step instruction.

## Create your first RichTextEditor in MVC

ASP.NET MVC RTE widget basically renders by using the simple text area element.
1.	You can create a MVC Project and add the necessary dll’s and scripts with the help of the given http://help.syncfusion.com/aspnetmvc/getting-started documentation.
2.	Add the following code example to the corresponding view page to render the RichTextEditor.

{% highlight CSHTML %}
<div>
	
	@Html.EJ().RTE("rteSample").Width("820px")
	
</div>
{% endhighlight %}

## Toolbar–Configuration

You can configure a toolbar with the tools as your application requires.

{% highlight CSHTML %}

<div>
    @{
        List<String> style = new List<string>() { "bold", "italic", "underline", "strikethrough" };
        List<String> lists = new List<string>() { "unorderedList", "orderedList" };
        List<String> doAction = new List<string>() { "undo", "redo" };
        List<String> links = new List<string>() { "createLink" };
        List<String> images = new List<string>() { "image" };
    }
    @Html.EJ().RTE("rteSample").Width("820px").Tools(tool => tool.Styles(style).Lists(lists).DoAction(doAction).Links(links).Images(images))
</div>

{% endhighlight %}

## Setting and Getting Content

You can set the content of the editor as follows.

{% highlight CSHTML %}

<div>
    @{
        List<String> style = new List<string>() { "bold", "italic", "underline", "strikethrough" };
        List<String> lists = new List<string>() { "unorderedList", "orderedList" };
        List<String> doAction = new List<string>() { "undo", "redo" };
        List<String> links = new List<string>() { "createLink" };
        List<String> images = new List<string>() { "image" };
    }
     @Html.EJ().RTE("rteSample").Width("820px").ContentTemplate(@<div>
        &lt;p&gt;&lt;b&gt;Description:&lt;/b&gt;&lt;/p&gt;
        &lt;p&gt;The Rich Text Editor (RTE) control is an easy to render in
                 client side. Customer easy to edit the contents and get the HTML content for
                 the displayed content. A rich text editor control provides users with a toolbar
                 that helps them to apply rich text formats to the text entered in the text area. 
        &lt;/p&gt;
        &lt;p&gt;&lt;b&gt;Functional Specifications/Requirements:&lt;/b&gt;&lt;/p&gt;
        &lt;ol&gt;&lt;li&gt;&lt;p&gt;Provide the tool bar support, it’s also customizable.&lt;/p&gt;&lt;/li&gt;
        &lt;li&gt;&lt;p&gt;Options to get the HTML elements with styles.&lt;/p&gt;&lt;/li&gt;
        &lt;li&gt;&lt;p&gt;Support to insert image from a defined path.&lt;/p&gt;&lt;/li&gt;
        &lt;li&gt;&lt;p&gt;Footer elements and styles(tag / Element information , Action button (Upload, Cancel))&lt;/p&gt;&lt;/li&gt;
        &lt;li&gt;&lt;p&gt;Re-size the editor support. &lt;/p&gt;&lt;/li&gt;&lt;li&gt;
        &lt;p&gt;Provide efficient public methods and client side events.&lt;/p&gt;&lt;/li&gt;
        &lt;li&gt;&lt;p&gt;Keyboard navigation support.&lt;/p&gt;&lt;/li&gt;&lt;/ol&gt;
    </div>).Tools(tool => tool.Styles(style).Lists(lists).DoAction(doAction).Links(links).Images(images))
</div>

{% endhighlight %}

To retrieve the editor contents,

{% highlight js %}

var currentValue = $("#rteSample").ejRTE("model.value");

{% endhighlight %}