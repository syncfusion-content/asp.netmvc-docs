---
layout: post
title: Getting Started | ListBox | ASP.NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: ListBox
documentation: ug
---

# Getting Started

This section explains briefly on how to create a ListBox control in your ASP.NET MVC application.

## Create your first ListBox in MVC

Here you can learn how to customize ListBox in Contact Selection tool. This allows you display the list of contacts, to select and move them to the next ListBox that has the selected items. The following example illustrates simulator of Group Creation tool like Skype messenger.

The following screenshot demonstrates the functionality of ListBox with Multi-Selection and Drag and Drop features.



![](Getting-Started_images/Getting-Started_img1.png)

Skype Group creation tool Simulator using ListBox
{:.caption}

In the above screenshot, you can select a list item from the first ListBox widget. After you select the item, you can move the selected item to the second ListBox widget. 

### Create a ListBox Widget

EssentialASP.NET MVCListBox control renders with built-in features.

The following steps are used to create ListBox control.  

1. You can create an MVC Project and add necessary assembly with the help of the given [MVC-Getting Started](http://help.syncfusion.com/aspnetmvc/listbox/getting-started) Documentation.
2. Please add the below code in your layout._cshtml page to add necessary script and CSS files to render the ListBox control.

   ~~~ cshtml

	<head>

	<link href="http://cdn.syncfusion.com/13.1.0.21/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />



		<!--Scripts-->

		<script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js"></script>



		<script src="http://cdn.syncfusion.com/js/assets/external/jquery.globalize.min.js"></script>



		<script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js"></script>



		<script src="http://cdn.syncfusion.com/13.1.0.21/js/web/ej.web.all.min.js"> </script>

	</head>
		
   ~~~
   

     Create a CSHTML file in View page and add the following code sample to it. 

3. Add the following code in your view page to render ListBox controls.



   ~~~ cshtml  

	<div id="sample">

		<h5>

			<b>Add people</b></h5>

		<p>

			Choose a contact and click move button to add in group

		</p>

		<br />

		<div id="control">

			<div id="container1">

				<p>

					Contacts List</p>

				@Html.EJ().ListBox("list1")

			</div>

			<div id="container2">

				<p>

					People in this group</p>

				@Html.EJ().ListBox("list2")

			</div>

		</div>

	</div>


   ~~~
   


4. Add the following style section for the ListBox controls alignment. 

   ~~~ css

	<style type="text/css" class="cssStyles">

		#control 
		{

			height: 350px;

			width: 500px;

			padding: 25px;

			background-color: #f7f7f7;

			display: flex;

		}

		#sample 
		{

			height: 472px;

			width: 600px;

		}

		#list2_container 
		{

			float: right;

		}

		#list1_container 
		{

			float: left;

		}

		.middle-buttons 
		{

			padding: 91px 25px 25px 25px;

		}

		#container1, #container2 
		{

			width: 200px;

		}

		img 
		{

			padding-right: 10px;

			padding-top: 3px;

			width: 18px;

			height: 15px;

		}

		#form1 
		{

			padding: 25px;

		}



	</style>

   ~~~
   

5. Run this code to render an empty ListBox control.



![](Getting-Started_images/Getting-Started_img2.png)

Render ListBox with <ul></ul> element
{:.caption}

### Configure ListBox with Items

To populate items inside ListBox, you have to add list items inside <ul> as <li></li> elements. The TargetID property is used to get the list items from the target. The Id of the ul that has the list items is given as the TargetID. Include the following <ul>, <li> elements in your sample.



{% highlight html %}   

<div id="sample">

    <h5>

        <b>Add people</b></h5>

    <p>

        Choose a contact and click move button to add in group

    </p>

    <br />

    <div id="control">

        <div id="container1">

            <p>

                Contacts List</p>

            @Html.EJ().ListBox("list1").TargetID("select")

            <ul id="select">

                <li>

                    <img src="~/images/listbox/busy.png" alt="Categorize" />

                    Nancy</li>

                <li>

                    <img src="~/images/listbox/busy.png" alt="Done" />

                    Andrew</li>

                <li>

                    <img src="~/images/listbox/avail.png" alt="Flag" />

                    Janet</li>

                <li>

                    <img src="~/images/listbox/away.png" alt="Forward" />

                    Margaret</li>

                <li>

                    <img src="~/images/listbox/away.png" alt="Move" />

                    Michael</li>

                <li>

                    <img src="~/images/listbox/avail.png" alt="E-mail" />

                    Robert</li>

                <li>

                    <img src="~/images/listbox/avail.png" alt="Meeting" />

                    Laura</li>

                <li>

                    <img src="~/images/listbox/avail.png" alt="Reply" />

                    Anne</li>

                <li>

                    <img src="~/images/listbox/away.png" alt="Move" />

                    Suyama</li>

                <li>

                    <img src="~/images/listbox/avail.png" alt="E-mail" />

                    Callahan</li>

                <li>

                    <img src="~/images/listbox/avail.png" alt="Meeting" />

                    Peacock</li>

                <li>

                    <img src="~/images/listbox/avail.png" alt="Reply" />

                    Fuller</li>

                <li>

                    <img src="~/images/listbox/avail.png" alt="Reply" />

                    Davolio</li>

                <li>

                    <img src="~/images/listbox/avail.png" alt="Reply" />

                    Dodsworth</li>

                <li>

                    <img src="~/images/listbox/avail.png" alt="Reply" />

                    Louis</li>

            </ul>

        </div>

        <div class="middle-buttons">

            @Html.EJ().Button("Add").Text(">>").ShowRoundedCorner(true).ClientSideEvents(e => e.Click("add"))

            <br />

            <br />

            @Html.EJ().Button("Remove").Text("<<").ShowRoundedCorner(true).ClientSideEvents(e => e.Click("remove"))

        </div>

        <div id="container2">

            <p>

                People in this group</p>

            @Html.EJ().ListBox("list2")

            <ul id="selectedItems">

            </ul>

        </div>

    </div>

</div>

{% endhighlight %}



Run the above code to render ListBox with list items rendered inside ListBox. ListBox with Contact list items is shown as follows.



![](Getting-Started_images/Getting-Started_img3.png)

ListBox with Contact list items
{:.caption}

### Enable Drag and Drop 

You can drag an item from a ListBox and drop it in droppable element.To drag and drop a list item across controls or within a control, you have to set the AllowDrag and AllowDrop property as “True”. 

Please refer the below code snippet:

{% highlight CSHTML %}
  
@Html.EJ().ListBox("list1").TargetID("select").AllowDrag(true).AllowDrop(true)

@Html.EJ().ListBox("list2").AllowDrag(true).AllowDrop(true)

{% endhighlight %}

Run the above code example to render the following ListBox with Drag and drop feature. ListBox with Drag and Drop list items across control is as follows:



![](Getting-Started_images/Getting-Started_img4.png)

ListBox with Drag and Drop list items
{:.caption}

Enable Multiple Selection 

You can select multiple list items simultaneously in ListBox control, and move the multiple, selected items to the selection ListBox. To select multiple items in a ListBox, set the AllowMultiSelection property for the ListBox as “True”.



{% highlight CSHTML %}
   

@Html.EJ().ListBox("list1").TargetID("select").AllowMultiSelection(true)

.AllowDragAndDrop(true)

{% endhighlight %}

Run the above code example to render the following ListBox with Multiple selection feature. ListBox control with Multiple Selection of list items is as follows.



![](Getting-Started_images/Getting-Started_img5.png)

ListBox  with Multiple Selection of list items
{:.caption}

### Add items to a Second ListBox

You have to move the selected list items to the second ListBox using AddItem(value) method and remove existing item in the first ListBox using RemoveItem() method.

The following code sample explains how to add an item to a second ListBox.



{% highlight js %}

<script type="text/javascript">

	function add(e) 
	{

		var firstListBox = $('#list1').data("ejListBox");

		var selectedItems = firstListBox.getSelectedItems();

		var len = selectedItems.length;

		for (i = 0; i < len; i++) 
		{

			var value = $(selectedItems[i]).html();

			selectedItems[i].remove();

			var target = $('#list2').data("ejListBox");

			target.addItem(value);

		}

	}

    function remove(e) 
	{

        var firstListBox = $('#list2').data("ejListBox");

        var selectedItem = firstListBox.getSelectedItems();

        var length = selectedItem.length;

        for (i = 0; i < length; i++) 
		{

            var value = $(selectedItem[i]).html();

            selectedItem[i].remove();

            var target = $('#list1').data("ejListBox");

            target.addItem(value);

        }

    }

</script>

{% endhighlight %}

Run this code and you can see the output. Selected items from the first ListBox have been moved to second ListBox using AddItem() and RemoveItem() method and it is displayed in the following figure.



![](Getting-Started_images/Getting-Started_img6.png)

ListBox Selection moved to Second ListBox
{:.caption}
