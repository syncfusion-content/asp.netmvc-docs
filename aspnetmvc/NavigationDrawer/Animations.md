---
layout: post
title: Animations | NavigationDrawer | ASP.NET MVC | Syncfusion
description: animations
platform: ejmvc
control: NavigationDrawer
documentation: ug
---

# Animations

You can set the transition type of the Navigation Drawer by using type property. The possible transition types are slide and overlay.

* Slide - both navigation panel and content page slides towards left/right direction to view the navigation panel items.
* Overlay - Only the navigation panel slides over the content page to view the navigation panel items. That is, part of the content page is hidden under navigation panel.



N> Transition slide type works only with fixed position.

The default value is Overlay.



{% highlight CSHTML %}

@{

@Html.EJ().Button("drawerTarget").Text("Open Drawer")

@Html.EJ().NavigationDrawer("navpane").Width(300).Type(NavigationDrawerType.Slide).TargetId("drawerTarget").Position(NavigationDrawerPosition.Fixed).ContentTemplate(@<div>

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

	#drawerTarget 
	{

		top: 200px;

		left: 600px;

		position: absolute;

	}

</style>

<script>

    $("#drawerTarget").click(function () {

        $("#navpane").ejNavigationDrawer("open");

    });

</script>    



{% endhighlight %}



The following screenshot illustrates the output.

![](Animations_images/Animations_img2.png)





![](Animations_images/Animations_img3.png)



