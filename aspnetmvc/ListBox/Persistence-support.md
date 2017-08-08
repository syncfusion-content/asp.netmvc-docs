---
layout: post
title: Persistence support | ListBox | ASP.NET MVC | Syncfusion
description: persistence support 
platform: ejmvc
control: ListBox
documentation: ug
---

# Persistence support 

This features enables you to save current model value to browser cookies for state maintains. When you refresh the ListBox control page, it retains the model value apply from browser cookies. The date type of EnablePersistence is Boolean type. 

The following steps explains you the configuration of EnablePersistence property in ListBox.

1. Add the below code in your view page to render the ListBox


   ~~~ cshtml

	// Add the following code in View page to configure ListBox widget

	<div id="control">

		<h5 class="ctrllabel">

			Select a skill

		</h5>    @Html.EJ().ListBox("listBoxSample").Width("240").Datasource((IEnumerable<ug_listbox.controllers.skillSet>)ViewBag.datasource).ListBoxFields(df => df.Text("text")) .EnablePersistence(true)

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
   

