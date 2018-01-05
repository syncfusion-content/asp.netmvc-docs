---
layout: post
title: Appearance and Styling | Splitter | ASP.NET MVC | Syncfusion
description: appearance and styling 
platform: ejmvc
control: Splitter
documentation: ug
---

# Appearance and Styling 

## Responsive

The EnableAutoResize option allows the Splitter control to adapt its rendering based on the parent container where it is actually placed. When this option is set to true, the Splitter control adjusts its height and width based on the outer container that contains it, and also the sub-elements within it adjust to its height, width and position, appropriately.

### Enabling Auto Resize

The following steps explain the implementation of AutoResize option in the Splitter control. 

1. In the View page, add the Splitter helper and configure the ‘EnableAutoResize’ property.


{% tabs %}

{% highlight CSHTML %}

@{Html.EJ().Splitter("outerSplitter").Height("280")

.Width("100%").Orientation(Orientation.Vertical).EnableAutoResize(true)

.PaneProperties(

p =>

{

p.Add().ContentTemplate(

	@<div>

		<div class="content" style="padding: 0px 15px;">

			<h3 class="h3">

				ASP.NET MVC

			</h3>

		</div>

	</div>).PaneSize("60");

	p.Add().ContentTemplate(

	@<div style="height: 100%; width: 100%">

		@innerSplitter()

	</div>);

}).Render();}



@helper innerSplitter()

{

@Html.EJ().Splitter("innerSplitter").EnableAutoResize(true).PaneProperties(p1=>

		{

			p1.Add().ContentTemplate(@<div>

				<div class="content">

					<h3 class="h3">

						Tools

					</h3>

					Essential Tools is an collection of user interface components used to create interactive

					ASP.NET MVC applications.

				</div>

			</div>);



			p1.Add().ContentTemplate(@<div>

	<div class="content">

		<h3 class="h3">

			Grid

		</h3>

		Essential MVC Grid offers full featured a Grid control with extensive support for

		Grouping and the display of hierarchical data.

	</div>

</div>);

		});

}

{% endhighlight %}

{% highlight css %}

<style type="text/css">

    #outerSplitter 
	{

        margin: 0 auto;

    }

    .h3 
	{

        font-size: 14px;

    }

    #innerSplitter 
	{

        border: 0 none;

    }

    .content 
	{

        padding: 15px;

    }

</style>


{% endhighlight %}
{% endtabs %} 



The output for Splitter when EnableAutoResize is “true”.



![](Appearance-and-Styling_images/Appearance-and-Styling_img1.png)





![](Appearance-and-Styling_images/Appearance-and-Styling_img2.png)



## Animation Support

The Splitter provides you animation support when you expand or collapse the pane. The animation speed can be modified by using the AnimationSpeed property, that has values in milliseconds.

Enabling Animation with Animation speed

The following steps explain the implementation of EnableAnimation option in the Splitter widget.

1. In the View page add the Splitter helper to customize the Splitter appearance. 



{% highlight CSHTML %}

@{Html.EJ().Splitter("Splitter").Height("200").Width("500").EnableAnimation(true).AnimationSpeed(300).PaneProperties(

p =>

{

	p.Add().ContentTemplate(

		@<div>

			 <div style="padding: 0px 15px;">

				 <h3 class="h3">Tools </h3>

				 Essential Tools is an collection of user interface components used to create interactive

				 ASP.NET MVC applications.

			 </div>

		</div>);

	p.Add().ContentTemplate(

		@<div>

			 <div style="padding: 0px 15px;">

				 <h3 class="h3">Grid </h3>

				 Essential MVC Grid offers full featured a Grid control with extensive support for

				 Grouping and the display of hierarchical data.

			 </div>

		</div>);

}).Render();}

{% endhighlight %}

The output for Splitter when EnableAnimation is “true”. Expanding or collapsing the outer pane in the Splitter produces the animation effect with the animation speed.



![](Appearance-and-Styling_images/Appearance-and-Styling_img3.png)



## Adjusting Splitter Size

### Height

The height of Splitter can be modified by using the Height property. The default value for Height property is null in Splitter. You can set the Height property by pixel or percentage values.

### Width

