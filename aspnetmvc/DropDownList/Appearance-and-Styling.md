---
layout: post
title: Appearance-and-Styling
description: appearance and styling
platform: ejmvc
control: DropDownList
documentation: ug
---

# Appearance and Styling

## Popup Customization  

### Popup Height

Dropdownlist widget provides you support to customize the dimensions of the dropdown popup. By using PopupHeight property, you can set the height of the popup list. Its data type is string. 

### Popup Width

Dropdown list widget provides you support to customize the dimensions of the dropdown popup. By using PopupWidth property, you can set the width of the popup list. Its data type is string. 

### Defining the popup customizing properties

The following steps explains you the configuration of PopupHeight & PopupWidth properties in Dropdownlist

1. Add the below code snippet to render the drop down list with customized popup height and width.


   ~~~ js

		// Add a DropDownList element using the helper class in CSHTML



		@Html.EJ().DropDownList("dropdownlist").TargetID("list").PopupWidth("250px").PopupHeight("100px")

				<div id="list">

					<ul>

						<li>Art</li>

						<li>Architecture</li>

						<li>Biography</li>

						<li>Comics</li>

						<li>Sports</li>

						<li>Science</li>

					</ul>

				</div>


   ~~~
   {:.prettyprint }
   
2. Output of the above steps



   ![](Appearance-and-Styling_images/Appearance-and-Styling_img1.png)

   _Figure 19: Dropdown with popup customization property_  

## Adjusting Dropdown size

### Width

Dropdownlist widget provides you support to customize the dimensions of the dropdown textbox. By using Width property you can set the width of the dropdown textbox. Its data type is string.

### Height

Dropdownlist widget provides you support to customize the dimensions of the dropdown textbox. By using Height property, you can set the height of the dropdown textbox. Its data type is string.

### Defining the dropdown size properties

The following steps explains you the configuration of Height & Width properties in Dropdownlist

1. Add the below code snippet to render the dropdown list with customized height and width.

   ~~~ js

		// Add a DropDownList element using the helper class in CSHTML



		@Html.EJ().DropDownList("dropdownlist").TargetID("list").Height("50px").Width("250px")

				<div id="list">

					<ul>

						<li>Art</li>

						<li>Architecture</li>

						<li>Biography</li>

						<li>Comics</li>

						<li>Sports</li>

						<li>Science</li>

					</ul>

				</div>


   ~~~
   {:.prettyprint }

Output of the above steps


![](Appearance-and-Styling_images/Appearance-and-Styling_img2.png)


_Figure 20: Dropdown with dropdown textbox customization property_  

### Water Mark 

Dropdownlist widget provides the support to water mark of the dropdown textbox. The WaterMarkText defines the text that display on page load. Its data type is string.

### Defining the Water Mark property

The following steps explains the configuration of WaterMarkText properties in Dropdownlist.

1. Add the below code snippet with water mark text


{% highlight js %}

// Add a DropDownList element using the helper class in CSHTML



@Html.EJ().DropDownList("dropdownlist").TargetID("list").WatermarkText("Select")

        <div id="list">

            <ul>

                <li>Art</li>

                <li>Architecture</li>

                <li>Biography</li>

                <li>Comics</li>

                <li>Sports</li>

                <li>Science</li>

            </ul>

        </div>


{% endhighlight %}


Output of the above steps


![](Appearance-and-Styling_images/Appearance-and-Styling_img3.png)

_Figure 21: Dropdown with WaterMark property_  

## Enabling Rounded corner

Dropdownlist widget provides you support to change the appearance of dropdown textbox. By using ShowRoundedCorner you can create a rounded corner on the dropdown textbox. Its data type is Boolean.

The following steps explains you the configuration of Rounded corner of the Dropdownlist

1. Add the below code snippet to render the dropdown list with rounded corners



   ~~~ js

		// Add a DropDownList element using the helper class in CSHTML



		@Html.EJ().DropDownList("dropdownlist").TargetID("list").ShowRoundedCorner(true)        

				<div id="list">

					<ul>

						<li>Art</li>

						<li>Architecture</li>

						<li>Biography</li>

						<li>Comics</li>

						<li>Sports</li>

						<li>Science</li>

					</ul>

				</div>

   ~~~
   {:.prettyprint }


