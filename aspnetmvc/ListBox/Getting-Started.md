---
layout: post
title: Getting-Started
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



{ ![F:/UG/screen shot/1.PNG](Getting-Started_images/Getting-Started_img1.png) | markdownify }
{:.image }


_Figure 1: Skype Group creation tool Simulator using ListBox_

In the above screenshot, you can select a list item from the first ListBox widget. After you select the item, you can move the selected item to the second ListBox widget. 

Create a ListBox Widget

EssentialASP.NET MVCListBox control renders with built-in features.

The following steps are used to create ListBox control.  

1. You can create an MVC Project and add necessary Dll with the help of the given [MVC-Getting Started](http://help.syncfusion.com/ug/js/documents/gettingstartedwithmv.htm) Documentation.
2. Please add the below code in your layout._cshtml page to add necessary script and css files to render the ListBox control.

[Layout._cshtml]

&lt;head&gt;

&lt;link href="http://cdn.syncfusion.com/13.1.0.21/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" /&gt;



    &lt;!--Scripts--&gt;

    &lt;script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js"&gt;&lt;/script&gt;



    &lt;script src="http://cdn.syncfusion.com/js/assets/external/jquery.globalize.min.js"&gt;&lt;/script&gt;



    &lt;script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js"&gt;&lt;/script&gt;



    &lt;script src="http://cdn.syncfusion.com/13.1.0.21/js/web/ej.web.all.min.js"&gt; &lt;/script&gt;

&lt;/head&gt;

     Create a CSHTML file in View page and add the following code sample to it. 

3. Add the following code in your view page to render ListBox controls.



[view]    

&lt;div id="sample"&gt;

    &lt;h5&gt;

        <b>Add people</b>&lt;/h5&gt;

    &lt;p&gt;

        Choose a contact and click move button to add in group

    &lt;/p&gt;

    &lt;br /&gt;

    &lt;div id="control"&gt;

        &lt;div id="container1"&gt;

            &lt;p&gt;

                Contacts List</p>

            @Html.EJ().ListBox("list1")

        &lt;/div&gt;

        &lt;div id="container2"&gt;

            &lt;p&gt;

                People in this group</p>

            @Html.EJ().ListBox("list2")

        &lt;/div&gt;

    &lt;/div&gt;

&lt;/div&gt;





4. Add the following style section for the ListBox controls alignment. 



[Css]

&lt;style type="text/css" class="cssStyles"&gt;

    #control {

        height: 350px;

        width: 500px;

        padding: 25px;

        background-color: #f7f7f7;

        display: flex;

    }

    #sample {

        height: 472px;

        width: 600px;

    }

    #list2_container {

        float: right;

    }

    #list1_container {

        float: left;

    }

    .middlebuttons {

        padding: 91px 25px 25px 25px;

    }

    #container1, #container2 {

        width: 200px;

    }

    img {

        padding-right: 10px;

        padding-top: 3px;

        width: 18px;

        height: 15px;

    }

    #form1 {

        padding: 25px;

    }



&lt;/style&gt;



5. Run this code to render an empty ListBox control.



{ ![](Getting-Started_images/Getting-Started_img2.png) | markdownify }
{:.image }


_Figure 2: Render ListBox with &lt;ul&gt;&lt;/ul&gt; element_

Configure ListBox with Items

To populate items inside ListBox, you have to add list items inside &lt;ul&gt; as &lt;li&gt;&lt;/li&gt; elements. The TargetID property is used to get the list items from the target. The Id of the ul that has the list items is given as the TargetID. Include the following &lt;ul&gt;, &lt;li&gt; elements in your sample.



[view]    

