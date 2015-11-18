---
layout: post
title: Getting Started | Tab  | ASP.NET MVC | Syncfusion
description: getting started 
platform: ejmvc
control: Tab 
documentation: ug
---

# Getting Started 

This section explains briefly about how to create a Tab Control in your application with ASP.NET MVC.

## Create your first Tab Control in MVC

The ASP.NET MVCTab control is an interface that displays the content in multiple sections. A TabPanel consists of HeaderText as well as a ContentTemplate. Tab is useful for a dashboard that is having limited space. The following section guides you to customize the Tab for displaying Hotel menu items, its rate details and the ingredients on demand.



![](Getting-Started_images/Getting-Started_img1.png)

Tab control with Hotel Menu items
{:.caption}


### Create Tab Control

The ASP.NET MVCTab widget basically builds a dynamic, interactive, menu-driven interface from your content. The content can be text, graphics or HTML. You can create the Tab headers using Text and Content templateproperty

The following steps are used to create Tab control.  

1. You can create an MVC Project and add necessary Dll and script with the help of the given [MVC-Getting Started](http://help.syncfusion.com/aspnetmvc/tab/getting-started) Documentation.
2. Add the mentioned code to the corresponding view page for Tab rendering.


   ~~~ cshtml


	@Html.EJ().Tab("DishType").Items(data =>

	{

		data.Add().ID("pizzamenu").Text("Pizza Menu").ContentTemplate(@<div></div>);

		data.Add().ID("pizzatype").Text("Pizza Type").ContentTemplate(@<div></div>);

		data.Add().ID("sandwichtype").Text("Sandwich Type").ContentTemplate(@<div></div>);

	})

   ~~~
   




The following output is displayed.



![](Getting-Started_images/Getting-Started_img2.png)' 

Tab control with Header

{:.caption}


### Configure Content

In this application, a detailed description is provided to each item. You can specify the contents in the Tab section within the Content template. 


{% highlight CSHTML %}

@Html.EJ().Tab("DishType").Items(data =>

{

data.Add().ID("pizzamenu").Text("Pizza Menu").ContentTemplate(@<div> Rating:

@Html.EJ().Rating("RatingPizza").Value(4).Precision(Precision.Exact)



<!--Food item description-->

<p>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</p>

</div>);

})

{% endhighlight %}


You can provide more customization to the Tab by using rating control, to describe an item’s price.

### Create the Rating 

The ASP.NET MVCRating control provides an intuitive rating experience that allows you to select the number of stars that represents the rating. The following code example explains you the creation of rating control. We can create the Rating control using html helper. We can render the rating control and its description inside the content template of first tab control.

For more information about rating, refer to the following link: 

<http://help.syncfusion.com/aspnetmvc>

{% highlight CSHTML %}

<!--Use the following codes with above Html contents-->



@Html.EJ().Tab("DishType").Items(data =>

{

data.Add().ID("pizzamenu").Text("Pizza Menu").ContentTemplate(@<div> Rating:

@Html.EJ().Rating("RatingPizza").Value(4).Precision(Precision.Exact)



<!--Food item description-->

<p>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</p>

</div>);

data.Add().ID("pizzatype").Text("Pizza Type").ContentTemplate(@<div></div>);

data.Add().ID("sandwichtype").Text("Sandwich Type").ContentTemplate(@<div></div>);

})

{% endhighlight %}


The following screenshot is the output for the given code example.



![](Getting-Started_images/Getting-Started_img3.png)



### Sub Tab with Content 

Each item has a variety of options, and these options are also specified in the limited space. So you can choose the Tab control that is used within the root Tab to specify more details.

The following code example represents sub Tab control rendering using helper function.

{% highlight CSHTML %}

<!--Use the following codes with in the  above Html -->


  @Html.EJ().Tab("DishType").Items(data =>

{

    data.Add().ID("pizzamenu").Text("Pizza Menu").ContentTemplate(@<div> Rating:

    @Html.EJ().Rating("RatingPizza").Value(4).Precision(Precision.Exact)



<!--Food item description-->

    <p>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</p>

       @firstTab()

</div>);

    data.Add().ID("pizzatype").Text("Pizza Type").ContentTemplate(@<div></div>);

    data.Add().ID("sandwichtype").Text("Sandwich Type").ContentTemplate(@<div></div>);

})

@helper firstTab()

{

    @Html.EJ().Tab("PizzaMenu").Items(data =>

    {

        data.Add().ID("Corn-Spinach").Text("Corn Spinach").ContentTemplate(@<div class="e-content">

            <img src=" http://js.syncfusion.com/demos/web/images/accordion/corn-and-spinach-05.png" alt="corn-spinach">

            <div class="ingredients">

                Rate    : $70<br />

                Ingredients : cheese, sweet corn &amp; green capsicums.

                <br />

                Description: Small pizza bases are topped with spinach and paneer and fresh cream, a nice layer of mozzarella cheese. This is baked until the cheese is all hot and gooey.

            </div>

        </div>

);

        data.Add().ID("ChickenDelite").Text("Chicken-Delite").ContentTemplate(@<div class="e-content">

    <img src="http://js.syncfusion.com/demos/web/images/accordion/chicken-delite.png" alt="chicken-delite">

    <div class="ingredients">

        Rate    : $100<br />

        Ingredients : cheese, chicken chunks, onions &amp; pineapple chunks.

        <br />

        Description: This is a tasty, elegant chicken dish that is easy to prepare.

    </div>

</div>

        );

    })



});





}

