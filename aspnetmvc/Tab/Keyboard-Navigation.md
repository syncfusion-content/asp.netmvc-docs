---
layout: post
title: Keyboard-Navigation
description: keyboard navigation
platform: ejmvc
control: Tab Control
documentation: ug
---

# Keyboard Navigation

Tab control provides supports keyboard interaction. Using this functionality you can interact with control using keyboard. This is achieved by enabling ‘AllowKeyboardNavigation’to ‘true’. By default this property value is set to ‘true’.

Following table illustrates the accessible key and their usage

<table>
<tr>
<th>
Keys</th><th>
Behavior</th></tr>
<tr>
<td>
Up</td><td>
Selected previous item.</td></tr>
<tr>
<td>
Right</td><td>
Selected previous item.</td></tr>
<tr>
<td>
Down</td><td>
Selected next item.</td></tr>
<tr>
<td>
Left</td><td>
Selected next item.</td></tr>
<tr>
<td>
Home</td><td>
Selected first item.</td></tr>
<tr>
<td>
End</td><td>
Selected last item.</td></tr>
</table>
The following code example is used to render the Tab element in RTL format. 

1. Add the following code in your view page to render Tab with keyboard navigation.



<table>
<tr>
<td>
[CSHTML]// Add the following code example to the corresponding CSHTML page to render Tab with keyboard navigation.<div style="width:550px">    @{Html.EJ().Tab("dishtab").Items(data =>           {               data.Add().ID("pizzatype").Text("Pizza Type")                   .ContentTemplate(@<div>                       Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.                   </div>);               data.Add().ID("sandwichtype").Text("Sandwich Type")                   .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.               </div>);           }).AllowKeyboardNavigation(true).Render();}</div></td></tr>
<tr>
<td>
[JS]// Add the following script to render Tab with keyboard navigation.<script type="text/javascript">        $(function () {        //Control focus key        $(document).on("keydown", function (e) {            if (e.altKey && e.keyCode === 74) {                // j- key code.                $("#dishtab ul a").focus();            }        });        });    </script></td></tr>
</table>




2. The following screenshot illustrates the Tab with keyboard navigation.

![](Keyboard-Navigation_images/Keyboard-Navigation_img1.png)



