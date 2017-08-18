---
layout: post
title: Appearance and Styling | RadialMenu | ASP.NET MVC | Syncfusion
description: appearance and styling
platform: ejmvc
control: Radial Menu
documentation: ug
---

# Appearance and Styling

You can customize RadialMenu control style and the appearance by using available themes or cssClass property.

## Theme

In order to apply styles to the RadialMenu control, refer these 2 files namely, ej.widgets.core.min.css and ej.theme.min.css. When you refer ej.web.all.min.css file, it is not necessary to include the files ej.widgets.core.min.css and ej.theme.min.css in your project, as ej.web.all.min.css is the combination of these two.

By default, there are 13 theme support available for RadialMenu component, namely:

* flat-azure
* flat-azure-dark
* fat-lime
* flat-lime-dark
* flat-saffron
* flat-saffron-dark
* gradient-azure
* gradient-azure-dark
* gradient-lime
* gradient-lime-dark
* gradient-saffron
* gradient-saffron-dark
* bootstrap

## CSS Class

RadialMenu component's appearance can only be customized using its CSS classes. Define CSS class, as per requirement and assign the class name to cssClass property.

### Configure RadialMenu using CSS class

Define CSS class to customize the RadialMenu control.

{% highlight css %}

    <style type="text/css">

        /* Customize the radialmenu */

       .e-radialmenu .e-default, .e-radialmenu .e-outerdefault.customCss 

       {

         fill:#f00;
       } 

    </style>

{% endhighlight %}

In the HTML page, define the li items for RadialMenu component.

{% highlight razor %}

      @Html.EJ().RadialMenu("defaultRadialMenu").ImageClass("e-radial").CssClass("customCss").TargetElementId("radialtarget1").Items(items
    =>
    {
        items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/copy.png")).Text("Copy");
        items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/paste.png")).Text("Paste");
        items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/redo.png")).Text("Redo");
        items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/undo.png")).Text("Undo");
    })

{% endhighlight %}


Customize **Radial Menu** control with cssClass in script as follows.



{% highlight javascript %}
  
       function radialShow(e) {
            var target = $("#radialtarget1"), radialRadius = 150, radialDiameter = 2 * radialRadius,
            // To get Iframe positions
                iframeY = target.offset().top + e.event.clientY, iframeX = target.offset().left + e.event.clientX,
            // To set Radial Menu position within target
                x = iframeX > target.width() - radialRadius ? target.width() - radialDiameter : (iframeX > radialRadius ? iframeX - radialRadius : 0),
                y = iframeY > target.height() - radialRadius ? target.height() - radialDiameter : (iframeY > radialRadius ? iframeY - radialRadius : 0);
                radialElement.ejRadialMenu("setPosition", x, y);
            }

{% endhighlight %}


Output of RadialMenu configured based on CSS class is as follow,

![](apperance-and-styling-images\apperance-and-styling_img1.png)



