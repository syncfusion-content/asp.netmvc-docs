---
layout: post
title: Getting Started | RadialMenu | ASP.NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: RadialMenu
documentation: ug
---

# Getting Started

## Create your first Radial Menu control in MVC

In this section, you can learn how to create a simple Radial Menu in the MVC application.

![](Getting-Started_images/Getting-Started_img1.png)



## Create a simple Radial Menu

The following steps guide you to add a Radial Menu control.

You can create an MVC Project and add the necessary assemblies, styles, and scripts to it. Refer to the [MVC-Getting Started.](http://docs.syncfusion.com/aspnetmvc/radialmenu/getting-started)

Add the following code example to the corresponding view page to render the Radial Menu.



{% highlight CSHTML %}

@Html.EJ().RadialMenu("radialmenu").Items(items =>

{

items.Add().ImageURL("http://js.syncfusion.com/ug/web/content/radial/copy.png").Text("Copy");

    items.Add().ImageURL("http://js.syncfusion.com/ug/web/content/radial/paste.png").Text("Paste");

    items.Add().ImageURL("http://js.syncfusion.com/ug/web/content/radial/Redo.png").Text("Redo");

    items.Add().ImageURL("http://js.syncfusion.com/ug/web/content/radial/Undo.png").Text("Undo"); })

{% endhighlight %}



Refer to the following code example to add target content to the Radial Menu.

{% highlight CSHTML %}



<div id="radialtarget">  

  <textarea id="textarea">



Syncfusion Essential JavaScript Studio for Mobile contains the following built-in theme support with that you can achieve the native appearance and functionality of iOS7, android and windows platforms in your mobile applications.



1.   iOS7



2.   Android



3.   Windows



4.   Flat



By default, the respective render modes are chosen based on the device where the application runs. You can also force and use a particular theme to a control or the whole application that is discussed in later sections. All of the above widgets are highly customizable and also designed with high performance in mind.

	</textarea>

 </div>



<!--Adds Style for Content-->

<style type="text/css" class="cssStyles">

#textarea 
{

	width: 100%;

	height: 270px;

}

</style>  

{% endhighlight %}



You can set the ID of target content to the Radial Menu as illustrated in the following code example. 

{% highlight CSHTML %}

@Html.EJ().RadialMenu("radialmenu").TargetElementId("radialtarget").Items(items =>

{

items.Add().ImageURL("http://js.syncfusion.com/ug/web/content/radial/copy.png").Text("Copy");

    items.Add().ImageURL("http://js.syncfusion.com/ug/web/content/radial/paste.png").Text("Paste");

    items.Add().ImageURL("http://js.syncfusion.com/ug/web/content/radial/Redo.png").Text("Redo");

    items.Add().ImageURL("http://js.syncfusion.com/ug/web/content/radial/Undo.png").Text("Undo"); })

{% endhighlight %}



You can display the Radial Menu by performing the desired action on the target while selecting the text inside the target. Therefore, call the show method in the select action of the content. Refer to the following code example and add it to the script section.

{% highlight js %}

<script type="text/javascript">

	$(function () 
	{

		$("#textarea").select(function (e) 
		{

			$('#radialmenu').ejRadialMenu("show");

		});

	});
	
</script>

{% endhighlight %}



Run the above code and select any text inside the target. The settings icon is displayed. Click that icon to render the following output.

![](Getting-Started_images/Getting-Started_img2.png)



