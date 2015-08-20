---
layout: post
title: Load-on-Demand
description: load on demand
platform: ejmvc
control: TreeView
documentation: ug
---

# Load on Demand

Loadon Demand option is useful when the full content of the TreeView is too large to be loaded completely, up front. The mechanism lets the nodes load their child nodes as you expand the parent by clicking the expandicon. While clicking on the parent node it first loads their particular child nodes and then loads the first level of nodes.

This feature is used reduce the loading time of the large number nodes in TreeView. For example, when you are using the TreeView with 10,000 nodes or greater, it takes a long time to load their child nodes. In this case, Load on Demand is used to load the particular part of child nodes when you click their parent node. Hence it reduces the loading time of TreeView.

To enable load on demand, set the value as ‘true’ for the LoadOnDemand property.

The following steps explains how to configure TreeView component with LodOnDemand property

As explained in the local data source add a class in the models with required properties. Then define the List in the controller page and add the objects. Then in the View page, using the TreeView helper map the List properties to the corresponding TreeView fields. 

1. In the Controller page, add a class and define the properties (or) in the Models, add a class as shown below
  
   ~~~ html


		// Define local data source elements with  fields            



		public class treeviewData

		    {

		       //TreeView data source should have Id, ParentId and Text as mandatory

			public int Id { get; set; }

		       // ParentId takes the value of the parent nodes Id

			public int Pid { get; set; }

		       //Text to be displayed in the TreeView node

			public string Name { get; set; }

		       //Set to true if node has children

			public bool HasChild { get; set; }      



		    }

   ~~~
   {:.prettyprint }


2. In the controller page, create a List of specified class type.

   ~~~ cs


		//Refer the Model in the controller

		using <Applicationname>.Models;



		public ActionResult Index()

		    {

			    List<treeviewData> localData = new List<treeviewData>();

			    localData.Add(new treeviewData{ id= 1, name= "Favorites", hasChild= true });

			    localData.Add(new treeviewData{ id= 2, pid= 1, name= "Desktop" });

			    localData.Add(new treeviewData{ id= 3, pid= 1, name= "Downloads" });

			    localData.Add(new treeviewData{ id = 4, pid = 1, name = "Recent places" });

			    localData.Add(new treeviewData{ id= 5, name= "libraries", hasChild= true });

			    localData.Add(new treeviewData{ id= 6, pid= 5, name= "Documents", hasChild= true });


			    localData.Add(new treeviewData{ id= 7, pid= 6, name= "My Documents" });

			    localData.Add(new treeviewData{ id= 8, pid= 6, name= "Public Documents" });

			    localData.Add(new treeviewData{ id= 9, pid= 5, name= "Pictures", hasChild= true });

			    localData.Add(new treeviewData{ id= 10, pid= 9, name= "My Pictures" });

			    localData.Add(new treeviewData{ id= 11, pid= 9, name= "Public Pictures" });

			    localData.Add(new treeviewData{ id= 12, pid= 5, name= "Music", hasChild= true });

			    localData.Add(new treeviewData{ id= 13, pid= 9, name= "My Music" });

			    localData.Add(new treeviewData{ id= 14, pid= 9, name= "Public Music" });

			    localData.Add(new treeviewData{ id= 15, pid= 5, name= "Subversion" });

			    localData.Add(new treeviewData{ id= 16, name= "Computer", hasChild= true });

			    localData.Add(new treeviewData{ id= 17, pid= 16, name= "Folder(C)" });

			    localData.Add(new treeviewData{ id= 18, pid= 16, name= "Folder(D)" });

			    localData.Add(new treeviewData{ id= 19, pid= 16, name= "Folder(F)" });


			    ViewBag.datasource = localData;

			    return View();

		   }

   ~~~
   {:.prettyprint }



{% highlight js %}

// Map Local datasource to corresponding fields and enable LoadOnDemand for TreeView control

@Html.EJ().TreeView("tree").TreeViewFields(s => s.Datasource((IEnumerable<treeviewData>)ViewBag.datasource).Id("id").ParentId("pid").Text("name").HasChild("hasChild")).LoadOnDemand(true)

{% endhighlight %}

The output for TreeView when LoadOnDemand is set to “True” is as follows.

<table>
<tr>
<td>
{{ '![](Load-on-Demand_images/Load-on-Demand_img1.png)' | markdownify }}

While Loading</td><td>
{{ '![](Load-on-Demand_images/Load-on-Demand_img2.png)' | markdownify }}

After Loading</td></tr>
</table>


_Figure51: TreeView with loadOnDemand_