2. Output of the above steps


   ![](Appearance-and-Styling_images/Appearance-and-Styling_img4.png)


   _Figure 22: Dropdown with Rounded corner property_  

   ## Icons Support 

   You can add the icons or images with list items in dropdown popup by using sprite CSS class. The following steps explains you the configuration about the icons support with Dropdownlist


   > Note: Images for this sample are available in ‘installed location /themes/images’ and you need to define images in mentioned CSS. Henceforth the images display.


   1111.Add the below code 1. add tgh

   ~~~ js 

		// Add a DropDownList element using the helper class in CSHTML



		@Html.EJ().DropDownList("dropdownlist").TargetID("mailtoolslist").Width("200px")

				<div id="mailtoolslist">

					<ul>

						<li>

							<div class="mailtools categorize"></div>

							Categorize and Move

						</li>

						<li>

							<div class="mailtools done"></div>

							Done

						</li>



						<li>

							<div class="mailtools movetofolder"></div>

							Move to Folder

						</li>

						<li>

							<div class="mailtools newmail"></div>

							New E-mail

						</li>

						<li>

							<div class="mailtools meeting"></div>

							New Meeting

						</li>

						<li>

							<div class="mailtools reply"></div>

							Reply & Delete

						</li>

					</ul>

				</div>

   ~~~
   {:.prettyprint }



3. Configure sprite CSS styles to Dropdownlist

   ~~~ css



		<style type="text/css" class="cssStyles">

				/*controls*/

				.mailtools {

					display: block;

					background-image: url(' http://js.syncfusion.com/demos/web/images/dropdownlist/iconsapps.png');

					height: 25px;

					width: 25px;

					background-position: center center;

					background-repeat: no-repeat;

				}



					.mailtools.done {

						background-position: 0 0;

					}



					.mailtools.movetofolder {

						background-position: 0 -22px;

					}



					.mailtools.categorize {

						background-position: 0 -46px;

					}



					.mailtools.flag {

						background-position: 0 -70px;

					}



					.mailtools.forward {

						background-position: 0 -94px;

					}



					.mailtools.newmail {

						background-position: 0 -116px;

					}



					.mailtools.reply {

						background-position: 0 -140px;

					}



					.mailtools.meeting {

						background-position: 0 -164px;

					}



				.control {

					margin-left: 20px;

				}



				.ctrllabel {

					padding-bottom: 3px;

				}

		   </style>

   ~~~
   {:.prettyprint }

Output of the above steps



![](Appearance-and-Styling_images/Appearance-and-Styling_img6.png)

_Figure 23: Dropdown with Icons property_  

## Animation with Dropdown list 

This feature adds some animation effect to dropdown widget when show /hide the popup list. This is achieved by setting Boolean value to EnableAnimation property.

### Defining the Animation property

The following steps explains you the configuration of EnableAnimation properties in Dropdownlist

1. Add the below code in your view page with animation effect.





{% highlight js %}

// Add a DropDownList element using the helper class in CSHTML



@Html.EJ().DropDownList("dropdownlist").TargetID("list").EnableAnimation(true)



        <div id="list">

            <ul>

                <li>Art</li>

                <li>Architecture</li>

                <li>Biography</li>

                <li>Comics</li>

                <li>Sports</li>

                <li>Science</li>

            </ul>

        </div>

{% endhighlight %}

## Theme

Dropdownlist control’s style and appearance can be controlled based on CSS classes. In order to apply styles to the Dropdownlist control, you need to refer two files namely, ej.widgets.core.min.css and ej.theme.min.css. If the file ej.widgets.all.min.css is referred, then it is not necessary to include the files ej.widgets.core.min.css and ej.theme.min.css in your project, as ej.widgets.all.min.css is the combination of these two. 

By default, there are 12 themes support available for Dropdownlist control namely

* bootstrap-theme
* default-theme
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

## Custom class with dropdown 

CSS class can be used to customize the Dropdown control appearance. Define a CSS class as per your requirement and assign the class name to CssClass property. The data type of CssClass property is string. 

### Configuring the Custom CSS property

The following steps explains you the configuration of CssClass properties in Dropdownlist

1. Add the below code in your page to render the dropdown list.

   ~~~ html

		// Add a DropDownList element using the helper class in CSHTML



		@Html.EJ().DropDownList("dropdownlist").TargetID("list").CssClass("customclass")

				<div id="list">

					<ul>

						<li>Art</li>

						<li>Architecture</li>

						<li>Biography</li>

						<li>Comics</li>

						<li>Sports</li>

						<li>Science</li>

					</ul>

				</div>


   ~~~
   {:.prettyprint }


2. Configure the CSS styles to apply on Dropdownlist


   ~~~ css 

		  <style type="text/css">

				.customclass {

					background-color: #FFFFCC;

					font-weight: bold;

					font-family: sans-serif;

				}

		 </style>

   ~~~
   {:.prettyprint }

3. Output of the above steps


![](Appearance-and-Styling_images/Appearance-and-Styling_img7.png)

_Figure 24: Dropdown with cssClass property_  

