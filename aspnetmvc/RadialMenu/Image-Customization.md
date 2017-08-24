---
layout: post
title: Image Customization | RadialMenu | ASP.NET MVC | Syncfusion
description: image customization
platform: ejmvc
control: Radial Menu
documentation: ug
---

## Image Customization

You can customize the **Radial Menu’s** Center and Back images by using the **ImageClass** and **BackImageClass** properties. Every menu item can be added with image using **url** property. By using this **ImageClass** attribute, you can customize the **Radial Menu** center image. 

Sub-Items are also supported in the **Radial Menu**. To navigate Sub-Items, click the arrows in the outer ring and it displays the corresponding sub-items group. Clicking the center button when a sub-items group is shown, displays the items on the previous level. Nested **Radial Menu** has the second level back button. In this case, you can use the **BackImageClass** attribute to change your second level back button. **BackImageClass** is used to customize the **nestedRadialmenu** back image. Refer to the following code example.

You can add the page content with text-area by referring to this section.

{% highlight razor %}

    @{
       Html.EJ().RadialMenu("nestedRadialMenu").ImageClass("image-class").BackImageClass("backimage-class").TargetElementId("radialTarget2").Items(items =>
        {
            items.Add().Text("Copy").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/copy.png"));
            items.Add().Text("Font").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/font.png")).Children(children =>
            {
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/f1.png")).Text("Italic");
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/font.png")).Text("Bold");
            });
            items.Add().Text("Table").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/table.png"));
            items.Add().Text("List").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/list.png")).Children(children =>
            {
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/l1.png")).Text("List");
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/l2.png")).Text("List");
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/l3.png")).Text("List");
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/l4.png")).Text("List");
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/l5.png")).Text("List");
            });
            items.Add().Text("Paste").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/paste.png")).Children(children =>
            {
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/c1.png")).Text("Paste");
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/c2.png")).Text("Paste");
            });
            items.Add().Text("Sort").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/sort.png")).Children(children =>
            {
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/s1.png")).Text("Sort");
                children.Add().ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/s2.png")).Text("Sort");
            });       
            items.Add().Text("Alignment").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/align.png")).Children(children =>
            {
                children.Add().Text("Left").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/a1.png")).Click("left");
                children.Add().Text("Right").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/a2.png")).Click("right");
            });
            items.Add().Text("Draw").ImageURL(Url.Content("mvc.syncfusion.com/demos/web/Images/RadialMenu/draw.png"));

        }).Render();
            }
    
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

Add the following styles in your code.
    
{% highlight css %}

    <style type="text/css" class="cssStyles">
        .e-radialmenu .image-class
        {
            background-image: url("mvc.syncfusion.com/demos/web/Images/RadialMenu/main.png");
        }
        
        .e-radialmenu .backimage-class
        {
            background-image: url("mvc.syncfusion.com/demos/web/Images/RadialMenu/Back_button.png");
        }
    </style>


{% endhighlight %}



The following screenshot illustrates the output.

![](image-customization_images\image-customization_img1.png)

Radial Menu - Image Customization – Main menu
{:.caption}

When you click the arrow, it navigates to the child item as illustrated in the following screenshot.

![](image-customization_images\image-customization_img2.png)

Radial Menu- Image Customization – Child menu 
{:.caption}




