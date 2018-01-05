---
layout: post
title: Appearance and Styling | AutoComplete  | ASP.NET MVC | Syncfusion
description: appearance and styling
platform: ejmvc
control: AutoComplete
documentation: ug
---

# Appearance and Styling

## Adjusting AutoComplete size

AutoComplete widget allows you to set the height and width of the textbox element in AutoComplete. The Height and Width properties take pixel values to set the dimension accordingly.

### Define height and width for AutoComplete textbox

The following steps explain the dimensional properties of an AutoComplete textbox.



1. In the View page, define the AutoComplete control and set values for Height and Width property.


{% highlight CSHTML %}


@*Refer to the DataSource defined in Local Data binding Step 1 *@

@Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text").GroupBy("Category"))

    .Height("50px").Width("250px")

    .MultiSelectMode(MultiSelectModeTypes.Delimiter)


{% endhighlight %}




The following image is the output for AutoComplete textbox with customized dimensions.



![](Appearance-and-Styling_images/Appearance-and-Styling_img1.png)

AutoComplete with Customized dimensions
{:.caption}

## Rounded corner

By enabling the ShowRoundedCorner property, you can customize the shape of the AutoComplete widget from a regular rectangular shape to a rounded rectangle shape that is set to ‘false’ by default.

### Enabling Rounded corner 

The following steps explain enabling the ShowRoundedCorner property for an AutoComplete textbox.



1. In the View page, define the AutoComplete control and enable the ShowRoundedCorner property.


{% highlight CSHTML %}



@*Refer to the DataSource defined in Local Data binding Step 1 *@

@Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text").GroupBy("Category"))

    .ShowRoundedCorner(true)


{% endhighlight %}


The following image is the output for AutoComplete when ShowRoundedCorner is set to “true”.



![](Appearance-and-Styling_images/Appearance-and-Styling_img2.png)

AutoComplete with Rounded corners
{:.caption}

## Watermark text

WatermarkText property provides you with an option to display a faded text in the AutoComplete textbox when the textbox is empty.

### Defining Watermark text 

The following steps explain you how to configure WatermarkText property for an AutoComplete textbox.



1. In the View page, define the AutoComplete control and enable the WatermarkText property.

{% highlight CSHTML %}


@*Refer to the DataSource defined in Local Data binding Step 1 *@

@Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text").GroupBy("Category"))

    .Width("250px").WatermarkText("Select an item")

{% endhighlight %}

The following image is the output for AutoComplete when WatermarkText is defined.



![](Appearance-and-Styling_images/Appearance-and-Styling_img3.png)

AutoComplete loaded with watermark text
{:.caption}

## Adjusting Suggestion list size

AutoComplete widget provides you with a property to define the dimensions of the popup panel that holds the suggestions list items. The PopupHeight and PopupWidth properties allow you to set the maximum height and width of the popup element for use when the content exceeds the default dimensions.

### Configure dimensions of PopUp panel

The following steps help you set height and width of the popup panel of an AutoComplete textbox.



1. In the View page, define the AutoComplete control and configure the Popup panel height and width properties.


{% highlight CSHTML %}

@*Refer to the DataSource defined in Local Data binding Step 1 *@

@Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text").GroupBy("Category"))

    .Width("250px").PopupHeight("80px").PopupWidth("350px")


{% endhighlight %}

The following image is the output for AutoComplete, after configuring the height and width of the popup panel.



![](Appearance-and-Styling_images/Appearance-and-Styling_img4.png)

AutoComplete PopUp panel with configured dimensions
{:.caption}

## PopUp Time Delay

AutoComplete widget allows you to set the time delay to fetch the list items. The value of DelaySuggestionTimeout is set in milliseconds, so that data search time can be configured. This enhances the turnaround time to populate the list items.

### Configure Time delay of PopUp panel

The following steps are used to set the time delay to load the popup panel of an AutoComplete textbox.

1. In the View page, add an Autocomplete helper and configure it.



2. Configure the delay time for popup panel in AutoComplete control as follows.

{% highlight CSHTML %}



@*Refer to the DataSource defined in Local Data binding Step 1 *@

@Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text").GroupBy("Category"))

    .Width("250px").DelaySuggestionTimeout(1000)


{% endhighlight %}


This takes 1000ms to display the popup panel list items.

## Theme

AutoComplete control’s style and appearance are controlled based on CSS classes. In order to apply styles to the AutoComplete control, you can refer 2 files namely, ej.widgets.core.min.s and ej.theme.min.s. When the file ej.widgets.all.min.s is referred, then it is not necessary to include the files ej.widgets.core.min.s and ej.theme.min.s in your project, as ej.widgets.all.min.s is the combination of these two. 

By default, there are 12 theme supports available for AutoComplete control namely:

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

CSS class is used to customize the AutoComplete control’s appearance. Define CSS class as per requirement and assign the class name to CssClass property.

Configure AutoComplete textbox using CSS class

The following steps allow you to configure CssClass for an AutoComplete textbox.



1. Define CSS class for customizing the AutoComplete control.


   ~~~ s


		<style type="text/s" class="sStyles">

				/* Customize the PopUp panel */

				.customCss

				{

					border-color:Purple;

					background-color: #E0E0E0;

				}

				/* Customize the AutoComplete input textbox */

			   .customCss .e-autocomplete

			   {

				  background-color: #FFFFCC;

				  font-weight:bold;

				  font-family: sans-serif;

			   }

			</style>

   ~~~
   

2. In the View page, define the AutoComplete control and assign the class name to CssClass property.


   ~~~ cshtml

		@*Refer to the DataSource defined in Local Data binding Step 1 *@

		@Html.EJ().Autocomplete("autocomplete")

			.Datasource((IEnumerable<CarsList>)ViewBag.datasource)

			.AutocompleteFields(field => field.Key("UniqueKey").Text("Text").Category("Category"))

			.Width("250px").CssClass("customCss")



   ~~~
   




The following image is of an AutoComplete textbox configured based on CSS class.

![](Appearance-and-Styling_images/Appearance-and-Styling_img5.png)

AutoComplete widget configured with CSS class
{:.caption}
