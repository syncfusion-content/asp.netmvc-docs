---
layout: post
title: Separators | Menu | ASP.NET MVC | Syncfusion
description: separators
platform: ejmvc
control: Menu
documentation: ug
---

# Separators

Separators can be added to menu items to display a horizontal bars between menu items. Separators are similar to borders and cannot be selected.**enableSeparator** is the property that is used to display the separators in the Menu control. It accepts Boolean type value. Its default value is true. 

1. Add the following code in your view page.

   ~~~ cshtml



	// Add the following code in the CSHTML page.

	<div class="imgframe">

		Html.EJ().Menu("menuControl").Items(items =>

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



		}).Width("500").EnableSeparator(true)
		
	</div>

   ~~~
   


   The following screenshot displays the output for the above code sample.

   ![](Separators_images/Separators_img1.png)

	Menu with Separators
	{:.caption}
	
2. Add the following code in your view page to display the Menu control without separator by setting EnableSeparator as false.

   ~~~ cshtml

	<div class="imgframe">

	@Html.EJ().Menu("menuControl").Items(items =>

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



		}).Width("500").EnableSeparator(false)

	</div>



   ~~~
   



The following screenshot displays the output for the above code. 

![](Separators_images/Separators_img2.png)

Menu without Separators
{:.caption}
