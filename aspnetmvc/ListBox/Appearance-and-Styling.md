---
layout: post
title: Appearance and Styling | ListBox | ASP.NET MVC | Syncfusion
description: appearance and styling
platform: ejmvc
control: ListBox
documentation: ug
---

# Appearance and Styling

## Adjusting ListBox size

### Width

ListBox widget provides you support to customize the dimensions of the ListBox. By using Width property you can set the width of the ListBox. Its data type is string.

### Height

ListBox widget provides you support to customize the dimensions of the ListBox. By using Height property, you can set the height of the ListBox. Its data type is string.

Defining the ListBox size properties

The following steps explains you the configuration of Height & Width properties in ListBox.

1. Add the below code in your view page to render the ListBox with customized height and width

   ~~~ cshtml
   
	// Add the following code in View page to configure ListBox widget
	<div id="control">  
		<h5 class="ctrllabel"> 
			Select a skill 
		</h5>
		@Html.EJ().ListBox("listBoxSample").Width("240").Height("302").Datasource((IEnumerable<SkillSet>)ViewBag.datasource).ListBoxFields(df 
		=> df.Text("text"))
	</div>

   ~~~
   
   
   ~~~ csharp
   
	// Add the following code to add list items in the controller page
	public class SkillSet 
	{    
		public string text { get; set; }  
	}    
	public ActionResult Index() 
	{ 
		List<SkillSet> skill = new List<SkillSet>();     
		skill.Add(new SkillSet { text = "ASP.NET" }); 
		skill.Add(new SkillSet { text = "ActionScript" });     
		skill.Add(new SkillSet { text = "Basic" });    
		skill.Add(new SkillSet { text = "C++" });   
		skill.Add(new SkillSet { text = "C#" });    
		skill.Add(new SkillSet { text = "dBase" });  
		skill.Add(new SkillSet { text = "Delphi" });  
		skill.Add(new SkillSet { text = "ESPOL" });   
		skill.Add(new SkillSet { text = "F#" });      
		skill.Add(new SkillSet { text = "FoxPro" });    
		skill.Add(new SkillSet { text = "Java" });     
		skill.Add(new SkillSet { text = "J#" });     
		skill.Add(new SkillSet { text = "Lisp" });    
		skill.Add(new SkillSet { text = "Logo" });    
		skill.Add(new SkillSet { text = "PHP" });    
		ViewBag.datasource = skill; 
		return View();    
	}

   ~~~
   


2. Output of the above steps


![](Appearance-and-Styling_images/Appearance-and-Styling_img1.png)



### Enabling Rounded corner

ListBox widget provides you support to change the appearance of ListBox. By using showRoundedCorner you can create a rounded corner on the ListBox. Its data type is Boolean.

The following steps explains you the configuration of Rounded corner of the ListBox.

1. Add the below code in your view page to render the ListBox with rounded corners


   ~~~ cshtml
   
	// Add the following code in View page to configure ListBox widget
	<div id="control">  
		<h5 class="ctrllabel"> 
			Select a skill  
		</h5> 
		@Html.EJ().ListBox("listBoxSample").Width("240").Datasource((IEnumerable<SkillSet>)ViewBag.datasource).ListBoxFields(df =>
		df.Text("text")).ShowRoundedCorner(true)
	</div>
		
   ~~~
   
		
   ~~~ csharp
   
	// Add the following code to add list items in the controller page 
	public class SkillSet
	{  
		public string text { get; set; } 
	} 
	public ActionResult Index()
	{    
		List<SkillSet> skill = new List<SkillSet>();  
		skill.Add(new SkillSet { text = "ASP.NET" });
		skill.Add(new SkillSet { text = "ActionScript" });
		skill.Add(new SkillSet { text = "Basic" });     
		skill.Add(new SkillSet { text = "C++" });     
		skill.Add(new SkillSet { text = "C#" });     
		skill.Add(new SkillSet { text = "dBase" });  
		skill.Add(new SkillSet { text = "Delphi" }); 
		skill.Add(new SkillSet { text = "ESPOL" });  
		skill.Add(new SkillSet { text = "F#" });    
		skill.Add(new SkillSet { text = "FoxPro" }); 
		skill.Add(new SkillSet { text = "Java" });  
		skill.Add(new SkillSet { text = "J#" });   
		skill.Add(new SkillSet { text = "Lisp" }); 
		skill.Add(new SkillSet { text = "Logo" }); 
		skill.Add(new SkillSet { text = "PHP" });  
		ViewBag.datasource = skill;   
		return View(); 
		}

   ~~~
   



2. Output of the above steps.


![](Appearance-and-Styling_images/Appearance-and-Styling_img2.png)



