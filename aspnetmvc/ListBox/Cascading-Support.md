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
		 df.Value("CategoryId")).CascadeTo("subcategoryList")
	 </div>
	 <div class="controlitem">
		 @Html.EJ().ListBox("subcategoryList").Datasource((IEnumerable<Category>)ViewBag.datasource1).ListBoxFields(df => 
		 df.Value("SubCategoryId")).CascadeTo("productList").Enabled(false)
	 </div>
	 <div class="controlitem">
		@Html.EJ().ListBox("productList").Datasource((IEnumerable<SubCategory>)ViewBag.datasource2).ListBoxFields(df => 
		df.Value("ProductId")).CascadeTo("subProductList").Enabled(false)
	 </div>
	 <div class="controlitem"> 
		@Html.EJ().ListBox("subProductList").Datasource((IEnumerable<SubProduct>)ViewBag.datasource3).Enabled(false)
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
			group.Add(new Groups { CategoryId = "a", Text = "Clothing" });  
			group.Add(new Groups { CategoryId = "b", Text = "Furniture" }); 
			ViewBag.datasource = group;  
			//first level child 
			firstLevel.Add(new Category { SubCategoryId = 11, CategoryId = "a", Text = "Women" });   
			firstLevel.Add(new Category { SubCategoryId = 12, CategoryId = "b", Text = "Home furniture" });  
			firstLevel.Add(new Category { SubCategoryId = 13, CategoryId = "b", Text = "Bedding" });
			ViewBag.datasource1 = firstLevel; 

			//second level child  
			secondLevel.Add(new SubCategory { ProductId = 101, SubCategoryId = 11, Text = "men shirts" }); 
			secondLevel.Add(new SubCategory { ProductId = 102, SubCategoryId = 11, Text = "men pants" });
			secondLevel.Add(new SubCategory { ProductId = 103, SubCategoryId = 12, Text = "women shirts" });
			secondLevel.Add(new SubCategory { ProductId = 104, SubCategoryId = 12, Text = "women pants" });
			secondLevel.Add(new SubCategory { ProductId = 105, SubCategoryId = 13, Text = "sofa" });   
			secondLevel.Add(new SubCategory { ProductId = 106, SubCategoryId = 13, Text = "chairs" });
			secondLevel.Add(new SubCategory { ProductId = 106, SubCategoryId = 14, Text = "bedsheets" }); 
			secondLevel.Add(new SubCategory { ProductId = 108, SubCategoryId = 14, Text = "pillows" }); 
			ViewBag.datasource2 = secondLevel; 

			//third level child 
			thirdLevel.Add(new SubProduct { ProductId = 101, Text = "red men shirts" }); 
			thirdLevel.Add(new SubProduct { ProductId = 101, Text = "blue men shirts" }); 
			thirdLevel.Add(new SubProduct { ProductId = 102, Text = "red men pants" });  
			thirdLevel.Add(new SubProduct { ProductId = 102, Text = "blue men pants" }); 
			thirdLevel.Add(new SubProduct { ProductId = 103, Text = "blue women shirts" }); 
			thirdLevel.Add(new SubProduct { ProductId = 103, Text = "red women shirts" });  
			thirdLevel.Add(new SubProduct { ProductId = 104, Text = "red women pants" });  
			thirdLevel.Add(new SubProduct { ProductId = 104, Text = "blue women pants" });  
			thirdLevel.Add(new SubProduct { ProductId = 105, Text = "red sofa" });   
			thirdLevel.Add(new SubProduct { ProductId = 105, Text = "blue sofa" }); 
			thirdLevel.Add(new SubProduct { ProductId = 106, Text = "red chairs" }); 
			thirdLevel.Add(new SubProduct { ProductId = 106, Text = "blue chairs" });   
			thirdLevel.Add(new SubProduct { ProductId = 107, Text = "red bedsheets" }); 
			thirdLevel.Add(new SubProduct { ProductId = 107, Text = "blue bedsheets" });
			thirdLevel.Add(new SubProduct { ProductId = 108, Text = "red pillows" });    
			thirdLevel.Add(new SubProduct { ProductId = 108, Text = "blue pillows" });  
			ViewBag.datasource3 = thirdLevel; 
			return View();
		}
	}

   ~~~
   
   
   ~~~ csharp
		
	public class Groups
	{    
		public string Text { get; set; }
		public string CategoryId { get; set; }
		public class Category
		{   
			public string Text { get; set; } 
			public string CategoryId { get; set; }
			public int SubCategoryId { get; set; }
		}
		public class SubCategory
		{  
			public string Text { get; set; }  
			public int ProductId { get; set; }
			public int SubCategoryId { get; set; }
		}
		public class SubProduct
		{
			public string Text { get; set; }
			public int ProductId { get; set; }
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



