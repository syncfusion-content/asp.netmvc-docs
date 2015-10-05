---
layout: post
title: Look and feel | Menu | ASP.NET MVC | Syncfusion
description: look and feel
platform: ejmvc
control: Menu
documentation: ug
---

# Look and feel

Essential JavaScript controls feature 12 built-in themes, six flat and gradient effects, and also supports custom skin options for user-defined themes.

12 themes support available for Menu control namely,

* default-theme
* flat-azure-dark
* flat-lime
* flat-lime-dark
* flat-saffron
* flat-saffron-dark
* gradient-azure
* gradient-azure-dark
* gradient-lime
* gradient-lime-dark
* gradient-saffron
* gradient-saffron-dark

## Cssclass

Menu control also customizes its appearance using user-defined CSS and custom skin options (colors and backgrounds). To apply custom themes you can use the “CssClass” property. “CssClass” property sets the root class for Menu control theme.

Using this CssClass you can override the existing styles under the theme style sheet. The theme stylesheet applies theme-specific styles like colors and backgrounds. In the following sample the value of “CssClass” property is set as “Purple-dark”. Purple-dark is added as root class to Menu control at the runtime. From this root class you can customize the Menu control theme.

1. Add the following code in your View page.

   ~~~ cshtml

	// Add the following code in your CSHTML page.

	<div class="imgframe">

			@Html.EJ().Menu("menucontrol").Items(items =>

			{

				items.Add().Id("Home").Text("Home").Children(child =>

					{

						child.Add().Text("Foundation");

						child.Add().Text("Launch");

						child.Add().Text("About").Children(child1 =>

						{

							child1.Add().Text("Company");

							child1.Add().Text("Location");

						});

					});

				items.Add().Text("Services").Children(child =>

					{

						child.Add().Text("Consulting");

						child.Add().Text("Outsourcing");

					});

				items.Add().Text("About");

				items.Add().Id("Contact").Text("Contact Us").Children(child =>

					{

						child.Add().Text("Contact number");

						child.Add().Text("E-mail");

					});

				items.Add().Id("Careers").Text("Careers").Children(child =>

					 {



						 child.Add().Text("Position").Children(child1 =>

								 {

									 child1.Add().Text("Developer");

									 child1.Add().Text("Manager");

								 });

						 child.Add().Text("Apply online");

					 });



			}).Width("500").CssClass("Purple-dark")

	</div>



   ~~~
   

2. Add the following code in your style section.


   ~~~ css

	<style type="text/css" class="cssStyles">

		.Purple-dark {

			background: pink;

		}



		.Purple-dark.e-horizontal .e-list > a {

				color: #4800ff;

		 }

	</style>

   ~~~
   

Following screenshot displays the output of the above code.

![](Look-and-feel_images/Look-and-feel_img1.png)

Look and feel of a Menu
{:.caption}
