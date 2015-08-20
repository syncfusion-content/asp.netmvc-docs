---
layout: post
title: Events
description: events
platform: ejmvc
control: Dialog
documentation: ug
---

# Events

 The Dialog widget provides the following events,

_Table2: Events of Dialog_

<table>
<tr>
<th>
Event</th><th>
Description</th></tr>
<tr>
<td>
BeforeClose</td><td>
Triggered when the control before close</td></tr>
<tr>
<td>
Close</td><td>
Triggered when the control is close</td></tr>
<tr>
<td>
BeforeOpen</td><td>
Triggered when the control before open</td></tr>
<tr>
<td>
Open</td><td>
Triggered when the control is open</td></tr>
<tr>
<td>
Drag</td><td>
Triggered when the control is drag</td></tr>
<tr>
<td>
DragStart</td><td>
Triggered when the control drag start </td></tr>
<tr>
<td>
DragStop</td><td>
Triggered when the control drag stop</td></tr>
<tr>
<td>
Resize</td><td>
Triggered when the control is resize</td></tr>
<tr>
<td>
ResizeStart</td><td>
Triggered when the control resize start</td></tr>
<tr>
<td>
ResizeStop</td><td>
Triggered when the control resize stop</td></tr>
</table>


## Configure Events

The following steps describes you on how the events are added to the Dialog control.

1. In the VIEW page set a helper element with dialog content for rendering the Dialog control.

   ~~~ js

		@{Html.EJ().Dialog("dialog").Title("WinRT").ContentTemplate(@<div>The Syncfusion Dialog control is rendered.</div>).Width(300).Height("200").ClientSideEvents(evt => evt.Create("onCreate").BeforeClose("onBeforeClose")

			.Close("onDialogClose").BeforeOpen("onBeforeOpen").Open("onOpen").Drag("onDrag").DragStart("onDragStart").DragStop("onDragStop").Resize("onResize")

			.ResizeStart("onResizeStart").ResizeStop("onResizeStop")).Render();}
			
   ~~~
   {:.prettyprint }

2. Define the script for handling Dialog events.

   ~~~ js

			<script type="text/javascript">

				function onCreate(args) {

					// {boolean} argument.cancel - returns the cancel option value

					// {object} argument.model - returns the dialog model

					// {string} argument.type - returns the name of the event

		alert("Event triggered is " + args.type);

				}



				function onBeforeClose(args) {

					// {Object} argument.event - returns the close icon click event args    

		// {boolean} argument.cancel - returns the cancel option value

		// {object} argument.model - returns the dialog model

					// {string} argument.type - returns the name of the event

					alert("Event triggered is " + args.type);

				}



				function onDialogClose (args) {

					// {Object} argument.event - returns the close icon click event args    

		// {boolean} argument.cancel - returns the cancel option value

		// {object} argument.model - returns the dialog model

					// {string} argument.type - returns the name of the event

					alert("Event triggered is " + args.type);

				}



				function onBeforeOpen(args) {

					// {boolean} argument.cancel - returns the cancel option value

		// {object} argument.model - returns the dialog model

					// {string} argument.type - returns the name of the event

					alert("Event triggered is " + args.type);

				}



				function onOpen(args) {

					// {boolean} argument.cancel - returns the cancel option value

		// {object} argument.model - returns the dialog model

					// {string} argument.type - returns the name of the event

					alert("Event triggered is " + args.type);

				}



				function onDrag(args) {

					// {boolean} argument.cancel - returns the cancel option value

		// {object} argument.model - returns the dialog model

		// {string} argument.type - returns the name of the event

					// {Object} argument.event - returns the mouse move event args

					alert("Event triggered is " + args.type);

				}



				function onDragStart(args) {

					// {boolean} argument.cancel - returns the cancel option value

		// {object} argument.model - returns the dialog model

		// {string} argument.type - returns the name of the event

					// {Object} argument.event - returns the mouse down event args

					alert("Event triggered is " + args.type);

				}



				function onDragStop(args) {

					 // {boolean} argument.cancel - returns the cancel option value

		// {object} argument.model - returns the dialog model

		// {string} argument.type - returns the name of the event

					// {Object} argument.event - returns the mouse down event args

					alert("Event triggered is " + args.type);

				}



				function onResize(args) {

					 // {boolean} argument.cancel - returns the cancel option value

		// {object} argument.model - returns the dialog model

		// {string} argument.type - returns the name of the event

					// {Object} argument.event - returns the mouse move event args

					alert("Event triggered is " + args.type);

				}



				function onResizeStart(args) {

					// {boolean} argument.cancel - returns the cancel option value

		// {object} argument.model - returns the dialog model

		// {string} argument.type - returns the name of the event

					// {Object} argument.event - returns the mouse down event args

					alert("Event triggered is " + args.type);

				}



				function onResizeStop(args) {

					// {boolean} argument.cancel - returns the cancel option value

		// {object} argument.model - returns the dialog model

		// {string} argument.type - returns the name of the event

					// {Object} argument.event - returns the mouse leave event args

					alert("Event triggered is " + args.type);

				}

			 </script>

   ~~~
   {:.prettyprint }


3. Output of Dialog widget when the events trigger is as follows.

<table>
<tr>
<td>
<br>
{{'![](Events_images/Events_img1.png)'| markdownify}}

</td><td>
{{ ' ![](Events_images/Events_img2.png)'| markdownify }}


</td></tr>
</table>

_Figure 25: Dialog triggered Create and BeforeOpen event_               



<table>
<tr>
<td>
{{ '![](Events_images/Events_img3.png)' | markdownify }}


</td><td>
</td><td>
{{ ' ![](Events_images/Events_img4.png)' | markdownify }}


</td></tr>
</table>
_Figure 26: Dialog triggered Open and BeforeClose event_  


<table>
<tr>
<td>
{{'![](Events_images/Events_img5.png)'|markdownify }}


</td><td>
{{'![](Events_images/Events_img6.png)'|markdownify }}


</td></tr>
</table>

_Figure 27: Dialog triggered Close and Drag event_


<table>
<tr>
<td>
{{'![](Events_images/Events_img7.png)'|markdownify }}


</td><td>
{{'![](Events_images/Events_img8.png)'| markdownify }}


</td></tr>
</table>

_Figure 28: Dialog triggered DragStart and DragStop event_


<table>
<tr>
<td>
{{'![](Events_images/Events_img9.png)'| markdownify }}
</td><td>
{{'![](Events_images/Events_img10.png)'| markdownify }}

</td></tr>
</table>

_Figure 29: Dialog triggered Resize and ResizeStart event_


![](Events_images/Events_img11.png)


_Figure 30: Dialog triggered ResizeStop event_

