---
layout: post
title: Dimension | Radial Menu |ASP.NET MVC | Syncfusion
description: dimension
platform: ejmvc
control: Radial Menu
documentation: ug
---


## Dimension

You can customize **Radial Menu** dimension by using **Radius** and **Position** properties.

### Radius

You can customize the **Radial Menu** size by using the **Radius** property. By default, the **Radial Menu** Radius is set as 150px. Refer to the following code example.

{% highlight razor %}

         @Html.EJ().RadialMenu("defaultRadialMenu").ImageClass("e-radial").TargetElementId("radialtarget1").Items(items
        =>
        {
            items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/font.png")).Text("Bold");
            items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/f1.png")).Text("Italic");
            items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/align.png")).Text("Align");
            items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/sort.png")).Text("Sort");
        }).Radius(150).Render();           
    
{% endhighlight %}

Add the following script in your code.
    
{% highlight javascript %}

        function radialShow(e) {
                var target = $("#radialRarget2"), radialRadius = 150, radialDiameter = 2 * radialRadius,
                // To get Iframe positions
                    iframeY = target.offset().top + e.event.clientY, iframeX = target.offset().left + e.event.clientX,
                // To set Radial Menu position within target
                    x = iframeX > target.width() - radialRadius ? target.width() - radialDiameter : (iframeX > radialRadius ? iframeX - radialRadius : 0),
                    y = iframeY > target.height() - radialRadius ? target.height() - radialDiameter : (iframeY > radialRadius ? iframeY - radialRadius : 0);
                    radialElement.ejRadialMenu("setPosition", x, y);
            }

{% endhighlight %}

The following screenshot illustrates the **Radial Menu** while clicking on the settings icon.

![](dimension-images\dimension_img2.png)

### Position 

To display the **Radial Menu** in the web page in a specific area, we can use the **Position** property. By default, the **Radial Menu** Position is set as null. 

Refer to the following code example.

{% highlight razor %}

         @Html.EJ().RadialMenu("defaultRadialMenu").ImageClass("e-radial").TargetElementId("radialtarget1").Items(items
        =>
        {
            items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/copy.png")).Text("Copy");
            items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/paste.png")).Text("Paste");
            items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/redo.png")).Text("Redo");
            items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/undo.png")).Text("Undo");
        }).Radius(150).Render();           
    
{% endhighlight %}


Add the following script in your code.
    
{% highlight javascript %}

        function radialShow(e) {
                var target = $("#radialTarget2"), radialRadius = 150, radialDiameter = 2 * radialRadius,
                // To get Iframe positions
                    iframeY = target.offset().top + e.event.clientY, iframeX = target.offset().left + e.event.clientX,
                // To set Radial Menu position within target
                    x = iframeX > target.width() - radialRadius ? target.width() - radialDiameter : (iframeX > radialRadius ? iframeX - radialRadius : 0),
                    y = iframeY > target.height() - radialRadius ? target.height() - radialDiameter : (iframeY > radialRadius ? iframeY - radialRadius : 0);
                    radialElement.ejRadialMenu("setPosition", x, y);
            }

{% endhighlight %}



The following screenshot illustrates the output while selecting the text in the page.

![](dimension-images\dimension_img4.png)

