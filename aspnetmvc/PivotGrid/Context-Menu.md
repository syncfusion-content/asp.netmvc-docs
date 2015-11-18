---
layout: post
title: Context Menu | PivotGrid | ASP.NET MVC | Syncfusion
description: context menu
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Context Menu

Cell Context support in PivotGrid allows you to choose the right-click event to access each cell for any desired operation. CellContext is enabled by setting the enableCellContext property to ‘True’. The name of the event to trigger on right-clicking is stored in the cellContextEvent property. After enabling CellContext on right-clicking a cell, the event triggers. The information about the cell is carried through a parameter.

The following code example illustrates how to create the PivotGrid control with the enabled CellContext. Here, the CellContext event displays a pop-up menu as follows.


{% highlight CSHTML %}

@section StyleSection
{ 
<style>
	#PivotGrid1 
	{  
	   width:100%;  
	   height:350px;
	   overflow:auto; 
	}	    
	.menuItem 
	{
		padding:5px 50px 5px 20px; 
	}
	.contextMenuPopup
	{ 
		position: absolute;
		background-color: #e6e6e6;
		border: #BBBCBB solid 1px; 
		padding: 1px;        
		color:#565656;  
	}       
	.activeMenuItemBlue
	{ 
		background-color:#66C1DC; 
		color:white; 
	}
	.activeMenuItemGreen 
	{ 
		background-color:#AECF49; 
		color:white;     
	}  
	.activeMenuItemOrange 
	{     
		background-color:#F9920B; 
		color:white;    
	}   
</style>
}
@section ScriptSection
{   
<script type="text/javascript"> 
$(function ()
{   
	$(document).bind("click", function ()
	{             
		$(".contextMenuPopup").remove();  
	}); 
});    
cell_RightClick = function (evt) 
{     
	$(".contextMenuPopup").remove();
	var contextMenu = $('<div class="contextMenuPopup"></div>');
	$(contextMenu[0]).html('<div class="menuItem">Cell Type</div><div class="menuItem">Position</div><div class="menuItem">Value</div>'); 
	$(contextMenu[0]).css("left", evt.args.clientX + 10).css("top", evt.args.clientY + 10);
	$("#PivotGrid1").append(contextMenu[0]);      
	$(".menuItem").bind("mouseenter", function (e)
	{         
		var bgColor = ($(".summary").css("background-color") != "transparent" && $(".summary").css("background-color") != "rgb(31, 31, 31)") ? $(".summary").css("background-color") : $(".summary").css("color");
		if (bgColor == "rgb(204, 237, 255)" || bgColor == "rgb(94, 171, 222)" || bgColor == "rgb(104, 195, 222)") 
		$(this).addClass("activeMenuItemBlue")
		else if (bgColor == "rgb(247, 252, 182)" || bgColor == "rgb(145, 170, 41)" || bgColor == "rgb(169, 199, 78)")
		$(this).addClass("activeMenuItemGreen")    
		else if (bgColor == "rgb(255, 238, 169)" || bgColor == "rgb(250, 161, 19)" || bgColor == "rgb(255, 187, 96)")
		$(this).addClass("activeMenuItemOrange")   
	}); 
	$(".menuItem").bind("mouseleave", function (e)
	{
		$(this).removeClass("activeMenuItemBlue").removeClass("activeMenuItemGreen").removeClass("activeMenuItemOrange"); 
	}); 
	$(".menuItem").click(function (e) 
	{
		alert("Click event occurs");  
	}); 
	}
</script>
}
@section ControlsSection
{
	@Html.EJ().Pivot().PivotGrid("PivotGrid1")
	.Url("../wcf/CellContextService.svc").EnableCellContext(true)
	.ClientSideEvents(events=>events.CellContext("cell_RightClick "))
}


{% endhighlight %}



The output of the above code creates a PivotGrid with CellContext options as shown in the following screenshot.

![](Context-Menu_images/Context-Menu_img1.png)



