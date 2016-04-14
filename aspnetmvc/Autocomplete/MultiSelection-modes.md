---
layout: post
title: MultiSelection modes | AutoComplete | ASP.NET MVC | Syncfusion
description: multiselection modes
platform: ejmvc
control: AutoComplete
documentation: ug
---

# MultiSelection modes

AutoComplete widget allows you to select multiple values from the suggestions list using the MultiSelectMode property. Multiple values are selected when MultiSelectMode value is set to VisualMode or Delimiter. 

Delimiter mode separates multiple items using a separator character defined. When the delimiter mode is set, you can define the delimiter character using DelimiterChar. It takes a single character and it is a symbol. 

VisualMode selects multiple items by enclosing the item in a rounded rectangle with a close icon to remove item from the selection.

## Configuring MultiSelection Mode

The following steps explain the configuration of the MultiSelectMode for an AutoComplete textbox.



1. In the View page, define the AutoComplete control and configure multiple selection mode.


{% highlight CSHTML %}

@*Refer to the DataSource defined in Local Databinding Step 1 *@

<div style="width: 600px">

    <div style="display:inline-block; float:left; margin-right:25px">

    <span style="display:block; margin-bottom:12px">Using Delimiter</span> 

        @Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

    .MultiSelectMode(MultiSelectModeTypes.Delimiter).Delimiter(";")

    </div>

    <div style="display:inline-block; float:left; margin-right:25px">

    <span style="display:block; margin-bottom:12px">Using VisualMode</span> 

        @Html.EJ().Autocomplete("autocompletevisual")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

    .MultiSelectMode(MultiSelectModeTypes.VisualMode)

    </div>

    <div style="display:inline-block; float:left;">

        <span style="display:block; margin-bottom:12px">Single selection</span>

        @Html.EJ().Autocomplete("autocompletesingle")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

.MultiSelectMode(MultiSelectModeTypes.None)

    </div>

</div>

{% endhighlight %}



The following image is the output for AutoComplete control with configured multiple selection.



![](MultiSelection-modes_images/MultiSelection-modes_img1.png)



_AutoComplete with MultiSelection_

