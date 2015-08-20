---
layout: post
title: Multiple-Selection
description: multiple selection
platform: ejmvc
control: ListBox
documentation: ug
---

# Multiple Selection

## Allow multiple selection

ListBox widget allows you to select multiple values from the list Items using AllowMultiSelection property. You can select multiple list items along with Control key and Shift key press. To select multiple values we need to set AllowMultiSelection value to true.

### Configuring multiple selection

The following steps explain you the configuration of the AllowMultiSelection for a ListBox.

1. Add the below code in your view page to render the ListBox



   ~~~ html

		<div id="control">

			<h5 class="ctrllabel">

				Select a skill

			</h5>

			@{List<int> indexList = new List<int>();



			indexList.Add(0);



			indexList.Add(3);



			}       @Html.EJ().ListBox("listboxsample").Width("240").Datasource((IEnumerable<skillset>)ViewBag.datasource).ListBoxFields(df => df.Text("text")).SelectedItemlist(indexList).AllowMultiSelection(true)

		</div>

   ~~~
   {:.prettyprint }





2. Output for ListBox control that provides multiple selection is as follows.


   ![](Multiple-Selection_images/Multiple-Selection_img1.png)



## Multiple selection through index 

You can select the list of items from the ListBox using selectedItemlist property. Its data type is array. To achieve this, you need to set true to AllowMultiSelection property in ListBox. 

The following steps explains you the configuration of SelectedItemlist property in ListBox

1. Add the below code in your view page to render the ListBox with allow multiple selection enabled.


   ~~~ html
		// Add the following code in View page to configure ListBox widget
		<div id="control">
			<h5 class="ctrllabel"> 
				Select a skill  
			</h5> 
			@{List<int> indexList = new List<int>();
			indexList.Add(1);
			indexList.Add(4); 
			}  
			@Html.EJ().ListBox("listboxsample").Width("240").Datasource((IEnumerable<skillset>)ViewBag.datasource).ListBoxFields(df
			=> df.Text("text")).SelectedItemlist(indexList).AllowMultiSelection(true)
			</div>

   ~~~
   {:.prettyprint }
   
   ~~~ cs
   
	   // Add the following code to add list items in the controller page 
	   public class skillset   
	   {
			public string text { get; set; }
	   }
		public ActionResult Index() 
		{ 
			List<skillset> skill = new List<skillset>();
			skill.Add(new skillset { text = "ASP.NET" });
			skill.Add(new skillset { text = "ActionScript" });
			skill.Add(new skillset { text = "Basic" }); 
			skill.Add(new skillset { text = "C++" });  
			skill.Add(new skillset { text = "C#" }); 
			skill.Add(new skillset { text = "dBase" }); 
			skill.Add(new skillset { text = "Delphi" });
			skill.Add(new skillset { text = "ESPOL" }); 
			skill.Add(new skillset { text = "F#" });   
			skill.Add(new skillset { text = "FoxPro" }); 
			skill.Add(new skillset { text = "Java" });  
			skill.Add(new skillset { text = "J#" });   
			skill.Add(new skillset { text = "Lisp" }); 
			skill.Add(new skillset { text = "Logo" });  
			skill.Add(new skillset { text = "PHP" }); 
			ViewBag.datasource = skill;   
			return View();      
		}

   ~~~
   {:.prettyprint }


2. Output of the above steps.


![](Multiple-Selection_images/Multiple-Selection_img2.png)



## Checkbox Support

### Show Checkbox 

You can enable the checkbox in the ListBox with this property. The data type of ShowCheckbox value is Boolean type. It maintains multiple selection and gets the checked items on its ListBox client side events.  

#### Defining the Checkbox support

The following steps explains you the configuration of checkbox options in ListBox.

1. Add the below code in your view page to render the ListBox with checkbox

   ~~~ html

		// Add the following code in View page to configure ListBox widget

		<div id="control">

			<h5 class="ctrllabel">

				Select a skill

			</h5>    @Html.EJ().ListBox("listboxsample").Width("240").Datasource((IEnumerable<ug_listbox.controllers.skillset>)ViewBag.datasource).ListBoxFields(df => df.Text("text")).ShowCheckbox(true)

		</div>
		
   ~~~
   {:.prettyprint }

   ~~~ cs

		// Add the following code to add list items in the controller page

		public class skillset

		{

			public string text { get; set; }

		}

		public ActionResult Index()

		{

			List<skillset> skill = new List<skillset>();

			skill.Add(new skillset { text = "ASP.NET" });

			skill.Add(new skillset { text = "ActionScript" });

			skill.Add(new skillset { text = "Basic" });

			skill.Add(new skillset { text = "C++" });

			skill.Add(new skillset { text = "C#" });

			skill.Add(new skillset { text = "dBase" });

			skill.Add(new skillset { text = "Delphi" });

			skill.Add(new skillset { text = "ESPOL" });

			skill.Add(new skillset { text = "F#" });

			skill.Add(new skillset { text = "FoxPro" });

			skill.Add(new skillset { text = "Java" });

			skill.Add(new skillset { text = "J#" });

			skill.Add(new skillset { text = "Lisp" });

			skill.Add(new skillset { text = "Logo" });

			skill.Add(new skillset { text = "PHP" });

			ViewBag.datasource = skill;

			return View();

		}

   ~~~
   {:.prettyprint }



2. Output of the above steps.



![](Multiple-Selection_images/Multiple-Selection_img3.png)



### Check All 

You can check all the check box in the list by using this property. The data type of CheckAll is Boolean type. To achieve this, set ShowCheckbox property as true.

The following steps explains you the configuration of checkbox options in ListBox.

1. Add the below code in your view page to render the ListBox with all items checked initially.


   ~~~ html
		// Add the following code in View page to configure ListBox widget
		<div id="control">
			<h5 class="ctrllabel">
				Select a skill 
			</h5>  
			@Html.EJ().ListBox("listboxsample").Width("240").Datasource((IEnumerable<ug_listbox.controllers.skillset>)ViewBag.datasource).ListBoxFields(df =>
			df.Text("text")) .ShowCheckbox(true).CheckAll(true)
			</div>

   ~~~
   {:.prettyprint }
	
   ~~~ cs
   
		// Add the following code to add list items in the controller page
		public class skillset
		{  
			public string text { get; set; } 
		}   
		public ActionResult Index()
		{  
			List<skillset> skill = new List<skillset>();  
			skill.Add(new skillset { text = "ASP.NET" });
			skill.Add(new skillset { text = "ActionScript" });
			skill.Add(new skillset { text = "Basic" });
			skill.Add(new skillset { text = "C++" });  
			skill.Add(new skillset { text = "C#" }); 
			skill.Add(new skillset { text = "dBase" }); 
			skill.Add(new skillset { text = "Delphi" });
			skill.Add(new skillset { text = "ESPOL" }); 
			skill.Add(new skillset { text = "F#" });  
			skill.Add(new skillset { text = "FoxPro" }); 
			skill.Add(new skillset { text = "Java" }); 
			skill.Add(new skillset { text = "J#" });   
			skill.Add(new skillset { text = "Lisp" }); 
			skill.Add(new skillset { text = "Logo" }); 
			skill.Add(new skillset { text = "PHP" }); 
			ViewBag.datasource = skill;    
			return View();
		}

   ~~~
   {:.prettyprint }


2. Output of the above steps.



![](Multiple-Selection_images/Multiple-Selection_img4.png)



### Uncheck All

You can uncheck all the check box in the list by using this property. The data type of UncheckAll is Boolean type. To achieve this, set ShowCheckbox property as true.

