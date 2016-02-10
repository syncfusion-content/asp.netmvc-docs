---
layout: post
title: Cascading | ListBox | ASP.NET MVC | Syncfusion
description: cascading  
platform: ejmvc
control: ListBox
documentation: ug
---

# Cascading 

We can dynamically populate data of a list box while selecting an item in another list box i.e. rendering child list box based on the item selection in parent list box. This can be achieved using “CascadeTo” property.

In the Model page, define the Class name Groups and Category.

In the Controller, create a list of “Groups” and “Category” classes and add the data.


{% tabs %}        
{% highlight c# %}

//define model classes with the corresponding properties


    public class Groups
    {
        public string Text { get; set; }
        public string CategoryId { get; set; }
    }
    public class Category
    {
        public string Text { get; set; }
        public string CategoryId { get; set; }
        public int SubcategoryId { get; set; }
    }
    
//specify desired datasource data by using the model class properties

public partial class ListBoxController : Controller
    {
        List<Groups> group = new List<Groups>();
        List<Category> firstLevel = new List<Category>();

        public ActionResult Index()
        {
            group.Add(new Groups { CategoryId = "a", Text = "Clothing" });
            group.Add(new Groups { CategoryId = "b", Text = "Furniture" });
            ViewBag.datasource = group;
            //first level child 
            firstLevel.Add(new Category { SubcategoryId = 11, CategoryId = "a", Text = "Men" });
            firstLevel.Add(new Category { SubcategoryId = 12, CategoryId = "a", Text = "Women" });
            firstLevel.Add(new Category { SubcategoryId = 13, CategoryId = "b", Text = "Home furniture" });
            firstLevel.Add(new Category { SubcategoryId = 14, CategoryId = "b", Text = "Bedding" });
            ViewBag.datasource1 = firstLevel;
            return View();
        }
    }

{% endhighlight %}

{% highlight razor %}

<div class="parentlistbox">
    <!--parent listbox element-->
    @{Html.EJ().ListBox("category")
          .Datasource((IEnumerable<Groups>)ViewBag.datasource)
          .ListBoxFields(fields => fields.Value("CategoryId"))
          .CascadeTo("subcategoryList")
          .Render();}
</div>

<div class="childlistbox">
    <!-- child listbox element-->
    @{Html.EJ().ListBox("subcategoryList")
          .Datasource((IEnumerable<Category>)ViewBag.datasource1)
          .LoadDataOnInit(false)
          .Render();}
</div>
<style>
    .parentlistbox, .childlistbox {
        padding: 10px;
        float: left;
    }
</style>


{% endhighlight %}
{% endtabs %}


The parent child relationship should be defined in data sources of both the list boxes. I.e. both data sources should contain a common field for mapping (just like [primary key and foreign key definitions](https://msdn.microsoft.com/en-IN/library/ms179610.aspx)).

![](Cascading_images\Cascading_img1.png)

The parent ListBox widget’s “CascadeTo” property should point to its child ListBox widget by specifying the id of the child ListBox widget. The child ListBox widget can be displayed with empty data on initialize by setting its “LoadDataOnInit” property to false.

N> In the below data source definition, the “CategoryId” column will act as a primary key to define the parent-child relationship.

## Multilevel cascading

Please refer the below code snippets which is expanded from the above example, to achieve multi-level (three level here) cascading of the ListBox widgets.

Create the UL elements to render the parent and the child ListBox widgets as below.

In the Model page, define the Class name as Groups, Category, SubCategory, SubProduct.

In the Controller page, to create a List of Groups, Category, SubCategory, SubProduct classes and add the data.

In the View page, add ListBox helper as below.

{% tabs %} 
{% highlight c# %}

//define model classes with the corresponding properties

    public class Groups
    {
        public string Text { get; set; }
        public string CategoryId { get; set; }
    }
    public class Category
    {
        public string Text { get; set; }
        public string CategoryId { get; set; }
        public int SubcategoryId { get; set; }
    }
    public class SubCategory
    {
        public string Text { get; set; }
        public int ProductId { get; set; }
        public int SubcategoryId { get; set; }
    }
    public class SubProduct
    {
        public string Text { get; set; }
        public int ProductId { get; set; }
    }

//specify desired datasource data by using the model class properties

public partial class ListBoxController : Controller
    {
        List<Groups> group = new List<Groups>();
        List<Category> firstLevel = new List<Category>();
        List<SubCategory> secondLevel = new List<SubCategory>();
        List<SubProduct> thirdLevel = new List<SubProduct>();
        public ActionResult Index()
        {
            group.Add(new Groups {CategoryId = "a", Text = "Clothing" });
            group.Add(new Groups {CategoryId = "b", Text = "Furniture" });
            ViewBag.datasource = group;
            //first level child 
            firstLevel.Add(new Category { SubcategoryId = 11,CategoryId = "a", Text = "Men" });
            firstLevel.Add(new Category { SubcategoryId = 12,CategoryId = "a", Text = "Women" });
            firstLevel.Add(new Category { SubcategoryId = 13,CategoryId = "b", Text = "Home furniture" });
            firstLevel.Add(new Category { SubcategoryId = 14,CategoryId = "b", Text = "Bedding" });
            ViewBag.datasource1 = firstLevel;

            //second level child  
            secondLevel.Add(new SubCategory { ProductId = 101, SubcategoryId = 11, Text = "men shirts" });
            secondLevel.Add(new SubCategory { ProductId = 102, SubcategoryId = 11, Text = "men pants" });
            secondLevel.Add(new SubCategory { ProductId = 103, SubcategoryId = 12, Text = "women shirts" });
            secondLevel.Add(new SubCategory { ProductId = 104, SubcategoryId = 12, Text = "women pants" });
            secondLevel.Add(new SubCategory { ProductId = 105, SubcategoryId = 13, Text = "sofa" });
            secondLevel.Add(new SubCategory { ProductId = 106, SubcategoryId = 13, Text = "chairs" });
            secondLevel.Add(new SubCategory { ProductId = 106, SubcategoryId = 14, Text = "bedsheets" });
            secondLevel.Add(new SubCategory { ProductId = 108, SubcategoryId = 14, Text = "pillows" });
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


{% endhighlight %}

{% highlight razor %}

<div class="controlitem">
    @{Html.EJ().ListBox("groupsList")
          .Datasource((IEnumerable<Groups>)ViewBag.datasource)
          .ListBoxFields(df => df.Value("CategoryId"))
          .CascadeTo("subcategoryList")
          .Render();}
</div>
<div class="controlitem">
    @{Html.EJ().ListBox("subcategoryList")
          .Datasource((IEnumerable<Category>)ViewBag.datasource1)
          .ListBoxFields(df => df.Value("SubcategoryId"))
          .CascadeTo("productList")
          .LoadDataOnInit(false)
          .Render();}
</div>
<div class="controlitem">
    @{Html.EJ().ListBox("productList")
          .Datasource((IEnumerable<SubCategory>)ViewBag.datasource2)
          .ListBoxFields(df => df.Value("ProductId"))
          .CascadeTo("subproductList")
          .LoadDataOnInit(false)
          .Render();}
</div>
<div class="controlitem">
    @{Html.EJ().ListBox("subproductList")
          .Datasource((IEnumerable<SubProduct>)ViewBag.datasource3)
          .LoadDataOnInit(false)
          .Render();}
</div>
<style>
    .controlitem {
        float: left;
        padding: 10px;
    }
</style>


{% endhighlight %}
{% endtabs %}



![](Cascading_images\Cascading_img2.png)