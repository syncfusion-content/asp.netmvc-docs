---
layout: post
title: Keyboard-Navigation
description: keyboard navigation	
platform: ejmvc
control: Accordion 
documentation: ug
---

## Keyboard Navigation	

You can use Keyboard shortcut keys as an alternative to the mouse on using Accordion control using AllowKeyboardNavigation property. However you will have to focus the control to enable the keyboard navigation. Accordion Control allows you to perform all kind of actions using keyboard shortcuts.

<table>
<tr>
<td>
Shortcut Key</td><td>
Description</td></tr>
<tr>
<td>
{ [Access key](http://en.wikipedia.org/wiki/Access_key) | markdownify } + j	</td><td>
Focuses into the accordion control</td></tr>
<tr>
<td>
Up</td><td>
Moves to previous panel</td></tr>
<tr>
<td>
Down</td><td>
Moves to next panel</td></tr>
<tr>
<td>
Left</td><td>
Moves to previous panel</td></tr>
<tr>
<td>
Right</td><td>
Moves to next panel</td></tr>
<tr>
<td>
Home</td><td>
Moves to the first accordion panel</td></tr>
<tr>
<td>
End</td><td>
Moves to the last accordion panel</td></tr>
</table>
Configure keyboard interaction

The following code explains you on how to enable keyboard interaction for an Accordion widget.

<table>
<tr>
<td>
[CSHTML]// In the View page, configure Accordion with corresponding data and configure Keyboard navigation for Accordion by setting AllowKeyboardNavigation property to true.&lt;div style="width: 400px; float:left;"&gt;@{Html.EJ().Accordion("accordion").Items(data =>        {            data.Add().Text("Essential Chart").ContentTemplate(@&lt;div&gt;                Essential Chart for ASP.NET MVC is a visually stunning, high-performance charting component that is easy to use. It includes 35 chart types ranging from simple column charts to specialized financial charts. The charts are highly customizable and have a powerful data model that makes data binding simple.            &lt;/div&gt;);            data.Add().Text("Essential Schedule").ContentTemplate(@&lt;div&gt;                Essential Schedule for ASP.NET MVC is an Outlook Calendar-like scheduler control that lets you add rich scheduling capabilities to your web applications. It includes an advanced set of features including data binding, multiple resource views, rich interactivity, support for AJAX, client-side events, and much more.            &lt;/div&gt;);            data.Add().Text("Essential Grid").ContentTemplate(@&lt;div&gt;                Essential Grid for ASP.NET MVC is a feature-rich control that provides extensive appearance customization options with support for grouped records. With Essential Grid for ASP.NET MVC, you can create a grid with a highly customizable look and feel. This grid is very useful for generating complex grid-based reports with rich formatting. It supports paging, sorting, grouping, filtering, and editing features. It also supports a JSON mode in which you can handle all the operations like paging and sorting. The performance of these operations in the JSON mode will be much faster than if the grid were to handle them. Essential Grid generates clean HTML in compliance with XHTML 1.0. It supports any kind of IEnumerable data source. It uses LINQ data retrieval techniques for handling data sources, and offers high performance.&lt;/div&gt;);        }).AllowKeyboardNavigation(true).Render();}&lt;/div&gt;</td></tr>
<tr>
<td>
[JavaScript]// Define script to focus into the Accordion control on Alt + J shortcut keys.&lt;script&gt;    $(function () {        $(document).on("keydown", function (e) {            if (e.altKey && e.keyCode === 74) { // j- key code.                $("#accordion").focus();            }        });    });&lt;/script&gt;</td></tr>
</table>




Output for Accordion widget focused and navigated to last item using Keyboard navigation is as follows.



{ ![](Keyboard-Navigation_images/Keyboard-Navigation_img1.png) | markdownify }
{:.image }


