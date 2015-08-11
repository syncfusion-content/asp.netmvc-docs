---
layout: post
title: Context-Menu
description: context menu
platform: ejmvc
control: Menu
documentation: ug
---

# Context Menu

A context menu is a type of menu in a graphical user interface (GUI) that appears when you perform right click operation. In this Menu control you can use a context menu by specifying the type of menu as ContextMenu. A context also provides support for nested level of menu items.

Before you use the context menu, provide the target area for it. 

In the following example, a context menu for the division containing text is created. In this, when you perform right click operation, the following menu appears with open, edit, etc.

1. Add the following code in your View page.




{% highlight html %}
[CSHTML]

// Add the following code in your CSHTML page.

   <div id="target" class="textarea">

        HTML is written in the form of HTML elements consisting of tags enclosed in angle

        brackets (like <html> ),within the web page content. HTML tags most commonly

        come in pairs like and ,although some tags, known as empty elements, are unpaired,

        for example <img>. The purpose of a web browser is to read HTML documents

        and compose them into visible or audible web pages. The browser does not display

        the HTML tags, but uses the tags to interpret the content of the page.

    </div>

    @Html.EJ().Menu("docfile").Items(items =>

                   {

                       items.Add().Text("Open").Children(child =>

                       {

                           child.Add().Text("Open with notepad");

                           child.Add().Text("Open with notepad++");

                       });

                       items.Add().Text("Edit");

                       items.Add().Text("Save");

                       items.Add().Text("Save as");

                       items.Add().Text("Print");

                       items.Add().Text("Properties");

                   }).MenuType(MenuType.ContextMenu).OpenOnClick(true).ContextMenuTarget("#target")



{% endhighlight  %}

2. Add the following code in your style section.
{% highlight css %}
[CSS]

<style type="text/css">

    .textarea {

        border: 1px solid;

        padding: 10px;

        position: relative;

        text-align: justify;

        width: 463px;

        color: gray;

        margin: 0 auto;

    }

</style>

{% endhighlight %}

The following screen shot displays the output of the above code.

![](Context-Menu_images/Context-Menu_img1.png)



_Figure33: Context Menu_



You can hide and show the context menu using the following methods.

## HideContextMenu

Hides the context Menu control. Add the following script code in the sample in order to hide the context menu.

{% highlight js %}
[Javascript]

<script type="text/javascript">

    jQuery(function ($) {

        $("#menucontrol").ejMenu({

            width: 500,



        });

        //initialize the menu object

        var menuObj = $("#menucontrol").data("ejMenu");



        //To enable Menu item using item id

        menuObj.hideContextMenu();

    });

</script>
{% endhighlight  %}

## ShowContextMenu

Shows the context menu control. Add the following script code in the sample in order to show the context menu.
{% highlight js %}

[Javascript]

<script type="text/javascript">

    jQuery(function ($) {

        $("#menucontrol").ejMenu({

            width: 500,



        });

        //initialize the menu object

        var menuObj = $("#menucontrol").data("ejMenu");



        //To enable Menu item using item id

        menuObj.showContextMenu();



    });

</script>


{% endhighlight  %}
