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

		</h5>    @Html.EJ().ListBox("listboxsample").Width("240").Datasource((IEnumerable<ug_listbox.controllers.skillset>)ViewBag.datasource).ListBoxFields(df => df.Text("text")) .EnablePersistence(true)

	</div>

   ~~~
   

   ~~~ csharp

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
   

