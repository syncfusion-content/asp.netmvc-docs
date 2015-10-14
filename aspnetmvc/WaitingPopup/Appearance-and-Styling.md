---
layout: post
title: Appearance and Styling | WaitingPopup | ASP.NET MVC | Syncfusion
description: appearance and styling 
platform: ejmvc
control: WaitingPopup
documentation: ug
---

# Appearance and Styling 

## Custom Text

WaitingPopup control provides support for Custom Text to mention any message inside the pop-up panel.  You can specify a custom text through the option Text that displays when the Waiting Popup is loading.

The following steps explains you the configuration of the custom text for WaitingPopup control.

1. In the VIEW page, add a helper element to render WaitingPopup widget.

   ~~~ cshtml

	<div id="target">

		@Html.EJ().WaitingPopup("target").ShowOnInit(true).Text("Loading... Please wait...")

	</div>
   ~~~
   



2. Add the following styles to render WaitingPopup widget.

   ~~~ css
   
	<style type="text/css" class="cssStyles">

		#control 
		{

		height: 320px;

		width: 600px;

		}

	</style>
   ~~~
   




Execute the above code to render the following output.



![](Appearance-and-Styling_images/Appearance-and-Styling_img1.png)

Custom Text in WaitingPopup
{:.caption}

### Template

WaitingPopup widget provides support for Template to customize the appearance of it by including HTML content instead of the default image.

The following steps explains you on how to define template to display a text and image for WaitingPopup control.

1. In the VIEW page, add a helper element to configure WaitingPopup widget.

   ~~~ cshtml

	<div id="target">

		@Html.EJ().WaitingPopup("target").ShowOnInit(true).Template("#content")

		<div id="content">

		<div class="block">

			<div class="logo"></div>

			<div class="txt">

			<p>Create cutting edge </p>

			<p><b>HTML5</b> web application </p>

			<p>with ease </p>

			</div>

		</div>

		<div class="loader"></div>

		</div>

	</div>

   ~~~
   


2. In CSS, you can configure the custom styles for WaitingPopup.
    
   N> Images for this sample are available ‘installed location /Content/images’ and we need to define images in mentioned CSS. Henceforth the images will display._

   ~~~ css

	<style type="text/css" class="cssStyles">

		#waitingPopUp 
		{

			height: 320px;

			width: 600px;

			margin: 0 auto;

		}

		.block 
		{

			height: 76px;

		}

		.logo 
		{

			background-image: url("../Image/js_logo.png");

			float: left;

			height: 100%;

			width: 77px;

			margin-right: 15px;

		}

		.txt 
		{

			float: left;

			font-size: 17px;

			height: 100%;

			text-align: left;

		}

		.txt p 
		{

			margin: 0;

		}

		.loader 
		{

			background: url("../Image/load dark.gif") no-repeat scroll -5px 18px transparent;

			height: 40px;

			width: 100%;

		}

		#content 
		{

			cursor: default;

			height: 112px;

			width: 275px;

		}

	</style>

   ~~~
   



Execute the above code to render the following output.


![](Appearance-and-Styling_images/Appearance-and-Styling_img3.png)

WaitingPopup with Custom Template
{:.caption}

### CSS Class

You can use the CSS class to customize the WaitingPopup control appearance. Define a CSS class as per requirement and assign the class name to CssClass property.

The following steps allows you to configure CSS class for an auto-complete textbox.

1. In the VIEW page, add a helper element to configure WaitingPopup widget.

   ~~~ cshtml
   
	<div id="target">

	 @Html.EJ().WaitingPopup("target").ShowOnInit(true).CssClass("custom").Text("Loading... Please wait...")</div>
   ~~~
   


2. Define CSS class for customizing the WaitingPopup widget.

   ~~~ css

	<style type="text/css" class="cssStyles">

	/*Customize the panel property*/

		#waitingPopUp 
		{

		height: 320px;

		width: 600px;

		margin: 0 auto;

		}

		/* Customize the WaitingPopup */

		.customStyle
		{

		background-color:darkred;

		font-style:italic;

		font-weight:bolder;

		opacity:0.5;

		}

	</style>

   ~~~
   


The following screenshot displays the output for the above code.

![](Appearance-and-Styling_images/Appearance-and-Styling_img4.png)

WaitingPopup with customized CSS
{:.caption}




