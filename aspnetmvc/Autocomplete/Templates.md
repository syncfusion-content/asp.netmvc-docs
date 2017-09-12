---
layout: post
title: Templates | AutoComplete | ASP.NET MVC | Syncfusion
description: templates
platform: ejmvc
control: AutoComplete
documentation: ug
---

# Templates

You can provide a Template for customizing the appearance of the AutoComplete textbox suggestions. This is achieved by assigning a string template to the Template property.

## Configuring Templates

The following steps explain you how to define a Template to display a text and image for an AutoComplete textbox.


1. Define DataSource elements with required template fields by using the Sprite CSS class names.


   ~~~ csharp
     public partial class AutocompleteController : Controller

     {

        List<Flags> flags = new List<Flags>();

        public ActionResult AutocompleteFeatures()

        {

			flags.Add(new Flags { Text = "Algeria", Sprite = "flag-algeria" });

			flags.Add(new Flags { Text = "Armenia", Sprite = "flag-am" });

			flags.Add(new Flags { Text = "Brazil", Sprite = "flag-br" });

			flags.Add(new Flags { Text = "Bangladesh", Sprite = "flag-bangladesh" });

			flags.Add(new Flags { Text = "Canada", Sprite = "flag-ca" });

			flags.Add(new Flags { Text = "Cuba", Sprite = "flag-cu" });

			flags.Add(new Flags { Text = "China", Sprite = "flag-china" });

			flags.Add(new Flags { Text = "Denmark", Sprite = "flag-denmark" });

			flags.Add(new Flags { Text = "Estonia", Sprite = "flag-estonia" });

			flags.Add(new Flags { Text = "Egypt", Sprite = "flag-eg" });

			flags.Add(new Flags { Text = "France", Sprite = "flag-fr" });

			flags.Add(new Flags { Text = "Finland", Sprite = "flag-fi" });

			flags.Add(new Flags { Text = "Greenland", Sprite = "flag-gl" });

			flags.Add(new Flags { Text = "India", Sprite = "flag-in" });

			flags.Add(new Flags { Text = "Indonesia", Sprite = "flag-id" });

			flags.Add(new Flags { Text = "Malaysia", Sprite = "flag-my" });

			flags.Add(new Flags { Text = "Mexico", Sprite = "flag-mexico" });

			flags.Add(new Flags { Text = "New Zealand", Sprite = "flag-new-zealand" });

			flags.Add(new Flags { Text = "Netherlands", Sprite = "flag-nl" });

			flags.Add(new Flags { Text = "Norway", Sprite = "flag-no" });

			flags.Add(new Flags { Text = "Portugal", Sprite = "flag-pt" });

			flags.Add(new Flags { Text = "Poland", Sprite = "flag-pl" });

			flags.Add(new Flags { Text = "Qatar", Sprite = "flag-qatar" });

			flags.Add(new Flags { Text = "Romania", Sprite = "flag-ro" });

			flags.Add(new Flags { Text = "Spain", Sprite = "flag-es" });

			flags.Add(new Flags { Text = "Singapore", Sprite = "flag-singapore" });

			flags.Add(new Flags { Text = "Saudi Arabia", Sprite = "flag-sa" });

			flags.Add(new Flags { Text = "Thailand", Sprite = "flag-th" });

			flags.Add(new Flags { Text = "Turkey", Sprite = "flag-tr" });

			flags.Add(new Flags { Text = "Ukraine", Sprite = "flag-ukraine" });

			flags.Add(new Flags { Text = "United States", Sprite = "flag-us" });

			flags.Add(new Flags { Text = "Uruguay", Sprite = "flag-uruguay" });

			flags.Add(new Flags { Text = "Viet Nam", Sprite = "flag-viet-nam" });

			ViewBag.datasource = flags;

			return View();

		} 

     }

     public class Flags

     {
		 public string Text { get; set; }

		 public string Sprite { get; set; }

     } 

   ~~~
   

2. Configure template structure for AutoComplete control as follows, including a <div> element with image and text in every row of the popup panel. Assign the corresponding variable name within ${<field name>} to map them into the list.


   ~~~ cshtml


     @Html.EJ().Autocomplete("autocomplete")

     .Datasource((IEnumerable<Flags>)ViewBag.datasource)

     .AutocompleteFields(fields => fields.Text("Text"))

     .Template("<div class='flag ${Sprite}'></div><div class='txt'> ${_Text_} </div>")

   ~~~
   

3. Define the CSS classes for the sprite images. You can find the images in the following location:

[Installed Drive]:\Users\[user name]\AppData\Local\Syncfusion\EssentialStudio\X.X.X.X\MVC\Samples\web\Images\autocomplete\flags.png

{% highlight s %}

<style type="text/s">

	/* Sprite s for country flags */

	.flag

	{

		background: url("Styles/flags.png") no-repeat;

		float: left;

		height: 15px;

		margin-right: 10px;

		margin-top: 3px;

		width: 25px;

	}

	.flag.flag-am {background-position: -25px 0}

	.flag.flag-ar {background-position: -50px 0}

	.flag.flag-bangladesh {background-position: -75px 0}

	.flag.flag-br {background-position: -100px 0}

	.flag.flag-ca {background-position: -125px 0}

	.flag.flag-china {background-position: 0 -15px}

	.flag.flag-cu {background-position: -25px -15px}

	.flag.flag-denmark {background-position: -50px -15px}

	.flag.flag-algeria {background-position: -75px -15px}

	.flag.flag-estonia {background-position: -100px -15px}

	.flag.flag-eg {background-position: -125px -15px}

	.flag.flag-es {background-position: 0 -30px}

	.flag.flag-fi {background-position: -25px -30px}

	.flag.flag-fr {background-position: -50px -30px}

	.flag.flag-gl {background-position: -75px -30px}

	.flag.flag-id {background-position: -100px -30px}

	.flag.flag-in {background-position: -125px -30px}

	.flag.flag-mexico {background-position: 0 -45px}

	.flag.flag-my {background-position: -25px -45px}

	.flag.flag-nl {background-position: -50px -45px}

	.flag.flag-no {background-position: -75px -45px}

	.flag.flag-new-zealand {background-position: -100px -45px}

	.flag.flag-pl {background-position: -125px -45px}

	.flag.flag-pt {background-position: 0 -60px}

	.flag.flag-qatar {background-position: -25px -60px}

	.flag.flag-ro {background-position: -50px -60px}

	.flag.flag-sa {background-position: -75px -60px}

	.flag.flag-singapore {background-position: -100px -60px}

	.flag.flag-th {background-position: -125px -60px}

	.flag.flag-tr {background-position: 0 -75px}

	.flag.flag-ukraine {background-position: -25px -75px}

	.flag.flag-us {background-position: -50px -75px}

	.flag.flag-uruguay {background-position: -75px -75px}

	.flag.flag-viet-nam {background-position: -100px -75px}

	.flag.flag-ye {background-position: -125px -75px}

	.txt {

		display: table-cell;

		height: 20px;

		vertical-align: middle;

	}  

</style>

{% endhighlight %}




The following image is the output for AutoComplete widget with Template support.



![](Templates_images/Templates_img1.png)

AutoComplete with Custom template
{:.caption}
