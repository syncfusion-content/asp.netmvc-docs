---
layout: post
title: Scroll Support | Tab  | ASP.NET MVC | Syncfusion
description: scroll support
platform: ejmvc
control: Tab 
documentation: ug
---

# Scroll Support

Tab control provides you scrolling support on Tab items to display a larger number of tabs with scroll buttons to get rid of the extending page size. The enabled Scroll buttons can be used to traverse through the elements.

By default, Tab header is rendered without scroll button. You can add the scroll button by setting the "EnableTabScroll" property to "true". When you move the cursor over the Tab header the scroll button is displayed.   



You can use the following code example to render the Tab widget with scroll button.

1. Add the following code in your view page to create a simple Tab with scroll button.


{% highlight CSHTML %}



@*Add the following code example to the corresponding CSHTML page to render Tab with scroll button.*@

<div style="width: 550px">

	@{Html.EJ().Tab("dish").Items(data =>

   {

	   data.Add().ID("pizza").Text("Pizza Type")

		   .ContentTemplate(@<div>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</div>);

	   data.Add().ID("pasta").Text("Pasta Type")

		   .ContentTemplate(@<div>Pasta cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</div>);

	   data.Add().ID("burger").Text("Burger Type")

		   .ContentTemplate(@<div>Burger cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</div>);

	   data.Add().ID("sandwich").Text("Sandwich Type")

		   .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</div>);

	   data.Add().ID("spaghetti").Text("Spaghetti Type")

		   .ContentTemplate(@<div>Spaghetti cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</div>);

	   data.Add().ID("ramen").Text("Ramen Type")

		   .ContentTemplate(@<div>Ramen cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</div>);

   }).EnableTabScroll(true).Render();}

</div>


{% endhighlight %}


The following screenshot illustrates you the Tab control with scroll button. 

![](Scroll-Support_images/Scroll-Support_img1.png)

Tab control with scroll support
{:.caption}



