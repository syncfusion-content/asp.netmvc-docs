---
layout: post
title: Orientation | Toolbar | ASP.NET MVC | Syncfusion
description: orientation
platform: ejmvc
control: Toolbar
documentation: ug
---

# Orientation

The Toolbar control supports both vertical and horizontal orientations, allowing it to fit into any scenario. The Orientation property of Toolbar defines the orientation in which the control is rendered. Set the value to this property as enum or string type. It accepts the following values.

* Syncfusion.JavaScript.Orientation.Horizontal
* Syncfusion.JavaScript.Orientation.Vertical

The following section explains you on how to set orientation for the toolbar.

## Horizontal

By default the Orientation property sets the Toolbar in horizontal orientation. You can refer the following steps to set horizontal orientation for Toolbar control. Default value of Orientation is Horizontal.

1. In View, create UL-LI list of toolbar items and invoke the toolbar helper.
2. Add the following code in your CSHTML page.

   ~~~ cshtml

	// Add this code in your CSHTML page and refer local data section for data source

	<div class="cols-sample-area">    @Html.EJ().Toolbar("toolbar").Width("250").Datasource((IEnumerable<ToolbarLocalBinding>)ViewBag.datasource).ToolbarFields(f => f.ID("IconId").SpriteCssClass("SpriteCss").TooltipText("Tooltip")).Orientation(Syncfusion.JavaScript.Orientation.Horizontal)

	</div>

   ~~~
   


3. Build and run the application.

The following screenshot illustrates a Toolbar with horizontal orientation.



![](Orientation_images/Orientation_img1.png)

Toolbar with Horizontal Orientation
{:.caption}



## Vertical

This property sets the Toolbar in vertical orientation. You can refer the following steps to set Vertical Orientation for Toolbar control.

1. Create UL-LI list of toolbar items and invoke the toolbar helper.
2. Add the following script in your HTML page.

   ~~~ cshtml

   // Add this code in your CSHTML page and refer local data section for data source

	<div class="cols-sample-area">    
	
		@Html.EJ().Toolbar("toolbar").Width("250").Datasource((IEnumerable<ToolbarLocalBinding>)ViewBag.datasource).ToolbarFields(f => f.ID("IconId").SpriteCssClass("SpriteCss").TooltipText("Tooltip")).Orientation(Syncfusion.JavaScript.Orientation.Vertical)

	</div>

   ~~~
   


3. Build and run the application.

The following screenshot illustrates a Toolbar with vertical orientation.

![](Orientation_images/Orientation_img2.png)

Toolbar with Vertical Orientation
{:.caption}

