---
layout: post
title: Template Support | ListBox | ASP.NET MVC | Syncfusion
description: template support
platform: ejmvc
control: ListBox
documentation: ug
---

# Template Support

ListBox widget provides the template support, when binding the data for the ListBox. For this behavior, set the common syntax /element in template property. You can add any HTML mark-up element inside the ListBox using this property.

The following steps explains you the behavior of template support with ListBox.

1. Add the below code in your view page to render the ListBox

   N> Images for this sample are available in ‘installed location/images/Employee’



   ~~~ cshtml
	// Add the following code in View page to configure ListBox widget
	<div class="control">
		<div class="ctrllabel">
			Template support 
		</div>  
	@Html.EJ().ListBox("listBoxSample").Datasource((IEnumerable<employeespecialists>)ViewBag.datasource).Height("238")
	.Template("<img class='employeeImg' src='../../Content/images/Employees/${employeeImg}.png' alt='employee' height='50px' width='50px'/>
	<div class='ename'> 
		${text} 
	</div>
	<div class='design'>
		${design} 
	</div>
	<div class='cont'>
		${country} 
	</div>")
	</div>
	
   ~~~
   
   
   ~~~ csharp
   
	// Add the following code to add list items in the controller page 
	public class EmployeeSpecialists 
	{           
		public string text { get; set; }   
		public string employeemployeeImg { get; set; }   
		public string design { get; set; } 
		public string country { get; set; }  
	} 
	public ActionResult Index() 
	{
		List<EmployeeSpecialists> employeeList = new List<EmployeeSpecialists>();
		employeeList.Add(new EmployeeSpecialists { text = "Erik Linden", employeeImg = "3", design = "Representative", country = "England" }); 
		employeeList.Add(new EmployeeSpecialists { text = "John Linden", employeeImg = "6", design = "Representative", country = "Norway" }); 
		employeeList.Add(new EmployeeSpecialists { text = "Louis", employeeImg = "7", design = "Representative", country = "Australia" });  
		employeeList.Add(new EmployeeSpecialists { text = "Lawrence", employeeImg = "8", design = "Representative", country = "India" }); 
		ViewBag.datasource = employeeList;     
		return View();
	}

   ~~~
   


2. Customize the template in CSS. 


   ~~~ css

	<style>

		.employeeImg 
		{

			margin: 0;

			padding: 3px 10px 3px 3px;

			border: 0 none;

			width: 60px;

			height: 60px;

			float: left;

		}



		.ename 
		{

			font-weight: bold;

			padding: 6px 3px 1px 3px;

		}



		.design, .cont 
		{

			font-size: smaller;

			padding: 3px 3px -1px 0px;

		}



		#selectExperts li 
		{

			width: 200px;

			height: 70px;

			padding: 5px;

		}

	</style>

   ~~~
   



3. Output of the above steps.




![](Template-Support_images/Template-Support_img2.png)