&lt;div id="sample"&gt;

    &lt;h5&gt;

        <b>Add people</b>&lt;/h5&gt;

    &lt;p&gt;

        Choose a contact and click move button to add in group

    &lt;/p&gt;

    &lt;br /&gt;

    &lt;div id="control"&gt;

        &lt;div id="container1"&gt;

            &lt;p&gt;

                Contacts List</p>

            @Html.EJ().ListBox("list1").TargetID("select")

            &lt;ul id="select"&gt;

                &lt;li&gt;

                    &lt;img src="~/images/listbox/busy.png" alt="Categorize" /&gt;

                    Nancy</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/busy.png" alt="Done" /&gt;

                    Andrew</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/avail.png" alt="Flag" /&gt;

                    Janet</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/away.png" alt="Forward" /&gt;

                    Margaret</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/away.png" alt="Move" /&gt;

                    Michael</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/avail.png" alt="E-mail" /&gt;

                    Robert</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/avail.png" alt="Meeting" /&gt;

                    Laura</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/avail.png" alt="Reply" /&gt;

                    Anne</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/away.png" alt="Move" /&gt;

                    Suyama</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/avail.png" alt="E-mail" /&gt;

                    Callahan</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/avail.png" alt="Meeting" /&gt;

                    Peacock</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/avail.png" alt="Reply" /&gt;

                    Fuller</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/avail.png" alt="Reply" /&gt;

                    Davolio</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/avail.png" alt="Reply" /&gt;

                    Dodsworth</li>

                &lt;li&gt;

                    &lt;img src="~/images/listbox/avail.png" alt="Reply" /&gt;

                    Louis</li>

            &lt;/ul&gt;

        &lt;/div&gt;

        &lt;div class="middlebuttons"&gt;

            @Html.EJ().Button("Add").Text(">>").ShowRoundedCorner(true).ClientSideEvents(e => e.Click("add"))

            &lt;br /&gt;

            &lt;br /&gt;

            @Html.EJ().Button("Remove").Text("&lt;&lt;").ShowRoundedCorner(true).ClientSideEvents(e =&gt; e.Click("remove"))

        &lt;/div&gt;

        &lt;div id="container2"&gt;

            &lt;p&gt;

                People in this group</p>

            @Html.EJ().ListBox("list2")

            &lt;ul id="selecteditems"&gt;

            &lt;/ul&gt;

        &lt;/div&gt;

    &lt;/div&gt;

&lt;/div&gt;





Run the above code to render ListBox with list items rendered inside ListBox. ListBox with Contact list items is shown as follows.



{ ![F:/UG/screen shot/3.PNG](Getting-Started_images/Getting-Started_img3.png) | markdownify }
{:.image }


_Figure 3: ListBox with Contact list items_

Enable Drag and Drop 

You can drag an item from a ListBox and drop it in droppable element.To drag and drop a list item across controls or within a control, you have to set the AllowDragAndDrop property as “True”. 

Please refer the below code snippet:

[view]    

@Html.EJ().ListBox("list1").TargetID("select").AllowDragAndDrop(true)

@Html.EJ().ListBox("list2").AllowDragAndDrop(true)



Run the above code example to render the following ListBox with Drag and drop feature. ListBox with Drag and Drop list items across control is as follows:



{ ![F:/UG/screen shot/4.png](Getting-Started_images/Getting-Started_img4.png) | markdownify }
{:.image }


_Figure 4: ListBox with Drag and Drop list items_

Enable Multiple Selection 

You can select multiple list items simultaneously in ListBox control, and move the multiple, selected items to the selection ListBox. To select multiple items in a ListBox, set the AllowMultiSelection property for the ListBox as “True”.



[view]    

@Html.EJ().ListBox("list1").TargetID("select").AllowMultiSelection(true)

.AllowDragAndDrop(true)



Run the above code example to render the following ListBox with Multiple selection feature. ListBox control with Multiple Selection of list items is as follows.



{ ![F:/UG/screen shot/5.PNG](Getting-Started_images/Getting-Started_img5.png) | markdownify }
{:.image }


_Figure 5__: ListBox  with Multiple Selection of list items_

Add items to a Second ListBox

You have to move the selected list items to the second ListBox using AddItem(value) method and remove existing item in the first ListBox using RemoveItem() method.

The following code sample explains how to add an item to a second ListBox.



[JS]

&lt;script type="text/javascript"&gt;

function add(e) {

        var firstListBox = $('#list1').data("ejListBox");

        var selecteditems = firstListBox.getSelectedItems();

        var len = selecteditems.length;

        for (i = 0; i < len; i++) {

            var value = $(selecteditems[i]).html();

            selecteditems[i].remove();

            var target = $('#list2').data("ejListBox");

            target.addItem(value);

        }

    }

    function remove(e) {

        var firstListBox = $('#list2').data("ejListBox");

        var selecteditem = firstListBox.getSelectedItems();

        var len = selecteditem.length;

        for (i = 0; i < len; i++) {

            var value = $(selecteditem[i]).html();

            selecteditem[i].remove();

            var target = $('#list1').data("ejListBox");

            target.addItem(value);

        }

    }

&lt;/script&gt;



Run this code and you can see the output. Selected items from the first ListBox have been moved to second ListBox using AddItem() and RemoveItem() method and it is displayed in the following figure.



{ ![F:/UG/screen shot/1.PNG](Getting-Started_images/Getting-Started_img6.png) | markdownify }
{:.image }


_Figure 6: ListBox Selection moved to Second ListBox_

