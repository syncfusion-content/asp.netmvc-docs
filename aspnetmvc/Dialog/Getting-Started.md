---
layout: post
title: Getting Started | Dialog | ASP.NET MVC | Syncfusion
description: How to create Dialog widget with the step-by-step instructions.
platform: ejmvc
control: Control Name undefined
documentation: ug
keywords : ejdialog, MVC Dialog, EJ MVC Dialog, Dialog ui, web Dialog, ej Dialog, Dialog control, ASP.NET MVC Dialog, ASP MVC Dialog
---

# Getting Started

This section helps to understand the getting started of the Dialog widget with the step-by-step instructions.

## Create a Dialog

Create a MVC Project and add the necessary Dlls and scripts with the help of the given [MVC Getting Started](http://help.syncfusion.com/aspnetmvc/getting-started) documentation.

Add the following code snippet to the corresponding view page to render the Dialog.

{% highlight razor %}


    @{
        Html.EJ()
            .Dialog("dialog")
            .Render();
    }



{% endhighlight %}



![Create Dialog](getting-started_images\getting-started_img1.png)

### Set content

Add the contents for the dialog using `ContentTemplate` property as below.

{% highlight razor %}


    @{
        Html.EJ()
            .Dialog("dialog")
            .ContentTemplate(@<p>This is a simple dialog</p>)
            .Render();
    }


{% endhighlight %}



![Add dialog content](getting-started_images\getting-started_img2.png)

### Set Title

The Dialog widget’s title can be set as follows.

{% highlight razor %}


    @{
        Html.EJ()
            .Dialog("dialog")
            .Title("Dialog")
            .ContentTemplate(@<p>This is a simple dialog</p>)
            .Render();
    }


{% endhighlight %}



![Set the title](getting-started_images\getting-started_img3.png)

### Open Dialog dynamically

In most cases, the Dialog widgets are needed only in dynamic actions like showing some messages on clicking a button, to provide alert, etc. So the Dialog widget provides “open” and “close” methods to open/close the dialogs dynamically.

The Dialog widget can be hidden on initialize using `ShowOnInit` property which should be set to false.

{%seealso%}
[Button](http://help.syncfusion.com/aspnetmvc/button/overview).
{%endseealso%}

Refer the below example. The dialog will be opened on clicking the Button widget.

{% highlight razor %}


    @*button widget*@
    @{
        Html.EJ()
            .Button("button")
            .Text("Open Dialog")
            .Type(ButtonType.Button)
            .ClientSideEvents(evt => evt.Click("openDialog"))
            .Render();
    }

    @{
        Html.EJ()
            .Dialog("dialog")
            .Title("Dialog")
            .ShowOnInit(false)
            .ContentTemplate(@<p>This is a Dialog</p>)
            .Render();
    } 


{% endhighlight %}



Add the below script to the view page

{% highlight js %}


    <script>
        function openDialog() {
            $("#dialog").ejDialog("open");
        }
    </script>



{% endhighlight %}



![Open-Dialog-dynamically](getting-started_images\getting-started_img4.png)



