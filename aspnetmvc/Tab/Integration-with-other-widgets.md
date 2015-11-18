---
layout: post
title: Integration with other widgets | Tab  | ASP.NET MVC | Syncfusion
description: integration with other widgets
platform: ejmvc
control: Tab 
documentation: ug
---

# Integration with other widgets

You can provide more customization to the Tab with Rating control as content in it for describing the item rating value.

The Essential ASP.NET MVC Rating control provide you an intuitive rating experience that allows you to select the number of stars that represents the rating. For more information about the rating, you can refer the following link:

<http://help.syncfusion.com/aspnetmvc/tab/integration-with-other-widgets>

The following code example explains you the Rating control creation. The input element is used to create the rating control. Render the input element as rating control using the input element id. 

1. Add the following code in your view page to render Tab with other widget (rating).



{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Tab with other widgets.



<div style="width:550px">

@{Html.EJ().Tab("dishtab").Items(data =>

	   {

		   data.Add().ID("pizzatype").Text("Pizza Type")

			   .ContentTemplate(@<div>Rating:@Html.EJ().Rating("PRating").Value(4)

				   Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

			   </div>);

		   data.Add().ID("sandwichtype").Text("Sandwich Type")

			   .ContentTemplate(@<div>Rating:@Html.EJ().Rating("SRating").Value(4)

			   Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

		   </div>);

	   }).Render();}

</div>

{% endhighlight %}

To render the rating controls in the first Tab element refer the styles mentioned in the following code example. 

1. Add the following styles to render Tab.

   ~~~ css

	<style type="text/css" class="cssStyles">

			.dishRating 
			{

				position: absolute;

				margin: -31px 0px 0px 80px;

			}       

	</style>

   ~~~
   


2. The following screenshot illustrates the Tab content with rating control. 

![](Integration-with-other-widgets_images/Integration-with-other-widgets_img1.png)

Tab content section with Rating Control
{:.caption}


