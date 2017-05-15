---
layout: post
title: Getting Started | Progress Bar | ASP.NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: Progress Bar
documentation: ug
---

# Getting Started

This section briefly describes how to create a Progress Bar control using ASP.NET MVC and learn its features.

## Create your first Progress Bar in MVC

ASP.NET MVCProgress Bar control provides support to display a Progress Bar that allows you to change the process of the ProgressBar animations and flexible APIs. Using the following guidelines, you can create the ProgressBar to validate the Password strength.

The following screenshot illustrates the functionality of a Progress Bar and displays the final result of the Password Strength Validation for your password using Progress Bar.



![](Getting-Started_images/Getting-Started_img4.png)

Progress Bar
{:.caption}

## Create a Textbox and Progress Bar

ASP.NET MVC Progress Bar control indicates the current progress of an operation like uploading a document through a simple interface. You can easily create the Progress bar control using simple HTML helpers as follows.

1. Create an MVC Project and add necessary assemblies, scripts and styles to it. 
   Refer [MVC-Getting Started.](http://help.syncfusion.com/aspnetmvc/progressbar/getting-started)



2. Add the following code to the corresponding view page to render Progress Bar.

   ~~~ cshtml
   
	<div class="start" >

			 <label for="start">Password</label>

				   <input type="password" id="password"/>

	  @Html.EJ().ProgressBar("progressBar").Value(20).Height("20px").Width("180px") 

	 </div>

   ~~~
   

3. Add the following styles to show the Progress Bar and Textbox.


   ~~~ css
   
	<style>

	.start 
	{

		margin-left: 105px;

		color: green;

		font-size: 18px;

	}

	.control 

	{

		margin-bottom: 5px;

		 margin-left: 230px;

	}
	#progressBar

	{

	margin-top: 10px;

	}

	</style>

   ~~~
   

4. Execute the above code to render the following output. 



![](Getting-Started_images/Getting-Started_img5.png)



### Find the Strength of the Password

In this scenario, the advancement of the Progress Bar is changed according to the length and special characters present in the text of the password field. This is achieved by binding the change in the properties of your control and by checking the length of the password field.

{% highlight js %}

<script> 

	var progressObj, k = 10, i = 0;

	$(document).keydown(function() {

		i = $("#password").val().length;

		if (i < 4) 
		{

			progress2();

			$('.e-progress').css({ background: 'red' });

		}
		else if (i > 4 && i < 7) 
		{

			progress1();

			$('.e-progress').css({ background: 'yellow' });

		} 
		else if (i > 7) 
		{

			var password = $("#password").val();

			if (/^[a-zA-Z0-9- ]*$/.test(password) == false) 
			{

				progress();

				$('.e-progress').css({ background: 'green' });

			}

		}

	});

	$(function () 
	{

		progressObj = $("#progressBar").data("ejProgressBar");       

	});

	function progress() 
	{

		progressObj.option("text", " very strong");

		progressObj.option("percentage", k + 90);

	}

	function progress1() 
	{

		progressObj.option("text", "strong");

		progressObj.option("percentage", k + 50);

	}

	function progress2() 
	{

		progressObj.option("percentage", k + 10);

		progressObj.option("text", "weak");  



	}



</script>

{% endhighlight %}

* The progress() function changes the text inside the Progress Bar to Very Strong and percentage to 100, and it is invoked when the length of the text is more than 7 and the text contains a symbol in it. Then it shows the Progress Bar in violet color.
* The progress1() function changes the text inside the Progress Bar to Strong and percentage to 60, and it is invoked when the length of the text is more than 4. Then it shows the Progress Bar in green color
* The progress 2() function changes the text inside the Progress Bar to Weak and percentage to 30, and it is invoked when the length of the text is less than 4. Then it shows the ProgressBar in red color.

The following screenshot displays a Progress Bar control for the above scenario.



![](Getting-Started_images/Getting-Started_img6.png)



![](Getting-Started_images/Getting-Started_img7.png)



![](Getting-Started_images/Getting-Started_img8.png)





