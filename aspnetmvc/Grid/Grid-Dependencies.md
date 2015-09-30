---
layout: post
title: Grid-Dependencies
description: grid dependencies
platform: ejmvc
control: Grid
documentation: ug
---

# Grid Dependencies

ej.web.all.js is a bundle of all EssentialJavaScript controls. When you use ej.web.all.js in your application, you can leave this section or else you can try to render the grid in your application by using ej.grid.min.js file. You can refer to the following frameworks and controls in your project.

_Table1: Grid Dependency_ 

<table>
<tr>
<th>
File                          </th><th>
Description/Usage</th></tr>
<tr>
<td>
ej.core.min.js</td><td>
Must be referred always before using all the JS controls.</td></tr>
<tr>
<td>
ej.data.min.js</td><td>
Used to handle datamanger operation and should be used while binding data to JS controls.</td></tr>
<tr>
<td>
ej.grid.min.js</td><td>
Should be referred when the grid control is used.</td></tr>
<tr>
<td>
ej.pager.min.js</td><td>
Should be referred when the paging is used in the grid.  </td></tr>
<tr>
<td>
ej.scroller.min.js</td><td>
Should be referred when the scrolling is used in the grid.  </td></tr>
<tr>
<td>
ej.waitingpopup.min.js</td><td>
Should be referred when the remote databinding is used in the grid. The waiting popup is shown while requesting the server for data.</td></tr>
<tr>
<td>
ej.gridresize.min.js</td><td>
Need to refer when the resizing feature is used in the grid.</td></tr>
<tr>
<td>
ej.dropdownlist.min.js</td><td rowspan = "8">
  These files are used while enabling the Editing and Filtering features in the grid.</td></tr>
<tr>
<td>
ej.dialog.min.js</td></tr>
<tr>
<td>
ej.button.min.js</td></tr>
<tr>
<td>
ej.autocomplete.min.js</td></tr>
<tr>
<td>
ej.datepicker.min.js</td></tr>
<tr>
<td>
ej.datetimepicker.min.js</td></tr>
<tr>
<td>
ej.checkbox.min.js</td></tr>
<tr>
<td>
ej.editor.min.js</td></tr>
</table>

N>_ ej.unobtrusive.min.js should be referred when the [`UnobtrusiveJavaScriptEnabled`](/js/unobtrusive-support "UnobtrusiveJavaScriptEnabled")  is set to true in web.config file.


