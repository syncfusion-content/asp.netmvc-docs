---
layout: post
title: Drag and Drop Support | ListBox | ASP.NET MVC | Syncfusion
description: drag and drop support
platform: ejmvc
control: ListBox
documentation: ug
---

# Drag and Drop Support

ListBox widget provides the Drag and Drop support. A list item can be dragged from a ListBox control and can be dropped in any droppable element. To enable Drag and Drop support, set the AllowDrag and AllowDrop property as true. In control, enable the AllowDrag and AllowDrop property where you want to drop list Item.

The following steps explains you the behavior of template support with ListBox.

1. Add the below code in your page to render the ListBox


   ~~~ cshtml

	// Add the following code in View page to configure ListBox widget 
	<div class="control1"> 
		<h5 class="ctrlLabel">
			Drag and drop skills 
		</h5>
		@Html.EJ().ListBox("listBoxSample").Datasource((IEnumerable<ug_listbox.controllers.skillSet>)ViewBag.datasource).ListBoxFields(df =>
		df.Text("text")) .AllowDrag(true).AllowDrop(true)
	</div>
	<div class="control2"> 
		@Html.EJ().ListBox("dragSample").AllowDrag(true).AllowDrop(true)
	</div>
		
   ~~~
   
   
   ~~~ csharp
		
	// Add the following code to add list items in the controller page  
	public class skillSet 
	{          
		public string text { get; set; }     
	}       
	public ActionResult Index()   
	{        
		List<skillSet> skill = new List<skillSet>();   
		skill.Add(new skillSet { text = "ASP.NET" });    
		skill.Add(new skillSet { text = "ActionScript" }); 
		skill.Add(new skillSet { text = "Basic" });      
		skill.Add(new skillSet { text = "C++" });       
		skill.Add(new skillSet { text = "C#" });      
		skill.Add(new skillSet { text = "dBase" });   
		skill.Add(new skillSet { text = "Delphi" });      
		skill.Add(new skillSet { text = "ESPOL" });     
		skill.Add(new skillSet { text = "F#" });      
		skill.Add(new skillSet { text = "FoxPro" });  
		skill.Add(new skillSet { text = "Java" });   
		skill.Add(new skillSet { text = "J#" });    
		skill.Add(new skillSet { text = "Lisp" });  
		skill.Add(new skillSet { text = "Logo" });   
		skill.Add(new skillSet { text = "PHP" });  
		ViewBag.datasource = skill;     
		return View();  
	}

   ~~~
   


2. Add the following class in CSS. 


   ~~~ cshtml 

	<style type="text/css" class="cssStyles">

		.control 
		{

			margin-left: 20px;

		}



		.ctrlLabel 
		{

			padding-bottom: 3px;

		}



		.control2 
		{

			padding-left: 350px;

		}

	</style>


   ~~~
   


3. Output of the above steps.

![](Drag-and-Drop-Support_images/Drag-and-Drop-Support_img1.png)