{% endhighlight %}


The following code example is used to position the image and content.

{% highlight css %}

<style type="text/css" class="cssStyles">

   /*reuse the previous rating control style section code*/                

   .ingredients 
   {

		height: 180px;

		margin-top: 8px;

	}

	img 
	{           

		float: left;        

		margin: 10px 26px 5px 1px;

	}

</style>

{% endhighlight %}

The following screenshot illustrates the first Tab with the sub Tab control.



![](Getting-Started_images/Getting-Started_img4.png)



### Orientation Change

Now, you can learn how to set the sub Tab orientation to vertical. By default, Tab control is rendered in horizontal orientation. You can change this orientation to vertical by using the HeaderPosition property. In the following code section, set the Tab header orientation as Left.

The following code section renders the sub Tab element in the vertical orientation.

{% highlight CSHTML %}

<!--Use the following codes with in the  above Html -->

    @Html.EJ().Tab("DishType").Items(data =>

{

    data.Add().ID("pizzamenu").Text("Pizza Menu").ContentTemplate(@<div>

        Rating:

        @Html.EJ().Rating("RatingPizza").Value(4).Precision(Precision.Exact)



        <!--Food item description-->

        <p>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</p>

        @firstTab()

    </div>);

    data.Add().ID("pizzatype").Text("Pizza Type").ContentTemplate(@<div></div>);

    data.Add().ID("sandwichtype").Text("Sandwich Type").ContentTemplate(@<div></div>);

})

    @helper firstTab()

{

    @Html.EJ().Tab("PizzaMenu").HeaderPosition(HeaderPosition.Left).Height("221").Items(data =>

    {

        data.Add().ID("Corn-Spinach").Text("Corn Spinach").ContentTemplate(@<div class="e-content">

            <img src=" http://js.syncfusion.com/demos/web/images/accordion/corn-and-spinach-05.png" alt="corn-spinach">

            <div class="ingredients">

                Rate    : $70<br />

                Ingredients : cheese, sweet corn &amp; green capsicums.

                <br />

                Description: Small pizza bases are topped with spinach and paneer and fresh cream, a nice layer of mozzarella cheese. This is baked until the cheese is all hot and gooey.

            </div>

        </div>

);

        data.Add().ID("ChickenDelite").Text("Chicken-Delite").ContentTemplate(@<div class="e-content">

            <img src="http://js.syncfusion.com/demos/web/images/accordion/chicken-delite.png" alt="chicken-delite">

            <div class="ingredients">

                Rate    : $100<br />

                Ingredients : cheese, chicken chunks, onions &amp; pineapple chunks.

                <br />

                Description: This is a tasty, elegant chicken dish that is easy to prepare.

            </div>

        </div>

        );

    })



});

{% endhighlight %}


The following screenshot is the output of above steps.



![](Getting-Started_images/Getting-Started_img5.png)



### Configure Contents to remaining Tab items

The second and third Tab contents are declared in the same method as of the first Tab content declaration. These Tabs also consist of rating and sub Tab controls. 



{% highlight CSHTML %}

