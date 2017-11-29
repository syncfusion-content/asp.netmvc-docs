---
layout: post
title: Multiple Columns | AutoComplete | ASP.NET MVC | Syncfusion
description: multiple columns
control: AutoComplete
documentation: ug
---

# Multiple Columns

The Autocomplete allows list of data to be displayed in several columns and column collection can be defined and customized through the **MultiColumnSettings** property.

In AutoComplete Multiple Column search is based on **searchColumnIndices** property which allows user to search text for any number of fields in the suggestion list without modifying the selected text format.

In AutoComplete Multiple Column searched value is updated to autocomplete input box based on **StringFormat** property which specifies values to updated.

N> **StringFormat** as “{0} ({1}) ({2})” means search based on 0, 1 and 2 columns data.

<table><tr><th>Name</th><th>Description</th></tr>
<tr><td>Enable</td><td>Allow list of data to be displayed in several columns.</td></tr>
<tr><td>ShowHeader</td><td>Allow header text to be displayed in corresponding columns.</td></tr>
<tr><td>StringFormat</td><td>Displayed selected value and autocomplete search based on mentioned column value specified in that format.</td></tr>
<tr><td>Columns</td><td>Field and Header Text collections can be defined and customized through this field.</td></tr>
<tr><td>Field</td><td>Get or set a value that indicates to display the columns in the autocomplete mapping with column name of the dataSource. </td></tr>
<tr><td>HeaderText</td><td>Get or set a value that indicates to display the title of that particular column.</td></tr></table>


## Configuring Multiple Columns

The following steps explain the configuration of the Multiple Columns for an AutoComplete textbox.

1.	In the View page, define the AutoComplete control and configure multicolumn.


{% highlight CSHTML %}

@*Refer to the DataSource defined in Local Data binding Step 1 *@

    <div style="width: 600px">

        <div style="display:inline-block; float:left; margin-right:25px">

        <span style="display:block; margin-bottom:12px">Using Delimiter</span> 

    @Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)
        
    .MultiColumnSettings(obj => obj.Enable(true).Columns(obj1 =>
    {
    obj1.Field("uniqueKey").HeaderText("Unique Key").Add();
    obj1.Field("text").HeaderText("Text").Add();
    }).ShowHeader(true).SearchColumnIndices(new List<int> { 0,1,2,3 }).StringFormat("{0}"))

        </div>
        
    </div>

{% endhighlight %}



The following image is the output for AutoComplete control with configured multiple column.



![](multicolumn_images/multicolumn_img1.png)



_AutoComplete with MultiColumn_

