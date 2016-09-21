---
layout: post
title: Item-Customization | Radial Menu | ASP.NET MVC | Syncfusion
description: item customization
platform: ejmvc
control: Radial Menu
documentation: ug
---

## Item Customization

You can customize individual **Radial Menu** items by using the items properties.

### Adding image and text to RadialMenu items

The **ImageUrl** property specifies the URL of the image for the items. **Text** attribute is used to specify the item text. Refer to the following code example.

You can add the page content in RTE control by referring this section.

{% highlight razor %}

        @Html.EJ().RadialMenu("defaultradialmenu").ImageClass("e-radial").TargetElementId("radialtarget1").Items(items
        =>
        {
            items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/copy.png")).Text("Copy");
            items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/paste.png")).Text("Paste");
            items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/redo.png")).Text("Redo");
            items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/undo.png")).Text("Undo");
        })     
    
{% endhighlight %}

You can display the **Radial Menu** by performing desired action on the target content while selecting the text inside the target. Therefore, call the **radialShow** method in the select action of the content. Refer the following code example and add it to the script.
    
{% highlight javascript %}

            function radialShow(e) {
                var target = $("#radialtarget2"), radialRadius = 150, radialDiameter = 2 * radialRadius,
                // To get Iframe positions
                    iframeY = target.offset().top + e.event.clientY, iframeX = target.offset().left + e.event.clientX,
                // To set Radial Menu position within target
                    x = iframeX > target.width() - radialRadius ? target.width() - radialDiameter : (iframeX > radialRadius ? iframeX - radialRadius : 0),
                    y = iframeY > target.height() - radialRadius ? target.height() - radialDiameter : (iframeY > radialRadius ? iframeY - radialRadius : 0);
                    radialEle.ejRadialMenu("setPosition", x, y);
            }


{% endhighlight %}



The following screenshot illustrates the output.

![](item-customization_images\item-customization_img1.png)

### Adding events to Radial Menu items

You can specify the click event to corresponding image/text of **Radial Menu** items for performing some specific action. You need to handle the click event in script manually for each item click.

You can add the page content in RTE control by referring to this section


{% highlight razor %}

    @{
       Html.EJ().RadialMenu("nestedradialmenu").ImageClass("imageclass").BackImageClass("backimageclass").TargetElementId("radialtarget2").Items(items =>
        {
            items.Add().Text("Copy").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/copy.png")).Click("Bold"); 
            items.Add().Text("Font").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/font.png"));              
            items.Add().Text("List").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/list.png")).Children(children =>
            {
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/list.png")).Text("List");              
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/l5.png")).Text("List");
            });
            items.Add().Text("Bold").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/font.png")).Click("bold").Children(children =>
            {
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/f1.png")).Text("Italic").Click("italic");
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/font.png")).Text("Bold").Click("bold");
            });     
            items.Add().Text("Paste).ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/paste.png")); 
            items.Add().Enabled(false).ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/undo.png")).Children(children =>
            {
                children.Add().Enabled(false).ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/undo.png"));
                children.Add().Enabled(false).ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/redo.png"));
            });
            items.Add().Text("Alignment").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/align.png")).Children(children =>
            {
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/a1.png")).Text("Left");
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/a2.png")).Text("Right");
            });                   

        }).Render();
            }

{% endhighlight %}

Add the following script in your code.
    
{% highlight javascript %}

       function radialShow(e) {
            var target = $("#radialtarget2"), radialRadius = 150, radialDiameter = 2 * radialRadius,
            // To get Iframe positions
                iframeY = target.offset().top + e.event.clientY, iframeX = target.offset().left + e.event.clientX,
            // To set Radial Menu position within target
                x = iframeX > target.width() - radialRadius ? target.width() - radialDiameter : (iframeX > radialRadius ? iframeX - radialRadius : 0),
                y = iframeY > target.height() - radialRadius ? target.height() - radialDiameter : (iframeY > radialRadius ? iframeY - radialRadius : 0);
                radialEle.ejRadialMenu("setPosition", x, y);
        }
        function italic(e) {
            rteObj.executeCommand("italic");
        }
        function bold(e) {
            rteObj.executeCommand("bold");
        }
        function copy(e) {
            rteObj.executeCommand("copy");
        }


{% endhighlight %}


The following screenshot illustrates the output.

![](item-customization_images\item-customization_img2.png)


