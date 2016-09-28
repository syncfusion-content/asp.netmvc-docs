---
layout: post
title: TreeView with Multiple Drag and Drop option | TreeView | ASP.NET MVC | Syncfusion
description: specify multiple drag and drop option in TreeView and its settings
platform: ejmvc
control: TreeView
documentation: ug
---


# Drag and Drop Multiple Nodes

TreeView supports to drag and drop multiple nodes by specifying [allowMultiSelection](http://help.syncfusion.com/js/api/ejtreeview#members:allowmultiselection) as true along with [allowDragAndDrop](https://help.syncfusion.com/js/api/ejtreeview#members:allowdraganddrop) as true. It allows you to drag and drop multiple nodes in TreeView.

In the controller page, create a data list that contains the details about tree nodes.

{% highlight c# %}

	public partial class TreeViewController : Controller
	{
		List<LoadData> tree1 = new List<LoadData>();
		List<LoadData> tree2 = new List<LoadData>();
		public ActionResult Index()
		{
			tree1.Add(new LoadData { Id = 1, Parent = 0, Text = "Item 1" });
			tree1.Add(new LoadData { Id = 2, Parent = 0, Text = "Item 2" });
			tree1.Add(new LoadData { Id = 3, Parent = 0, Text = "Item 3" });
			tree1.Add(new LoadData { Id = 4, Parent = 0, Text = "Item 4" });
			tree1.Add(new LoadData { Id = 5, Parent = 1, Text = "Item 1.1" });
			tree1.Add(new LoadData { Id = 6, Parent = 1, Text = "Item 1.2" });
			tree1.Add(new LoadData { Id = 7, Parent = 1, Text = "Item 1.3" });
			tree1.Add(new LoadData { Id = 8, Parent = 3, Text = "Item 3.1" });
			tree1.Add(new LoadData { Id = 9, Parent = 3, Text = "Item 3.2" });
			tree1.Add(new LoadData { Id = 10, Parent = 5, Text = "Item 1.1.1" });
			ViewBag.datasource1 = tree1;
	
			tree2.Add(new LoadData { Id = 11, Parent = 0, Text = "Item 5" });
			tree2.Add(new LoadData { Id = 12, Parent = 0, Text = "Item 6" });
			tree2.Add(new LoadData { Id = 13, Parent = 0, Text = "Item 7" });
			tree2.Add(new LoadData { Id = 14, Parent = 0, Text = "Item 4" });
			tree2.Add(new LoadData { Id = 15, Parent = 11, Text = "Item 5.1" });
			tree2.Add(new LoadData { Id = 16, Parent = 11, Text = "Item 5.2" });
			tree2.Add(new LoadData { Id = 17, Parent = 11, Text = "Item 5.3" });
			tree2.Add(new LoadData { Id = 18, Parent = 13, Text = "Item 7.1" });
			tree2.Add(new LoadData { Id = 19, Parent = 13, Text = "Item 7.2" });
			tree2.Add(new LoadData { Id = 10, Parent = 15, Text = "Item 5.1.1" });
			ViewBag.datasource2 = tree2;
			return View();
		}
	}
	public class LoadData
	{
		public int Id { get; set; }
		public int? Parent { get; set; }
		public string Text { get; set; }
		public bool? hasChild { get; set; }
		public bool? expanded { get; set; }
		public bool? ischecked { get; set; }
		public bool? selected { get; set; }
		public string spriteCss { get; set; }
	}

{% endhighlight %}

In the view page, add TreeView helper and map the properties defined in to the corresponding fields in data source and specify the multiple drag and drop settings.

{% highlight razor %}

	@Html.EJ().TreeView("treeViewDrag").TreeViewFields(fields =>
		fields.Datasource((IEnumerable<LoadData>)ViewBag.datasource1)
			.Id("Id")
			.ParentId("Parent")
			.Text("Text")
		).AllowMultiSelection(true).AllowDragAndDrop(true)
	
	<br />
	
	@Html.EJ().TreeView("treeViewDrop").TreeViewFields(fields =>
		fields.Datasource((IEnumerable<LoadData>)ViewBag.datasource2)
			.Id("Id")
			.ParentId("Parent")
			.Text("Text")
		).AllowMultiSelection(true).AllowDragAndDrop(true)
	
{% endhighlight %}

