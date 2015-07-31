---
layout: post
title: Keyboard-Interaction
description: keyboard interaction
platform: ejmvc
control: AutoComplete
documentation: ug
---

## Keyboard Interaction

You can use keyboard shortcut keys as an alternative to the mouse while using the AutoComplete widget. The AutoComplete widget allows you to perform all kinds of actions using keyboard shortcuts.

_Keyboard shortcut keys_

<table>
<tr>
<td>
Shortcut Key</td><td>
Description</td></tr>
<tr>
<td>
{{ '[Access key](http://en.wikipedia.org/wiki/Access_key)' | markdownify }} + j	</td><td>
Focuses into the AutoComplete text box</td></tr>
<tr>
<td>
Up</td><td>
Moves to previous item in pop up</td></tr>
<tr>
<td>
Down</td><td>
Moves to next item in pop up</td></tr>
<tr>
<td>
Enter</td><td>
Selects the focused item</td></tr>
<tr>
<td>
Esc</td><td>
Closes the popup</td></tr>
</table>


Configure Keyboard Interaction

The following steps explain how you can enable keyboard interaction for an AutoComplete textbox.



1. In the View page, define the AutoComplete control.



[CSHTML]



@*Refer to the DataSource defined in Local Databinding Step 1 *@

@{IDictionary<string, object> htmlAttribute = new Dictionary<string, object>();

htmlAttribute.Add("accesskey", "j");

}



@(Html.EJ().Autocomplete("autocomplete").HtmlAttributes(htmlAttribute)

    .Datasource((IEnumerable<CarsList>

    )ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text").Category("Category"))

    .Width("200px"))    



2. Run the sample, press AccessKey + J to focus in the AutoComplete widget and you can navigate using the arrow keys. Use the Escape key to close the popup.



{{ '![](Keyboard-Interaction_images/Keyboard-Interaction_img1.png)' | markdownify }}
{:.image }


_AutoComplete focused with keyboard shortcut_

