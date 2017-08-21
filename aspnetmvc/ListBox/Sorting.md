---
layout: post
title: Sorting | ListBox | ASP.NET MVC | Syncfusion
description: sorting support 
platform: ejmvc
control: ListBox
documentation: ug
---

# Sorting

    We can change ListBox items rendering order either as ascending or descending, by using "SortOrder" property. By default SortOrder will be "None". Please use code as like in below,

    This is example code position of the ListBox may change if your are apply styles as per your requirement.

    1. Add the below code in your view page to render the ListBox with sorting option

        ~~~ cshtml
            //Add the following code in View page to configure ListBox widget
          <div class="contents">
                <span class="txt">Select skill</span>
                @Html.EJ().ListBox("skillSet").Datasource((IEnumerable<SkillSet>)ViewBag.DataSource1).SortOrder(SortOrder.None).ListBoxFields(df => df.Value("skill"))
            </div>
         ~~~

        ~~~ csharp
   
	// Add the following code to add listbox items in the controller page
 public partial class ListBoxController : Controller
    {
        List<SkillSet> veg1 = new List<SkillSet>();
        List<GroupList> skills = new List<GroupList>();
        // GET: /Sorting/
        public ActionResult Sorting()
        {            
            veg1.Add(new SkillSet { skill = "F#" });
            veg1.Add(new SkillSet { skill = "ActionScript" });
            veg1.Add(new SkillSet { skill = "Delphi" });
            veg1.Add(new SkillSet { skill = "Basic" });
            veg1.Add(new SkillSet { skill = "C++" });
            veg1.Add(new SkillSet { skill = "ESPOL" });
            veg1.Add(new SkillSet { skill = "C#" });
            veg1.Add(new SkillSet { skill = "DBase" });
            veg1.Add(new SkillSet { skill = "ASP.NET" });
            ViewBag.DataSource1 = veg1;
            return View();
            }
        }
        ~~~ 
    
    ~~~ csharp
         public class SkillSet
            {
               public string skill { get; set; }

            }
    ~~~ 

    once you have included the above code your output will be shown as given,

![](Sorting-Images\img1.png)