### Badge Customization in Radial Menu Items

You can specify set badges for the items by using badge settings in radial menu. You can set value for badge and enable badge with default value.

The **Enabled** property to enable or disable badges. **Value** attribute is to set the badge value.

{% highlight razor %}

      @Html.EJ().RadialMenu("defaultradialmenu").ImageClass("e-radial").TargetElementId("radialtarget1").Items(items
    =>
    {
        items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/copy.png")).Text("Copy")..Badge(badge => badge.Enabled(true).Value(2));
        items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/paste.png")).Text("Paste");
        items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/redo.png")).Text("Redo");
        items.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/undo.png")).Text("Undo");
    })

{% endhighlight %}

Add the following script in your code.
    
{% highlight javascript %}

       function radialShow(e) {
            var target = $("#radialtarget2"), radialRadius = 150, radialDiameter = 2 * radialRadius,
            // To get Iframe positions
                iframeY = target.offset().top + e.event.clientY, iframeX = target.offset().left + e.event.clientX,
            // To set Radial Menu position within target
                x = iframeX > target.width() - radialRadius ? target.width() - radialDiameter : (iframeX > radialRadius ? iframeX - radialRadius : 0),
                y = iframeY > target.height() - radialRadius ? target.height() - radialDiameter : (iframeY > radialRadius ? iframeY - radialRadius : 0);
                radialEle.ejRadialMenu("setPosition", x, y);
        }

{% endhighlight %}


The following screenshot illustrates the output.

![](item-customization_images\item-customization_img3.png)

### Slider Customization in Radial Menu Items

You can customize the Radial Menu with slider settings.The **data-ej-type** property specifies the type of radial menu item, where you can set the type for RadialMenu item.

You can customize the **Radial Menu** slider settings by using the **Ticks**, **StrokeWidth** and **LabelSpace** properties. The **Ticks** property ppecifies the slider ticks for radial menu item.**StrokeWidth** attribute is used to specify the slider's stroke width value.**LabelSpace** attribute is used to specify the value of slider label space.

Refer to the following code example.

You can add slidersettings in radial menu items by referring this section.

{% highlight razor %}

    @{
        Html.EJ().RadialMenu("nestedradialmenu").ImageClass("imageclass").BackImageClass("backimageclass").TargetElementId("radialtarget2").Items(items =>
        {
            items.Add().Text("Copy").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/copy.png")).Click("Bold"); 
            items.Add().Text("Font").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/font.png").Type(MenuItemType.Slider).SliderSettings(slider => slider.StrokeWidth(1).Ticks(new List<double> { 0, 2, 4, 6, 8, 10, 12, 14 })));              
            items.Add().Text("List").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/list.png")).Children(children =>
            {
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/list.png")).Text("List");              
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/l5.png")).Text("List");
            });
            items.Add().Text("Bold").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/font.png")).Click("bold").Children(children =>
            {
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/f1.png")).Text("Italic").Click("italic");
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/font.png")).Text("Bold").Click("bold");
            });     
            items.Add().Text("Paste).ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/paste.png")); 
            items.Add().Enabled(false).ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/undo.png")).Children(children =>
            {
                children.Add().Enabled(false).ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/undo.png"));
                children.Add().Enabled(false).ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/redo.png"));
            });
            items.Add().Text("Alignment").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/align.png")).Children(children =>
            {
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/a1.png")).Text("Left");
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/a2.png")).Text("Right");
            });                   

        }).Render();
            }

{% endhighlight %}

Add the following script in your code.
    
{% highlight javascript %}

         function radialShow(e) {
            var target = $("#radialtarget2"), radialRadius = 150, radialDiameter = 2 * radialRadius,
            // To get Iframe positions
                iframeY = target.offset().top + e.event.clientY, iframeX = target.offset().left + e.event.clientX,
            // To set Radial Menu position within target
                x = iframeX > target.width() - radialRadius ? target.width() - radialDiameter : (iframeX > radialRadius ? iframeX - radialRadius : 0),
                y = iframeY > target.height() - radialRadius ? target.height() - radialDiameter : (iframeY > radialRadius ? iframeY - radialRadius : 0);
                radialEle.ejRadialMenu("setPosition", x, y);
          }     


{% endhighlight %}

The following screenshot illustrates the output.

![](item-customization_images\item-customization_img4.png)

