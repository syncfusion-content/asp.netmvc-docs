---
layout: post
title: Load Conent | Dialog | ASP.NET MVC | Syncfusion
description: How to load content to dialog widget either using the Ajax, iframe, and Image.
platform: ejmvc
control: Control Name undefined
documentation: ug
keywords : ejdialog, MVC Dialog, EJ MVC Dialog, Dialog ui, web Dialog, ej Dialog, Dialog control, ASP.NET MVC Dialog, ASP MVC Dialog
---

# Load content

By default, the content inside the ContentTemplate property element is considered as the content for the Dialog widget.

Also, we can render the Dialog widget content through the following ways.

1. Request through AJAX

2. Request iframe content

3. Request image content

This settings can be specified through `ContentType` property.

{{ 'N> Create a view page (AjaxContent.cshtml) which contains the content of the dialog.' | markdownify }}

{% highlight razor %}


    @{
        Html.EJ()
            .Dialog("dialog")
            .Title("Dialog")
            .ContentType("ajax")
            .ContentUrl("AjaxContent")
            .Render();
    }



{% endhighlight %}

AjaxContent.cshtml

{% highlight razor %}


    <div id="content"> This content is loaded via AJAX request. </div>



{% endhighlight %}



![Load content](load-content_images\load-content_img1.png)

We can handle the AJAX request’s success and failures through the events “ClientSideOnAjaxSuccess” and “ClientSideOnAjaxError” events respectively. 

You can modify the previous example as below to handle the success and failure events.

{% highlight razor %}


    @{
        Html.EJ()
            .Dialog("dialog")
            .Title("Dialog")
            .ContentType("ajax")
            .ContentUrl("AjaxContent")
            .ClientSideEvents(evt => evt.AjaxSuccess("onSuccess").AjaxError("onError"))
            .Render();
    }



{% endhighlight %}


Add the below script to the view page

{% highlight js %}


    <script>
        function onSuccess(args) {
            //handle success event
        }
        function onError(args) {
            //handle success event
        }
    </script>



{% endhighlight %}


N> The same way we can render the iframe and image content for the Dialog widget by specifying the `ContentType` as “iframe” and “image” respectively and also by specifying the proper location in the `ContentUrl` property.

