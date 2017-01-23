---
layout: post
title: Getting Started | NavigationDrawer | ASP.NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: NavigationDrawer
documentation: ug
---

# Getting Started

## Create your first Navigation Drawer control in MVC

In this section, you can learn how to create a simple navigation drawer.


![](Getting-Started_images/Getting-Started_img1.png)


### Create Navigation Drawer Widget

The following steps guide you in adding a Navigation Drawer control for a web application that displays a list of items such as home, profile, photos and location where you can navigate to desired page by clicking on the option available in the drawer. 

You can create an MVC Project and add the necessary assemblies, styles and scripts to it.  Refer to the [MVC-Getting Started.](http://help.syncfusion.com/aspnetmvc/navigationdrawer/getting-started)

To add a Navigation Drawer control, call NavigationDrawer helper. You can display the navigational item as a list by using ListView. This is achieved by creating the ListView inside the content template. You can set the text for list items by using Text property. You can paste the following code in corresponding view page.


{% highlight CSHTML %}

@Html.EJ().NavigationDrawer("navpane").Width(300).Position(NavigationDrawerPosition.Fixed).ContentTemplate(@<div>

@Html.EJ().ListView("list").ShowHeader(false).Width(300).Items(items =>

	 {

		 items.Add().Text("Home");

		 items.Add().Text("Profile");

		 items.Add().Text("Photos");

		 items.Add().Text("Location");

	 });

</div>)



{% endhighlight %}


Create the target element as follows to display the drawer by clicking target icon.

{% highlight CSHTML %}

<div class="navi">

     <div id="target" class="icon-target"> Drawer</div>

</div>

{% endhighlight %}



To set the target icon image from sprite and to position the target icon properly use the following code example.

{% highlight css %}

<style>

	[class*="icon-"]

	{

		background-image: url("http://js.syncfusion.com/ug/web/content/drawer/sprite.png");

	}

 .icon-target 

	{

		 background-position: 0 -331px;

		 font-size: 34px;

		 height: 48px;

		 position: absolute;

		 text-indent: 50px;

		 top: -3px;

		 width: 48px;

		 z-index: 3;

	 }

 .navi 

	{

		background: none repeat scroll 0 0 #C4C4B4;

		color: #fff;

		height: 45px;

		padding-left: 5px;

		width: 100%;

	}

   body

	 {

		background: none repeat scroll 0 0 #ece9d8;

	 }

</style>



{% endhighlight %}



Set the TargetId property as follows.

{% highlight CSHTML %}

@Html.EJ().NavigationDrawer("navpane").Width(300).Position(NavigationDrawerPosition.Fixed).TargetId("target").ContentTemplate(@<div>

@Html.EJ().ListView("list").ShowHeader(false).Width(300).Items(items =>

	 {

		 items.Add().Text("Home");

		 items.Add().Text("Profile");

		 items.Add().Text("Photos");

		 items.Add().Text("Location");

	 });

</div>)

{% endhighlight %}


Run the application to render the following output. 

![](Getting-Started_images/Getting-Started_img2.png)



You can display the drawer either by clicking on the target icon or by swiping from left on the page. Refer to the following screenshot.

![](Getting-Started_images/Getting-Started_img3.png)



You can set the images for Navigation Drawer by using the ImageClass property as follows.    

{% highlight CSHTML %}

@Html.EJ().NavigationDrawer("navpane").Width(300).Position(NavigationDrawerPosition.Fixed).TargetId("target").ContentTemplate(@<div>

@Html.EJ().ListView("list").ShowHeader(false).Width(300).Items(items =>

 {

	 items.Add().Text("Home").ImageClass("icon-home");

	 items.Add().Text("Profile").ImageClass("icon-profile");

	 items.Add().Text("Photos").ImageClass("icon-photos");

	 items.Add().Text("Location").ImageClass("icon-location");

 });

</div>)



{% endhighlight %}



You can define the image classes specified for the list items as follows.

{% highlight css %}

<style>

	#navpane [class*="icon-"]

	{

		width: 35px;

		height: 35px;

	}

	.icon-home

	{

		background-position: 0 0;

	}

	.icon-profile

	{

		background-position: 0 -180px;

	}

	.icon-photos

	{

		background-position: 0 -120px;

	}

	.icon-location

	{

		background-position: 0 -58px;

	}    
</style>



{% endhighlight %}



Run the application to render the following output. 

![](Getting-Started_images/Getting-Started_img4.png)



Create corresponding content elements for each options in the navigation list as follows.



{% highlight CSHTML %}

<!-- Home Page Content-->

<div id="Home">

  The Home screen allows you to choose the specific content type displayed.

</div>

<!-- Profile Page Content-->

<div id="Profile" style="display: none">

   The Profile page content is displayed.

</div>

<!-- Photos Page Content-->

<div id="Photos" style="display: none">

    The Photos page content is displayed.

</div>

<!-- Location Page Content-->

<div id="Location" style="display: none">

     The Location page content is displayed.

</div>

</div>

{% endhighlight %}



You can load the desired content for the navigation items by updating the content through MouseDown handler of ListView. You can define the handler and pass the method name with MouseDown attribute through listViewSettings. Also to know which item’s content is being loaded in the page, make the list selection to persist in the drawer by setting persistSelection as true. Refer to the following code example.



{% highlight CSHTML %}

@Html.EJ().NavigationDrawer("navpane").Width(300).Position(NavigationDrawerPosition.Fixed).TargetId("target").ContentTemplate(@<div>

@Html.EJ().ListView("list").ShowHeader(false).ClientSideEvents(click => click.MouseDown("slideMenuClick")).PersistSelection(true).Width(300).Items(items =>

 {

	 items.Add().Text("Home").ImageClass("icon-home");

	 items.Add().Text("Profile").ImageClass("icon-profile");

	 items.Add().Text("Photos").ImageClass("icon-photos");

	 items.Add().Text("Location").ImageClass("icon-location");

 });

</div>)

{% endhighlight %}



In the mouse down handler, you can hide the other content and display the respective selected item’s content.



{% highlight js%}

<script type="text/javascript">

	function slideMenuClick(e) 
	{

			$('#Home, #Profile, #Photos, #Location').hide(); //Hiding all other contents

			$('#' + e.text).show(); //Displaying the content based on the text of item selected

			$("#navpane").ejNavigationDrawer("close");

	}

</script>

{% endhighlight %}



Run the application to render the following output. 

![](Getting-Started_images/Getting-Started_img5.png)



