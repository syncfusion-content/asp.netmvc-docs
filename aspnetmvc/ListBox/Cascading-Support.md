---
layout: post
title: Cascading Support | ListBox | ASP.NET MVC | Syncfusion
description: cascading support 
platform: ejmvc
control: ListBox
documentation: ug
---

# Cascading Support 

Using cascade option, you can create a behavior of cascade between ListBox controls. For this, create a database with single field that is common between two ListBox data fields and then mention that column id in value field. With this, you can set second ListBox id in CascadeTo property in first ListBox. 

In the following code example, in the first and second ListBox, "categoryId" is the common field. 

The "categoryId" value of the selected item in the First Listbox that matches with "categoryId" value in the second Listbox, is retrieved and the item is loaded.


N> In case the second ListBox is to be disabled, until the first one is selected, you can set enable property as false in second ListBox that enables automatically once the value is selected in first one.

You can add any number of cascading ListBox. For this, create a Datasource with single field value that is common between the two consecutive cascading ListBox and cascading is achieved based on that common field.”  

The following steps explains you the behavior of cascade ListBox. 

1. Add the below code in your view page to render the ListBox with cascade option/

   ~~~ cshtml

	 // Add the following code in View page to configure ListBox widget
	 <div class="controlitem"> 
		 <span class="txt">
			Cascading Listbox
		 </span>
		 @Html.EJ().ListBox("groupsList").Datasource((IEnumerable<Groups>)ViewBag.datasource).ListBoxFields(df => 
		 df.Value("categoryId")).CascadeTo("subcategoryList")
	 </div>
	 <div class="controlitem">
		 @Html.EJ().ListBox("subcategoryList").Datasource((IEnumerable<Category>)ViewBag.datasource1).ListBoxFields(df => 
		 df.Value("subCategoryId")).CascadeTo("productList").Enabled(false)
	 </div>
	 <div class="controlitem">
		@Html.EJ().ListBox("productList").Datasource((IEnumerable<SubCategory>)ViewBag.datasource2).ListBoxFields(df => 
		df.Value("productId")).CascadeTo("subproductList").Enabled(false)
	 </div>
	 <div class="controlitem"> 
		@Html.EJ().ListBox("subproductList").Datasource((IEnumerable<SubProduct>)ViewBag.datasource3).Enabled(false)
	 </div>
 
   ~~~
   
   
   ~~~ csharp
   
	// Add the following code to add list items in the controller page
	public partial class ListBoxController : Controller
	{    
		List<Groups> group = new List<Groups>();
		List<Category> firstLevel = new List<Category>(); 
		List<SubCategory> secondLevel = new List<SubCategory>();
		List<SubProduct> thirdLevel = new List<SubProduct>(); 
		public ActionResult Cascading()  
		{       
			group.Add(new Groups { categoryId = "a", text = "Clothing" });  
			group.Add(new Groups { categoryId = "b", text = "Furniture" }); 
			ViewBag.datasource = group;  
			//first level child 
			firstLevel.Add(new Category { subCategoryId = 11, categoryId = "a", text = "Women" });   
			firstLevel.Add(new Category { subCategoryId = 12, categoryId = "b", text = "Home furniture" });  
			firstLevel.Add(new Category { subCategoryId = 13, categoryId = "b", text = "Bedding" });
			ViewBag.datasource1 = firstLevel; 

			//second level child  
			secondLevel.Add(new SubCategory { productId = 101, subCategoryId = 11, text = "men shirts" }); 
			secondLevel.Add(new SubCategory { productId = 102, subCategoryId = 11, text = "men pants" });
			secondLevel.Add(new SubCategory { productId = 103, subCategoryId = 12, text = "women shirts" });
			secondLevel.Add(new SubCategory { productId = 104, subCategoryId = 12, text = "women pants" });
			secondLevel.Add(new SubCategory { productId = 105, subCategoryId = 13, text = "sofa" });   
			secondLevel.Add(new SubCategory { productId = 106, subCategoryId = 13, text = "chairs" });
			secondLevel.Add(new SubCategory { productId = 106, subCategoryId = 14, text = "bedsheets" }); 
			secondLevel.Add(new SubCategory { productId = 108, subCategoryId = 14, text = "pillows" }); 
			ViewBag.datasource2 = secondLevel; 

			//third level child 
			thirdLevel.Add(new SubProduct { productId = 101, text = "red men shirts" }); 
			thirdLevel.Add(new SubProduct { productId = 101, text = "blue men shirts" }); 
			thirdLevel.Add(new SubProduct { productId = 102, text = "red men pants" });  
			thirdLevel.Add(new SubProduct { productId = 102, text = "blue men pants" }); 
			thirdLevel.Add(new SubProduct { productId = 103, text = "blue women shirts" }); 
			thirdLevel.Add(new SubProduct { productId = 103, text = "red women shirts" });  
			thirdLevel.Add(new SubProduct { productId = 104, text = "red women pants" });  
			thirdLevel.Add(new SubProduct { productId = 104, text = "blue women pants" });  
			thirdLevel.Add(new SubProduct { productId = 105, text = "red sofa" });   
			thirdLevel.Add(new SubProduct { productId = 105, text = "blue sofa" }); 
			thirdLevel.Add(new SubProduct { productId = 106, text = "red chairs" }); 
			thirdLevel.Add(new SubProduct { productId = 106, text = "blue chairs" });   
			thirdLevel.Add(new SubProduct { productId = 107, text = "red bedsheets" }); 
			thirdLevel.Add(new SubProduct { productId = 107, text = "blue bedsheets" });
			thirdLevel.Add(new SubProduct { productId = 108, text = "red pillows" });    
			thirdLevel.Add(new SubProduct { productId = 108, text = "blue pillows" });  
			ViewBag.datasource3 = thirdLevel; 
			return View();
		}
	}

   ~~~
   
   
   ~~~ csharp
		
	public class Groups
	{    
		public string text { get; set; }
		public string categoryId { get; set; }
		public class Category
		{   
			public string text { get; set; } 
			public string categoryId { get; set; }
			public int subCategoryId { get; set; }
		}
		public class SubCategory
		{  
			public string text { get; set; }  
			public int productId { get; set; }
			public int subCategoryId { get; set; }
		}
		public class SubProduct
		{
			public string text { get; set; }
			public int productId { get; set; }
		}
		
	}

   ~~~
   


2. Configure the styles as follows.



   ~~~ cshtml 

	<style>

		.controlitem {

			margin-left: 50px;

			display: inline-block;

		}

	</style>

   ~~~
   

3. Output of the above steps.



![](Cascading-Support_images/Cascading-Support_img2.png)



