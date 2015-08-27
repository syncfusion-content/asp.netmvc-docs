---
layout: post
title: Data-Binding
description: data binding
platform: ejmvc
control: Toolbar
documentation: ug
---

# Data Binding

Toolbar provides you a flexible approach for binding data from various data sources. There are various properties in Toolbar for Data Binding.

## Data fields and configuration 

The following sub-properties provides a way to bind either the local/remote data to the Toolbar control.



_Table: Property Table of MVC Toolbar control_

<table>
<tr>
<th>
Property</th><th>
Value type</th><th>
Description</th></tr>
<tr>
<td>
Datasource</td><td>
object</td><td>
It specifies the data source of the Toolbar. The data source contains the list of data for generating the Toolbar items.</td></tr>
<tr>
<td>
Fields</td><td>
object</td><td>
It specifies the mapping fields for the data items of the Toolbar.</td></tr>
<tr>
<td>
Id</td><td>
string</td><td>
It specifies the id of the element</td></tr>
<tr>
<td>
Text</td><td>
string</td><td>
It specifies the text content of the element.</td></tr>
<tr>
<td>
ImageUrl</td><td>
string</td><td>
This property defines the imageURL for the image location. While setting images, the folder name in which the images are stored should be set to imageUrl property.</td></tr>
<tr>
<td>
ImageAttributes</td><td>
string</td><td>
This property defines style for the image. While setting an image, styles can be applied such as height, width by using this property.</td></tr>
<tr>
<td>
SpriteCssClass</td><td>
string</td><td>
This property sets the Sprite CSS for the image element in Toolbar.</td></tr>
<tr>
<td>
HtmlAttributes</td><td>
object</td><td>
This property sets the HTML attribute for the Toolbar item. It can be any HTML attribute such as id, class, style.</td></tr>
<tr>
<td>
TooltipText</td><td>
string</td><td>
This property sets the text value for Toolbar item while mouse over in Toolbar.</td></tr>
<tr>
<td>
Query</td><td>
object</td><td>
It specifies the query to retrieve the data from online server.</td></tr>
<tr>
<td>
Group</td><td>
string</td><td>
It groups the given Toolbar items.</td></tr>
</table>


## Local data

To bind the Local Data to the Toolbar control, map the user-defined JSON data names with its appropriate data source field. You can bind data to Toolbar by mapping fields such as Id, SpriteCssClass, ImageUrl, group and TooltipText.

The following steps explain how you can bind local data to Toolbar Control.

In the View page, add Toolbar helper to configure Toolbar. 


{% highlight C# %}
// Add the following data list to be bind in the controller page and define the corresponding data.
// Define local data source elements with  fields 
 public class ToolbarLocalBinding 
 {     
	public string IconId { get; set; } 
	public string SpriteCss { get; set; }
	public string Tooltip { get; set; }   
	}
 
 //Refer the Model in the controller
 using <Applicationname>.Models;
 public ActionResult Index()
 { 
	List<ToolbarLocalBinding> toolslist = new List<ToolbarLocalBinding>(); 
	toolslist.Add(new ToolbarLocalBinding { IconId = "1", SpriteCss = "LeftAlign_tool", Tooltip = "left" });
	toolslist.Add(new ToolbarLocalBinding { IconId = "2", SpriteCss = "CenterAlign_tool", Tooltip = "centre" }); 
	toolslist.Add(new ToolbarLocalBinding { IconId = "3", SpriteCss = "RightAlign_tool", Tooltip = "right" });  
	toolslist.Add(new ToolbarLocalBinding { IconId = "4", SpriteCss = "Justify_tool", Tooltip = "justify" });  
	toolslist.Add(new ToolbarLocalBinding { IconId = "5", SpriteCss = "Bold_tool", Tooltip = "bold" });  
	toolslist.Add(new ToolbarLocalBinding { IconId = "6", SpriteCss = "Italic_tool", Tooltip = "italic" }); 
	toolslist.Add(new ToolbarLocalBinding { IconId = "7", SpriteCss = "StrikeThrough_tool", Tooltip = "strike" });  
	toolslist.Add(new ToolbarLocalBinding { IconId = "8", SpriteCss = "Underline_tool", Tooltip = "underline" }); 
	ViewBag.datasource = toolslist; 
	return View();    
 }
{% endhighlight %} 

{% highlight html %} 
 <div class="cols-sample-area"> 
 @Html.EJ().Toolbar("toolbarcontent").Width("250").Datasource((IEnumerable<MVCSamples.Models.ToolbarLocalBinding>)
 ViewBag.datasource).ToolbarFields(f => f.ID("IconId").SpriteCssClass("SpriteCss").TooltipText("Tooltip"))
 .Orientation(Orientation.Horizontal)
 </div>
 {% endhighlight %}


{% highlight css%}

<style type="text/css" class="cssStyles">

    .darktheme .cols-sample-area .e-tooltxt .ToolbarItems {

        background-image: url('../images/toolbar/ui-icons-metro.png');

    }



    .cols-sample-area .e-tooltxt .ToolbarItems {

        display: block;

        background-image: url('../images/toolbar/ui-icons-dark.png');

        height: 22px;

        width: 22px;

    }



    .e-tooltxt:hover .ToolbarItems, .darktheme .cols-sample-area .e-tooltxt:hover .ToolbarItems {

        background-image: url('../images/toolbar/ui-icons-light.png');

    }



    .ToolbarItems.LeftAlign_tool {

        background-position: -26px -39px;

    }



    .ToolbarItems.CenterAlign_tool {

        background-position: -55px -39px;

    }



    .ToolbarItems.RightAlign_tool {

        background-position: -89px -39px;

    }



    .ToolbarItems.Justify_tool {

        background-position: -123px -39px;

    }



    .ToolbarItems.Bold_tool {

        background-position: -159px -39px;

    }



    .ToolbarItems.Italic_tool {

        background-position: -196px -39px;

    }



    .ToolbarItems.StrikeThrough_tool {

        background-position: -55px -70px;

    }



    .ToolbarItems.Underline_tool {

        background-position: -23px -68px;

    }



    .html {

        background-color: yellowgreen;

    }

</style>

{% endhighlight %}

![](Data-Binding_images/Data-Binding_img1.png)


_Figure 6: ToolBar control bounded to Local Data_

## Remote data

You can bind Toolbar to Remote Data using DataManager and the query in fields is used to retrieve the data. DataManager supports the following types of data-binding: JSON, Web Services and OData. It uses two different classes; ej.DataManager for processing, and ej.Query for serving data. ej.DataManager communicates with data source and ej.Query generates data queries that are read by the DataManager. In the following link, how to create DataManager is explained in full detail.

<http://docs.syncfusion.com/aspnetmvc/toolbar/data-binding>

The following steps explain how you can bind remote data to Toolbar control.

1. In the View page, add Toolbar helper to configure Toolbar.



{% highlight js %}

@Html.EJ().Toolbar("toolbarcontent").Datasource(ds => ds.URL("http://mvc.syncfusion.com/Services/Northwnd.svc/")).Query("ej.Query().from('Orders').take(6)").ToolbarFields(f => f.Text("CustomerID")).Orientation(Orientation.Horizontal).Width("340")

{% endhighlight %}

![](Data-Binding_images/Data-Binding_img2.png)



_Figure 7: ToolBar control bounded to Remote Data_