The width of Splitter can be modified by using the Width property. The default value for Width property is null in Splitter. You can set the Width property by pixel or percentage values.

### Max Size

Defines the maximum resizable size of the pane when you resize the Splitter widget. The default value of MaxSize is null in Splitter. You can set the MaxSize property by pixel values.

### Min Size

Defines the minimum resizable size of the pane when you resize  the Splitter widget. The default value of MinSize is 10 in Splitter. You can set the MinSize property by pixel values.

### Pane Size

Defines the pane size in the Splitter widget. The default value of PaneSize is 0px in Splitter. You can set the PaneSize property by pixel or percentage values.

### Resizable

Defines whether the pane in the Splitter is resizable or not. Setting the resizable property as “false” disables the resize option to the pane. The default value of Resizable property is true in Splitter.

The following steps explain the implementation of Splitter properties. 

1. In the View page add Splitter helper and configure resizable property of the split pane.



{% highlight CSHTML %}

@{Html.EJ().Splitter("Splitter").Height("200").Width("500").PaneProperties(

p =>

{

	p.Add().ContentTemplate(

		@<div>

			 <div style="padding: 0px 15px;">

				 <h3 class="h3">Tools </h3>

				 Essential Tools is an collection of user interface components used to create interactive

				 ASP.NET MVC applications.

			 </div>

		</div>);

	p.Add().ContentTemplate(

		@<div>

			 <div style="padding: 0px 15px;">

				 <h3 class="h3">Grid </h3>

				 Essential MVC Grid offers full featured a Grid control with extensive support for

				 Grouping and the display of hierarchical data.

			 </div>

		</div>).Collapsible(true).MinSize("100").MaxSize("150").PaneSize("150").Resizable(true);

}).Render();}


{% endhighlight %}


The output for Splitter after adding the properties.



![](Appearance-and-Styling_images/Appearance-and-Styling_img4.png)





![](Appearance-and-Styling_images/Appearance-and-Styling_img5.png)





![](Appearance-and-Styling_images/Appearance-and-Styling_img6.png)





![](Appearance-and-Styling_images/Appearance-and-Styling_img7.png)



## Theme

Splitter control’s style and appearance can be controlled based on CSS classes. In order to apply styles to the Splitter control, refer 2 files namely: ej.widgets.core.min.css and ej.theme.min.css. If the file ej.widgets.all.min.css is referred, then it is not necessary to include the files ej.widgets.core.min.css and ej.theme.min.css in your project, as ej.widgets.all.min.css is the combination of these two. 

By default, there are 12 themes support available for Autocomplete control namely

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

## CSS Class

The CSS properties can be customized by using CssClass in the Splitter widget. The following steps explain the implementation of CssClass option in the Splitter widget.

In the View page add the Splitter helper and customize the Splitter appearance. 


{% highlight CSHTML %}

@{Html.EJ().Splitter("Splitter").Height("200").Width("500").CssClass("customCSS").PaneProperties(

    p =>

    {

        p.Add().ContentTemplate(

            @<div>

                 <div style="padding: 0px 15px;">

                     <h3 class="h3">Tools </h3>

                     Essential Tools is an collection of user interface components used to create interactive

                     ASP.NET MVC applications.

                 </div>

            </div>);

        p.Add().ContentTemplate(

            @<div>

                 <div style="padding: 0px 15px;">

                     <h3 class="h3">Grid </h3>

                     Essential MVC Grid offers full featured a Grid control with extensive support for

                     Grouping and the display of hierarchical data.

                 </div>

            </div>).Collapsible(true).MinSize("100").Resizable(true);

    }).Render();}


{% endhighlight %}


1. Customize the CSS class by setting CSS properties. 



{% highlight CSS %}



<style>

	.customCSS 
	{            

		border-color: #661e19;

	}



	/*Customize Splitbar*/

	.customCSS .e-splitbar 
	{

		background-color: #f9c89f;

	}



	/*Customize Splitter pane*/

	.customCSS .e-pane 
	{

		color: #b21010;

		background-color: #f6e492;

	}     

</style>


{% endhighlight %}


The output for Splitter after customizing the CSS class.



![](Appearance-and-Styling_images/Appearance-and-Styling_img8.png)