@{Html.EJ().Tab("DishType").Items(data => 
        {
			data.Add().ID("Pizzatype").Text("Pizza Menu").ContentTemplate(@<div> 
			Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.
			@firstTab()
            </div>);
			data.Add().ID("sandwitchtype").Text("Sandwizza Menu").ContentTemplate(@<div>
			Sandwizza cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health. 
			@secondTab() 
			</div>);  
			data.Add().ID("Pastatype").Text("Pasta Menu").ContentTemplate(@<div>
			</div>);  
		}).Render();

		@helper secondTab(){ 
		   @Html.EJ().Tab("SandwichMenu").HeaderPosition(HeaderPosition.Left).Height("221").Items(data =>
		   {       
				data.Add().ID("GardenVeggie").Text("Garden Veggie").ContentTemplate(@<div class="e-content">
				<img src="http://js.syncfusion.com/demos/web/images/accordion/garden-veggie.png" alt="garden-veggie "> 
				<div class="ingredients"> 
				Rate    : $55<br />  
				Ingredients : grilled chicken, corn &amp;olives.
				<br />    
				Description: To make an appetizer pizza made with crescent roll dough, baked and topped with flavored cream cheese and crispy fresh vegetables.
				Broccoli, carrots, and bell peppers make this a wonderfully delicious vegetarian treat
				</div> 
				</div>);
				data.Add().ID("ChickenTikka").Text("Chicken Tikka ").ContentTemplate(@<div class="e-content">  
				<img src="http://js.syncfusion.com/demos/web/images/accordion/chicken-tikka.png" alt="chicken-tikka"> 
				<div class="ingredients">  
				Rate    : $100<br /> 
				Ingredients : onions, grilled chicken, chicken salami &amp; tomatoes.   
				<br />      
				Description: Juicy chunks of boneless chicken roasted on open fire.This takeaway favourite is freezer-friendly and quick to reheat, giving you the chance to get ahead. 
				</div>   
				</div>); 
				data.Add().ID("PaneerTikka").Text("Paneer Tikka  ").ContentTemplate(@<div class="e-content"> 
				<img src="http://js.syncfusion.com/demos/web/images/accordion/paneer-tikka.png" alt="paneer-tikka"> 
				<div class="ingredients"> 
				Rate    : $150  
				<br /> 
				Ingredients : onions, paneer & tomatoes.
				<br />
				Description: Delve into the tasty Paneer Tikka Kebabs made from marinated paneer or cottage cubes.
				Relish these grilled delicacies with green mint chutney and onion rings.
				</div> 
				</div>);
			})   
		}   
			</div>
{% endhighlight  %}


Add third Tab contents in element during initialization using content template option.

{% highlight CSHTML %}
@{Html.EJ().Tab("DishType").Items(data =>  
   {   
		data.Add().ID("Pizzatype").Text("Pizza Menu").ContentTemplate(@<div>
		Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.
		@firstTab()  
		</div>); 
		data.Add().ID("sandwitchtype").Text("Sandwizza Menu").ContentTemplate(@<div>
		Sandwizza cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health. 
		@secondTab() 
		</div>); 
		data.Add().ID("Pastatype").Text("Pasta Menu").ContentTemplate(@<div>
		Pasta cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.  
		@thirdTab() 
		</div>); 
		}).Render();   

 @helper thirdTab(){
 @Html.EJ().Tab("PastaMenu").HeaderPosition(HeaderPosition.Left).Height("221").Items(data =>
 {     
	data.Add().ID("KheemaPasta").Text("Kheema Pasta ").ContentTemplate(@<div class="e-content">
	<img src="http://js.syncfusion.com/demos/web/images/accordion/corn-and-spinach.png" alt="kheema-pasta "> 
	<div class="ingredients"> 
	<p>     
	Rate : $30<br /> 
	Ingredients : chicken, onions, chilly, garlic &amp; tomatoes.<br />
	Description: Kheema pasta dish make with veg or non-veg type.It is delicious and can be served for dinner, brunch or evening snack. 
	</p> 
	</div>  
	</div>); 
	data.Add().ID("TunaPasta").Text("Tuna Pasta").ContentTemplate(@<div class="e-content">
	<img src="http://js.syncfusion.com/demos/web/images/accordion/garden-fresh.png" alt="tuna-pasta">
	<div class="ingredients">  
	<p>     
	Rate : $55<br /> 
	Ingredients : tomato ,olive, oninor &amp;garlic.<br />  
	Description: Canned tuna is used to make this yummy tomato sauce.
	</p>       
	</div> 
	</div> );   
	data.Add().ID("ChannaPasta").Text("Channa Pasta").ContentTemplate(@<div class="e-content"> 
	<img src="http://js.syncfusion.com/demos/web/images/accordion/zesty-mushroons-and-tomatoes.png" alt="channa-asta"> 
	<div class="ingredients">   
	<p>              
	Rate : $30<br />     
	Ingredients : sautered spinach mix, sweet corn, parsley &amp;mozarella cheese. .<br /> 
	Description: This is a pasta dish make with leftover channa masala (chole). This can be made from scratch too by making the channa masala first and then tossing in the cooked pasta. 
	</p>     
	</div>      
	</div>); 
	})     
	}
{% endhighlight  %}


Apply the following styles to the Tab.

{% highlight css %}

<style type="text/css" class="cssStyles">

	/*to reuse the previous style section code and following css*/        

   .sandwichImg, .pastaImg 
   {

		height: 25px;

		width: 25px;

	}

	.sandwichImg 
	{

		background: url("http://js.syncfusion.com/UG/Web/Content/rsz_garden-fresh.png") no-repeat;                       

	}

	.pastaImg 
	{

		background: url("http://js.syncfusion.com/UG/Web/Content/rsz_garden-veggie.png") no-repeat;                 

	}        

</style>

{% endhighlight %}


The following screenshot illustrates the second Tab contents in Tab and the final hotel menu with rating, description and ingredients of the item in the Tab interface.



![](Getting-Started_images/Getting-Started_img6.png)



