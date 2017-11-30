---
layout: post
title: Dependencies of the ComboBox control for Syncfusion ASP.NET MVC
description: Dependencies of the ComboBox control for Syncfusion ASP.NET MVC 
platform: ASP.NET MVC
control: ComboBox
documentation: ug
---

##ComboBox Dependencies

The external script dependencies of the ComboBox control are as follows:

* [jQuery 1.7.1](http://jquery.com/) and later versions.

The internal script dependency ej.web.all.js is a bundle of all Syncfusion ASP.NET MVC controls. If you use ej.web.all.js in your application, you can leave this section, or else try to render ComboBox in your application using the ej.combobox.min.js file. Refer to the following frameworks and controls in your project.


<table>
	<tr>
		<th>File </th>
		<th>Description / Usage </th>
	</tr>
	<tr>
		<td>ej.core.min.js</td>
		<td>Must be referred always before using all the JS controls.</td>
	</tr>
	<tr>
		<td>ej.data.min.js</td>
		<td>Used to handle data operation and should be used while binding data to JS controls.</td>
	</tr>
	<tr>
		<td>ej.ComboBox.min.js</td>
		<td>The ComboBox’s main file</td>
	</tr>
	<tr>
		<td>ej.globalize.min.js</td>
		<td>Should be referred when localization used in ComboBox.</td>
	</tr>
</table>