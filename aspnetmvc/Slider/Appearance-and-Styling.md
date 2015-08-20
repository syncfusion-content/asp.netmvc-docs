---
layout: post
title: Appearance-and-Styling
description: appearance and styling	
platform: ejmvc
control: Slider
documentation: ug
---

# Appearance and Styling	

Slider widget looks sleek and enriched with good UI appearance. It is included with both metro (flat) theme and gradient theme support. Totally twelve inbuilt themes are provided including six flat themes and six gradient themes. The themes include three colour variations such as “Azure”, “Lime” and “Saffron”. The themes supported by the Slider widgets are as follows,

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



In order to apply different themes, you can refer the “ej.widgets.all.min.css” file from the corresponding theme folders. This file is a combination of two style sheets “ej.widgets.core.min.css” and “ej.theme.min.css”. Instead of including “ej.widgets.all.min.css” file you can also refer the “ej.widgets.core.min.css” and “ej.theme.min.css” files separately. 

The following steps explains you on how to apply “flat-lime-dark” theme to the Slider widget

1. In an VIEW page, specify the desired “ej.widgets.all.min.css” file to load the corresponding theme.

{% highlight html %}
//In _Layout page, specify the desired
 “ej.widgets.all.min.css” file to load the corresponding theme.
 <head>
 <title>Slider</title>
 <!--Flat-saffron theme-->
 <link href="http://cdn.syncfusion.com/13.1.0.21/js/web/flat-saffron-dark/ej.web.all.min.css" rel="stylesheet" />
 <!--scripts-->        <script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js">
 </script>
 <script src="http://cdn.syncfusion.com/js/assets/external/jquery.globalize.min.js"> </script>
 <script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js"> </script>
 <script src="http://cdn.syncfusion.com/13.1.0.21/js/web/ej.web.all.min.js"></script>
 </head></td><td>
{% endhighlight %}

{% highlight js %}
// Add this code in your view page
    @(Html.EJ().Slider("defaultSlider").Value("60").Width("500").MinValue(40).MaxValue(80)    .ShowScale(true).SmallStep(5).LargeStep(20))
    @(Html.EJ().Slider("rangeSlider").SliderType(SlideType.Range).Values("10,90")    .ShowScale(true).SmallStep(5).LargeStep(20))
{% endhighlight %}



Execute the above code example to render the following output.

![](Appearance-and-Styling_images/Appearance-and-Styling_img1.png)



## Css Class

When you want to display the Slider widget in a different style based on the appearance of your application, you can use this CssClass property to apply custom theme for the Slider. Specify a class name as the value for CssClass property. The specified class is added to the wrapper of the Slider widget. Now, you can easily override the styles of the Slider widget by accessing the styles from the root level (using the cssclass specified).

The following steps explains you on how to configure the Slider with custom theme using the CssClass property. Here, a class name “purple” is specified for the CssCalss.

1. In an VIEW page, specify the helper elements to render the “Default Slider” and “Range Slider”.

   ~~~ js

		// Add this code in your view page

		@(Html.EJ().Slider("rangeSlider").SliderType(SlideType.Range).Values("25,75")

		.Width("500").CssClass("purple"))

   ~~~
   {:.prettyprint }

2. Include the “CssClass” value before each style of the Slider widget and customize the styles as follows.


   ~~~ js



		.purple.e-slider.e-widget {

		  background-color: burlywood;

		  border-color: #bbbcbb;

		}

		.purple.e-tooltip {

		  background: none repeat scroll 0 0 violet;

		  /* Old browsers */



		  border-color: #1b95cf;

		  color: white;

		}

		.purple.e-slider .e-handle.e-select {

		  background-color: purple;

		  border-color: purple;

		}

		.purple.e-slider .e-handle.e-hover {

		  background-color: purple;

		  border-color: purple;

		}

		.purple.e-slider .e-handle.e-focus {

		  box-shadow: 0 0 2px rgba(0, 0, 0, 0.2);

		}

		.purple.e-slider .e-range {

		  background: none repeat scroll 0 0 violet;

		  /* Old browsers */



		}

		.purple.e-scale .e-tick {

		  background-image: url(images/dot.png);

		}

		
   ~~~
   {:.prettyprint }

Execute the above code example to render the following output.

![](Appearance-and-Styling_images/Appearance-and-Styling_img2.png)



### Show Tooltip

Slider displays the tooltip to indicate the current value when you click on the Slider handle. By default, Slider displays the tooltip. Using the ShowTooltip option you can enable or disable the Tooltip. Data type of this property is “boolean”.

The following steps explains you on how to disable the tooltip in Slider.

1. In an VIEW page, specify the helper elements to render the Default Slider.

{% highlight js %}

// Add this code in your view page

@(Html.EJ().Slider("defaultSlider").Value("60").Width("500").ShowTooltip(false))

{% endhighlight %}

![](Appearance-and-Styling_images/Appearance-and-Styling_img3.png)





### Show Rounded Corner

This property is used to display the Slider and its handle with rounded corners. By default ShowRoundedCorner is in disabled state. Data type of this property is “Boolean”.

The following steps explains you on how to disable the tooltip in Slider.

1. In an VIEW page, specify the helper elements to render the “Default Slider”.

{% highlight js %}

// Add this code in your view page

@(Html.EJ().Slider("defaultSlider").Value("60").Width("500").ShowRoundedCorner(true))

{% endhighlight %}

Execute the above code example to render the following output.

![](Appearance-and-Styling_images/Appearance-and-Styling_img4.png)



