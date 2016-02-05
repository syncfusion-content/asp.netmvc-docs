---
layout: post
title: Animation | Dialog | ASP.NET MVC | Syncfusion
description: How to apply animation effects.
platform: ejmvc
control: Control Name undefined
documentation: ug
keywords : ejdialog, MVC Dialog, EJ MVC Dialog, Dialog ui, web Dialog, ej Dialog, Dialog control, ASP.NET MVC Dialog, ASP MVC Dialog
---

## Animation

The Dialog widget can be animated while opening and closing the dialog.

We can specify the effect and the duration for the animation. There are two types of effects (slide and fade). We can configure these settings separately for open and close dialog actions.


{% highlight razor %}


    @{
        List<string> actionButtons = new List<string>();
        actionButtons.Add("close");
        actionButtons.Add("maximize");
        actionButtons.Add("minimize");
        actionButtons.Add("collapsible");
    }

    @{
        Html.EJ()
         .Dialog("dialog")
         .Title("Dialog")
         .ActionButtons(actionButtons)
         .Animation(animate => animate.Show(show => show.Duration(500).Effect("slide")).Hide(hide => hide.Duration(500).Effect("fade")))
         .ContentTemplate(@<p>This is a Dialog</p>)
         .Render();
    }



{% endhighlight %}



![Animation](animation_images\animation_img1.png)

