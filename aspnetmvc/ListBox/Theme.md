---
layout: post
title: Theme
description: theme
platform: ejmvc
control: ListBox
documentation: ug
---

## Theme

ListBox control’s style and appearance can be controlled based on CSS classes. In order to apply styles to the ListBox control, you can refer to two files namely, ej.widgets.core.min.css and ej.theme.min.css. When you refer to the file ej.widgets.all.min.css, it is not necessary to include the files ej.widgets.core.min.css and ej.theme.min.css in your project, as ej.widgets.all.min.css is the combination of these two. 

By default, there are 12 themes support available for ListBox control namely,

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

The following screenshot illustrates the ListBox with Flat-lime and Flat-Saffron built-in themes.

{ ![C:/Users/Rajaveni/Desktop/docs/UG images/blog/flatlime.png](Theme_images/Theme_img1.png) | markdownify }
{:.image }


{ ![C:/Users/Rajaveni/Desktop/docs/UG images/blog/flatsaffron.png](Theme_images/Theme_img2.png) | markdownify }
{:.image }


Custom class with ListBox 

CSS class can be used to customize the ListBox control appearance. Define a CSS class as per your requirement and assign the class name to CssClass property. The data type of CssClass property is string. 

Configuring the Custom CSS property

The following steps explains you the configuration of CssClass properties in ListBox.

1. Add the below code in your view page to render the ListBox with custom css class.



<table>
<tr>
<td>
[View]// Add the following code in View page to configure ListBox widget&lt;div id="control"&gt;    &lt;h5 class="ctrllabel"&gt;        Select a skill    &lt;/h5&gt;    @Html.EJ().ListBox("listboxsample").Datasource((IEnumerable<ug_listbox.controllers.skillset>)ViewBag.datasource).ListBoxFields(df => df.Text("text")) .CssClass("customclass")&lt;/div&gt;</td></tr>
<tr>
<td>
[CS]// Add the following code to add list items in the controller page        public class skillset        {            public string text { get; set; }        }        public ActionResult Index()        {            List<skillset> skill = new List<skillset>();            skill.Add(new skillset { text = "ASP.NET" });            skill.Add(new skillset { text = "ActionScript" });            skill.Add(new skillset { text = "Basic" });            skill.Add(new skillset { text = "C++" });            skill.Add(new skillset { text = "C#" });            skill.Add(new skillset { text = "dBase" });            skill.Add(new skillset { text = "Delphi" });            skill.Add(new skillset { text = "ESPOL" });            skill.Add(new skillset { text = "F#" });            skill.Add(new skillset { text = "FoxPro" });            skill.Add(new skillset { text = "Java" });            skill.Add(new skillset { text = "J#" });            skill.Add(new skillset { text = "Lisp" });            skill.Add(new skillset { text = "Logo" });            skill.Add(new skillset { text = "PHP" });            ViewBag.datasource = skill;            return View();        }</td></tr>
</table>




1. Configure the CSS styles to apply on ListBox.



[CSS]  

&lt;style&gt;

    .customclass {

        background-color: #FFFFCC;

        font-weight: bold;

        font-family: sans-serif;

    }

&lt;/style&gt;



2. Output of the above steps.


{ ![](Theme_images/Theme_img3.png) | markdownify }
{:.image }


