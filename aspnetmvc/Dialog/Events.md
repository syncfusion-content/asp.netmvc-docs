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

_Table_ _2__: Events of Dialog_

<table>
<tr>
<td>
Event</td><td>
Description</td></tr>
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



{% highlight html %}

@{Html.EJ().Dialog("dialog").Title("WinRT").ContentTemplate(@<div>The Syncfusion Dialog control is rendered.</div>).Width(300).Height("200").ClientSideEvents(evt => evt.Create("onCreate").BeforeClose("onBeforeClose")

    .Close("onDialogClose").BeforeOpen("onBeforeOpen").Open("onOpen").Drag("onDrag").DragStart("onDragStart").DragStop("onDragStop").Resize("onResize")

    .ResizeStart("onResizeStart").ResizeStop("onResizeStop")).Render();}
	
{% endhighlight %}










2. Define the script for handling Dialog events.

{% highlight JS %}

[JavaScript]



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

{% endhighlight  %}

3. Output of Dialog widget when the events trigger is as follows.

<table>
<tr>
<td>
<br>
{{ ' ![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/diaevt.PNG](Events_images/Events_img1.png)' | markdownfy }}

</td><td>
{{ ' ![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/diab4open.PNG](Events_images/Events_img2.png)' | markdownfy }}


</td></tr>
</table>
_Figure 25: Dialog triggered Create and BeforeOpen event_               



<table>
<tr>
<td>
{{ '![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/dialog isopen.PNG](Events_images/Events_img3.png)' | markdownfy }}


</td><td>
</td><td>
{{ ' ![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/dialog isbeforeclose.PNG](Events_images/Events_img4.png)' | markdownfy }}


</td></tr>
</table>
_Figure 26: Dialog triggered Open and BeforeClose event_  


<table>
<tr>
<td>
{{ '![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/diaafterclose.PNG](Events_images/Events_img5.png)' | markdownfy }}


</td><td>
{{ '![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/dialogevtdrag.PNG](Events_images/Events_img6.png)' | markdownfy }}


</td></tr>
</table>
_Figure 27: Dialog triggered Close and Drag event_


<table>
<tr>
<td>
{{ ' ![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/dialogdragstart.PNG](Events_images/Events_img7.png)' | markdownfy }}


</td><td>
{{ ' ![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/dialogdragstop.PNG](Events_images/Events_img8.png)' | markdownfy }}


</td></tr>
</table>
_Figure 28: Dialog triggered DragStart and DragStop event_


<table>
<tr>
<td>
<td>
{{ ' ![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/dialogresize.PNG](Events_images/Events_img9.png)' | markdownfy }}
</td><td>
<td>
{{ ' ![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/dialogresizestart.PNG](Events_images/Events_img10.png)' | markdownfy }}

</td></tr>
</table>
_Figure 29: Dialog triggered Resize and ResizeStart event_


'![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/dialogresizestop.PNG](Events_images/Events_img11.png)



_Figure 30: Dialog triggered ResizeStop event_

