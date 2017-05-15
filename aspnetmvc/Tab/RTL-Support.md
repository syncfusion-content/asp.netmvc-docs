---
layout: post
title: RTL Support | Tab  | ASP.NET MVC | Syncfusion
description: rtl support
platform: ejmvc
control: Tab 
documentation: ug
---

# RTL Support

Tab control provides support for load contents in right to left format. This is achieved by setting ‘EnableRTL’ property to “true”.

The following code example is used to render the Tab element in RTL format. 

1. Add the following code in your view page to render Tab with RTL format.


   ~~~ cshtml

	// Add the following code example to the corresponding CSHTML page to render Tab in Rtl format.



	<div style="width:550px">

		@{Html.EJ().Tab("dish").Items(data =>

			   {

				   data.Add().ID("pizza").Text("Pizza Type")

					   .ContentTemplate(@<div>

						   Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

					   </div>);

				   data.Add().ID("sandwich").Text("Sandwich Type")

					   .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

				   </div>);

			   }).EnableRTL(true).Render();}

	</div>

   ~~~
   



2. The following screenshot illustrates the Tab with RTL format.

![](RTL-Support_images/RTL-Support_img1.png)


