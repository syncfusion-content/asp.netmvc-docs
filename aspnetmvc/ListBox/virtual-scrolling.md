---
layout: post
title: VirtualScrolling support | ListBox | ASP.NET MVC | Syncfusion
description: VirtualScrolling support 
platform: ejmvc
control: ListBox
documentation: ug
---

# VirtualScrolling support 

ListBox widget provides the VirtualScrolling support, when binding the remote data for the ListBox. It loads partially, only a set of data from remote server loaded initially, and imports data further upon loading. To enable VirtualScrolling support, set the EnableVirtualScrolling property as true. You can set ItemsCount that specifies number of items in the ListBox. You can load any number of items upon request with ItemRequest ClientSide Event.

The following steps explains you the behavior of VirtualScrolling support in ListBox.

1. Add the below code in your page to render the ListBox


   ~~~ cshtml
   
	  // Add the following code in View page to configure ListBox widget
	  <div class="control">  
			<h5 class="ctrllabel">
				Select Customer ID
			</h5>  
			@Html.EJ().ListBox("customerList").Datasource(listBoxDatasource =>
			listBoxDatasource.URL("http://mvc.syncfusion.com/Services/Northwnd.svc/")).Query("ej.Query().from('Customers')").ListBoxFields(f => 
			f.Text("CustomerID")).ItemsCount(91) .AllowVirtualScrolling(true).ClientSideEvents(e => 
			e.ActionBegin("itemRequested"))
		</div>
	
   ~~~
   
   
   ~~~ js
	<script type="text/javascript"> 
		function itemRequested(args) {
		var target = $("#customerList").data("ejListBox");
		//to load 20 items
		target.model.query = ej.Query().from('Customers').range(args.start, args.start + 20);
		this.model.itemsCount = 20; 
		}
	</script>
   ~~~
   



2. Output of the above steps.


   ![](Load-on-Demand-support_images/Load-on-Demand-support_img1.png)



