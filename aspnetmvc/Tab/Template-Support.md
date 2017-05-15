---
layout: post
title: Template Support | Tab  | ASP.NET MVC | Syncfusion
description: template support
platform: ejmvc
control: Tab 
documentation: ug
---

# Template Support

## ASP.NET MVC

The Content template option provided in MVC is used to specify the HTML elements inside the Tab control. We can use this option to load any HTML elements and showcase it in the Tab panels as per our requirement.

The following code block showcases how to use content template option in the Tab control.



{% highlight CSHTML %}



<div style="width:650px">

@{Html.EJ().Tab("pizza").Items(data =>

   {

	   data.Add().ID("garden").Text("GARDEN FRESH (Veg)")

		   .ContentTemplate(@<div>

			<img src="~/Content/accordion/garden-veggie.png" alt="garden-fresh" />

			<div class="ingredients">

				Rate    : $50

				<br />

				Ingredients : cheese, onions, green capsicums & tomatoes.

			</div>

		</div>);

	   data.Add().ID("corn").Text("CORN & SPINACH (Veg)")

		   .ContentTemplate(@<div>

			<img src="~/Content/accordion/corn-and-spinach-05.png" alt="garden-fresh" />

			<div class="ingredients">

				Rate    : $70

				<br />

				Ingredients : cheese, sweet corn & green capsicums.

			</div>

		</div>);

	   data.Add().ID("chicken").Text("CHICKEN DELITE (Non-veg)")

		   .ContentTemplate(@<div>

			<img src="~/Content/accordion/chicken-delite.png" alt="garden-fresh" />

			<div class="ingredients">

				Rate    : $100

				<br />

				Ingredients : cheese, chicken chunks, onions & pineapple chunks.

			</div>

		</div>);

   }).Render();}

</div>


{% endhighlight %}




Output:

![](Template-Support_images/Template-Support_img1.png)

Tab control with template support
{:.caption}



