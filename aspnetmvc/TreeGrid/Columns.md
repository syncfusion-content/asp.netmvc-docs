---
layout: post
title: Columns | TreeGrid | ASP.NET MVC | Syncfusion
description: columns
platform: ejmvc
control: TreeGrid
documentation: ug
---

# Columns

The TreeGrid column displays the information from a bounded data source and it is editable to update the task details through TreeGrid.

## Column Resizing

You can change the width of the column in TreeGrid to show the entire text of the column by resizing the column. The following code example shows you how to enable the Column Resize feature at Gantt initialize.


{% highlight CSHTML %}


@(Html.EJ().TreeGrid("TreeGridContainer")                              

.AllowColumnResize(true)

}

{% endhighlight  %}



## Column Template

Column Template is used to customize the column’s look and feel based on requirement.

The following code example shows you how to display the icon in the TreeGrid column.


{% tabs %}
 
{% highlight C# %}

public partial class TreeGridController : Controller

{

	// GET: /TreeGridColumnTemplate/

	public ActionResult TreeGridColumnTemplate()

	{

		var data=this.GetColumnTemplateDataSource();

		ViewBag.datasource = data;

		return View();

	}

	private List<ColumnTemplate> GetColumnTemplateDataSource()

	{

		List<ColumnTemplate> TreeGridCollection = new List<ColumnTemplate>();



		ColumnTemplate ParentRecord = null;



		ParentRecord = new ColumnTemplate()

		{

			Name = "JS",

			DateModified = "06/26/2014",

			Type = "File Folder",

			DateCreated = "06/16/2014",

			Children = new List<ColumnTemplate>()

		};

		ColumnTemplate ParentRecord1 = new ColumnTemplate()

		{

			Name = "sample",

			DateModified = "06/26/2014",

			Type = "File Folder",

			DateCreated = "06/16/2014",

			Children = new List<ColumnTemplate>()

		};

		ColumnTemplate ParentRecord2 = new ColumnTemplate()

		{

			Name = "web",

			DateModified = "06/26/2014",

			Type = "File Folder",

			DateCreated = "06/16/2014",

			Children = new List<ColumnTemplate>()

		};

		ColumnTemplate ParentRecord3 = new ColumnTemplate()

		{

			Name = "treegrid",

			DateModified = "06/26/2014",

			Type = "File Folder",

			DateCreated = "06/16/2014",

			Children = new List<ColumnTemplate>()

		};

		ColumnTemplate ChildRecord1 = new ColumnTemplate()

		{

			Name = "treegrid.html",

			DateModified = "06/26/2014",

			Type = "HTML document",

			DateCreated = "06/16/2014",

		};

		ColumnTemplate ChildRecord2 = new ColumnTemplate()

		{

			Name = "editing.html",

			DateModified = "06/26/2014",

			Type = "HTML document",

			DateCreated = "06/16/2014",

		};

		ColumnTemplate ChildRecord3 = new ColumnTemplate()

		{

			Name = "sorting.html",

			DateModified = "06/26/2014",

			Type = "HTML document",

			DateCreated = "06/16/2014",

		};

		ParentRecord3.Children.Add(ChildRecord1);

		ParentRecord3.Children.Add(ChildRecord2);

		ParentRecord3.Children.Add(ChildRecord3);

		ParentRecord2.Children.Add(ParentRecord3);

		ParentRecord1.Children.Add(ParentRecord2);

		ParentRecord.Children.Add(ParentRecord1);

		TreeGridCollection.Add(ParentRecord);

		return TreeGridCollection;

	}

	public class ColumnTemplate

	{

		public string Name

		{

			get;

			set;

		}

		public string DateModified

		{

			get;

			set;

		}

		public string Type

		{

			get;

			set;

		}

		public string DateCreated

		{

			get;

			set;

		}

		public List<ColumnTemplate> Children

		{

			get;

			set;

		}



	}
}
{% endhighlight  %}
{% highlight CSHTML %}


<script type="text/x-jsrender" id="customColumnTemplate">     

<div  style='height:20px;' unselectable='on'>{{if hasChildRecords}}<div class='intend' style='height:1px; float:left; width:{{:level*20}}px; display:inline-block;'></div>

	{{else !hasChildRecords}}

	<div class='intend' style='height:1px; float:left; width:{{:(level)*20}}px; display:inline-block;'></div>

	{{/if}}                         

	<div class='{{if expanded}}e-treegridexpand {{else hasChildRecords}}e-treegridcollapse {{/if}} {{if level===4}}e-doc{{/if}}' style='height:20px;width:30px;margin:auto;float:left;margin-left:10px;

	style='float: left;display:inline-block; unselectable='on'></div>

	<div class='e-cell' style='display:inline-block;width:100%' unselectable='on'>{{:#data['Name']}}</div>

</div>

</script>   

<style>

	.e-treegrid .e-treegridexpand 
	{

		background-image: url(../../images/treegrid/folder-open.png);

		background-repeat: no-repeat;

		width: 14px;

		height: 14px;

	}

	.e-treegrid .e-treegridcollapse 
	{

		background-image: url(../../images/treegrid/Folder.png);

		background-repeat: no-repeat;

		width: 14px;

		height: 14px;

	}

	.e-treegrid .e-doc 
	{

		background-image: url(../../images/treegrid/Document.png);

		background-repeat: no-repeat;

		width: 14px;

		height: 14px;

	}



	.e-treegrid .e-treegridexpand:before 
	{

		content: none;

	}



	.e-treegrid .e-treegridcollapse:before 
	{

		content: none;

	}

</style> 



@(Html.EJ().TreeGrid("TreeGridContainer")      

.Columns(co=>

   {

	   co.Field("Name").headerText("Name").IsTemplateColumn(true).TemplateID("customColumnTemplate").Add();

	   co.Field("Type").headerText("Type").Add();

	   co.Field("DateCreated").headerText("Date Created").Add();

	   co.Field("DateModified").headerText("Date Modified").Add();

   }

)

.ChildMapping("Children")

.Datasource(ViewBag.datasource)

)

}   

{% endhighlight %}
{% endtabs %}  
The following screenshot displays the customized column in TreeGrid control.

![](Columns_images/Columns_img1.png)



## Column Filtering

Column Filtering in TreeGrid is used to filter the records by single or multiple column conditions. In TreeGrid control, column filtering can be enabled with AllowFiltering property, by setting this property to ‘true’, a filter bar is rendered in all available columns, providing filtering support to every columns. You can also limit filtering to specific column by setting ‘false’ to AllowFiltering property in each column object.

Filtering modes can be toggled between Immediate and OnEnter modes using FilterBarMode property.

* Immediate- In this mode, filtering starts with key press event.
* OnEnter- In this mode, filtering starts when enter key is pressed.

Filtering type can be defined by FilterEditType property in each column object.

### FilterEditType:

* String
* Numeric
* Boolean
* Dropdownlist
* Datepicker
* Datetimepicker


{% highlight CSHTML %}

@(Html.EJ().TreeGrid("treegrid1")

	.AllowFiltering(true)

   .Columns(co =>

	   {

		   co.Field("TaskId").headerText("Task Id").EditType(TreeGridEditingType.Numeric).AllowFiltering(false).Width(45).Add();

		   co.Field("TaskName").headerText("Task Name").EditType(TreeGridEditingType.String).FilterEditType(TreeGridFilterEditType.String).Add();

		   co.Field("StartDate").headerText("Start Date").EditType(TreeGridEditingType.Datepicker).FilterEditType(TreeGridFilterEditType.Datepicker).Add();

		   co.Field("EndDate").headerText("End Date").EditType(TreeGridEditingType.Datepicker).FilterEditType(TreeGridFilterEditType.Datepicker).Add();

		   co.Field("Duration").headerText("Duration").EditType(TreeGridEditingType.Numeric).FilterEditType(TreeGridFilterEditType.Numeric).Add();

		   co.Field("Progress").headerText("Progress").EditType(TreeGridEditingType.Numeric).FilterEditType(TreeGridFilterEditType.Numeric).Add();

	   }

   )

.Render())

{% endhighlight %}



The following screenshot displays the column filtering in TreeGrid control.

![](Columns_images/Columns_img2.png)


## Column Chooser

TreeGrid supports enabling and disabling the visibility of the columns dynamically with the ShowColumnChooser property. By using this property, the visibility of the custom columns can also be toggled. The Column chooser option is rendered as sub menu item within column menu in the TreeGrid columns.

![](Columns_images/Columns_img3.png)



The column menu is enabled with the ShowColumnChooser property and the default value for this property is false

The column menu provides the following options

* Sort Ascending
* Sort Descending
* Columns 

The Sort Ascending and Sort Descending options are enabled or disabled by using the AllowSorting property. With these options, single level sorting can be performed in the TreeGrid columns. To perform multilevel sorting, the AllowMultiSorting property should be enabled. 

You can also disable the visibility of the particular column in column collection manually by setting the Visible property to false.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("treegrid1")

    .ShowColumnChooser(true)

    .AllowSorting(true)

    .AllowMultiSorting(true)

    .Columns(co=>

     {
         co.Field("duration").HeaderText("Duration").Visible(false)

     }

    )

)



{% endhighlight %}

![](Columns_images/Columns_img4.png)



