---
layout: post
title: TargetId
description: targetid
platform: ejmvc
control: NavigationDrawer
documentation: ug
---

# TargetId

This property is used to define the target Id for Navigation Drawer. The drawer opens while you click on the specified target element.



{% highlight js %}

@{

    @Html.EJ().Button("drawerTarget").Text("Open Drawer")

    @Html.EJ().NavigationDrawer("navpane").Position(NavigationDrawerPosition.Fixed).TargetId("drawerTarget").ContentTemplate(@<div>

        @Html.EJ().ListView("list").Width(300).Items(items =>

         {

             items.Add().Text("Home");

             items.Add().Text("Profile");

             items.Add().Text("Photos");

             items.Add().Text("Location");

         })

    </div>)

}

<style>

    #drawerTarget {

        top: 200px;

        left: 600px;

        position: absolute;

    }

</style>



{% endhighlight %}



The following screenshots illustrates the output.

![](TargetId_images/TargetId_img1.png)





![](TargetId_images/TargetId_img2.png)



