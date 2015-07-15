---
layout: post
title: MultiSelection-modes
description: multiselection modes
platform: ejmvc
control: AutoComplete
documentation: ug
---

## MultiSelection modes

AutoComplete widget allows you to select multiple values from the suggestions list using the MultiSelectMode property. Multiple values are selected when MultiSelectMode value is set to VisualMode or Delimiter. 

Delimitermode separates multiple items using a separator character defined. When the delimiter mode is set, you can define the delimiter character using DelimiterChar. It takes a single character and it is a symbol. 

Visualmode selects multiple items by enclosing the item in a rounded rectangle with a close icon to remove item from the selection.

Configuring MultiSelection Mode

The following steps explain the configuration of the MultiSelectMode for an AutoComplete textbox.



1. In the View page, define the AutoComplete control and configure multiple selection mode.



[CSHTML]



@*Refer to the DataSource defined in Local Databinding Step 1 *@

&lt;div style="width: 600px"&gt;

    &lt;div style="display:inline-block; float:left; margin-right:25px"&gt;

    <span style="display:block; margin-bottom:12px">Using Delimiter</span> 

        @Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

    .MultiSelectMode(MultiSelectModeTypes.Delimiter).Delimiter(";")





    &lt;/div&gt;

    &lt;div style="display:inline-block; float:left; margin-right:25px"&gt;

    <span style="display:block; margin-bottom:12px">Using VisualMode</span> 

        @Html.EJ().Autocomplete("autocompletevisual")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

    .MultiSelectMode(MultiSelectModeTypes.VisualMode)



    &lt;/div&gt;

    &lt;div style="display:inline-block; float:left;"&gt;

        <span style="display:block; margin-bottom:12px">Single selection</span>

        @Html.EJ().Autocomplete("autocompletesingle")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

.MultiSelectMode(MultiSelectModeTypes.None)





    &lt;/div&gt;

&lt;/div&gt;





The following image is the output for AutoComplete control with configured multiple selection.



{ ![](MultiSelection-modes_images/MultiSelection-modes_img1.png) | markdownify }
{:.image }


_AutoComplete with MultiSelection_

