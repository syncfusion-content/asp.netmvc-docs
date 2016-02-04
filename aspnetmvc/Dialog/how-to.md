---
layout: post
title: How To? | Dialog | ASP.NET MVC | Syncfusion
description: How to achieve specific requirements in Dialog widget for Essential ASP.NET MVC
platform: ejmvc
control: Control Name undefined
documentation: ug
keywords : ejdialog, MVC Dialog, EJ MVC Dialog, Dialog ui, web Dialog, ej Dialog, Dialog control, ASP.NET MVC Dialog, ASP MVC Dialog
---

# How To?

## Create Multiple Dialogs

Essential Studio for ASP.NET library supports multiple Dialog widgets in the same web page with different contents and different functionalities.

Initialize the Dialog widgets by configuring as below.

{% highlight razor %}


    @{
        Html.EJ()
            .Dialog("firstdialog")
            .Title("Dialog")
            .Width(250)
            .Position(pos => pos.XValue("20px").YValue("20px"))
            .ContentTemplate(@<p>This is a simple dialog</p>)
            .Render();
    }

    @{
        Html.EJ()
            .Dialog("seconddialog")
            .Title("Window")
            .Width(250)
            .Position(pos => pos.XValue("300px").YValue("20px"))
            .ContentTemplate(@<p>This is a different dialog</p>)
            .Render();
    }

    @{
        Html.EJ()
            .Dialog("thirddialog")
            .Title("Popup")
            .Width(250)
            .Position(pos => pos.XValue("150px").YValue("150px"))
            .ContentTemplate(@<p>This is an another dialog</p>)
            .Render();
    }



{% endhighlight %}



N> If the position of the dialog is not set as above, all the three dialogs will be overlapped with each other.

![Create Multiple Dialogs](how-to_images\create-multiple-dialogs_img1.png)


## Create Nested Dialog

A Dialog widget can be nested within another Dialog widget.

Create a div element to render the child Dialog widget and use it as a content of parent Dialog widget.

{% highlight razor %}


    @{
        Html.EJ()
            .Button("outerbutton")
            .Text("Open Dialog")
            .Type(ButtonType.Button)
            .ClientSideEvents(evt => evt.Click("openDialog"))
            .Render();
    }

    @{
        Html.EJ()
            .Dialog("outerdialog")
            .Title("Dialog")
            .Width(500)
            .Height(400)
            .ShowOnInit(false)
            .ContentTemplate(@<div>
                @Html.EJ().Button("innerbutton").Text("Open Nested Dialog").ClientSideEvents(evt => evt.Click("openNestedDialog"))
            </div>)
            .Render();
    }

    @{
        Html.EJ()
            .Dialog("seconddialog")
            .Title("Window")
            .Width(400)
            .Height(300)
            .ShowOnInit(false)
            .ContentTemplate(@<p>This is a nested dialog</p>)
            .Render();
    }



{% endhighlight %}


Add the below script to the view page

{% highlight js %}


    <script>
        function openDialog() {
            $("#outerdialog").ejDialog("open");
        }
        function openNestedDialog() {
            $("#seconddialog").ejDialog("open");
        }
    </script>



{% endhighlight %}



