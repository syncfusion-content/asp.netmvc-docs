---
layout: post
title: Miscellaneous
description: miscellaneous
platform: ejmvc
control: ColorPicker
documentation: ug
---

## Miscellaneous

getValue

The getValue() method in ColorPicker returns the hexadecimal value.

1. In the CSHTML page, configure the ColorPicker widget as follows.



<table>
<tr>
<td>
[CSHTML]@*In the CSHTML page, add the Html helpers to render ColorPicker widget*@ @Html.EJ().ColorPicker("colorPicker").Value("#278787")</td></tr>
<tr>
<td>
[JAVASCRIPT] &lt;script&gt;   var ColorObj;   jQuery(function ($) {      ColorObj = $("#colorPicker").ejColorPicker({ value: "#278787" }).data('ejColorPicker');      ColorObj.getValue();    }); &lt;/script&gt;</td></tr>
</table>
setValue

The setValue() method in ColorPicker is used to set the color value. The given value is in hexadecimal form.

1. In the CSHTML page, configure the ColorPicker widget as follows.



<table>
<tr>
<td>
[CSHTML]@*In the CSHTML page, add the Html helpers to render ColorPicker widget*@ @Html.EJ().ColorPicker("colorPicker")</td></tr>
<tr>
<td>
[JAVASCRIPT] &lt;script&gt;   var ColorObj;   jQuery(function ($) {      ColorObj = $("#colorPicker").ejColorPicker().data('ejColorPicker');      ColorObj.setValue("#278787");    }); &lt;/script&gt;</td></tr>
</table>
getColor

The getColor() method in ColorPicker control returns the color value in r,g,b,a form.

1. In the CSHTML page, configure the ColorPicker widget as follows.



<table>
<tr>
<td>
[CSHTML]@*In the CSHTML page, add the Html helpers to render ColorPicker widget*@ @Html.EJ().ColorPicker("colorPicker").Value("#278787")</td></tr>
<tr>
<td>
[JAVASCRIPT] &lt;script&gt;   var ColorObj;   jQuery(function ($) {      ColorObj = $("#colorPicker").ejColorPicker({value: "#278787" }).data('ejColorPicker');      ColorObj.getColor();    }); &lt;/script&gt;</td></tr>
</table>


