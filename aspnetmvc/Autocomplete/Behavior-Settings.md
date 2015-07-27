---
layout: post
title: Behavior-Settings
description: behavior settings
platform: ejmvc
control: AutoComplete
documentation: ug
---

# Behavior Settings

## Filtering Type

AutoComplete textbox supports a wide range of filtering options to search items in the PopUp list. The FilterType takes enum or string values. The default value is startswith. Other supported values are contains endswith, lessthan, greaterthan, greaterthanorequal, lessthanorequal, equal and notequal.

### Defining the Filter type

The following steps explain the configuration of the filtering conditions for an AutoComplete textbox.



1. In the View page, define the AutoComplete control and add the filter type as contains.

{% highlight html %}


@*Refer to the DataSource defined in Local Databinding Step 1 *@



@Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

    .FilterType(FilterOperatorType.Contains)


{% endhighlight %}


The following image is the output for AutoComplete control that filters list items based on the ‘contains’ option.

![](Behavior-Settings_images/Behavior-Settings_img1.png)



_AutoComplete using "contains" filterType_

## AutoFill

The AutoComplete textboxwidget offers an AutoFill option. This feature is used to automatically fill the item when text is entered when EnableAutoFill is set to ‘True’. The first Item in the suggestions list that matches the entered text is automatically displayed in the AutoComplete textbox. The search text is selected in the AutoComplete textbox for identification. 

This feature reduces the need to type the entire text and makes the search box more efficient. This is used only with filterType “startswith”, since text is filled automatically based on the text entered.

### Configure AutoFill property in AutoComplete

The following steps explain how to enable the AutoFill property for an AutoComplete textbox.

1. In the View page, add the Autocomplete helper and enable the EnableAutoFill property

{% highlight html %}



@*Refer to the DataSource defined in Local Databinding Step 1 *@



@(Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>

    )ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

    .EnableAutoFill(true))    


{% endhighlight %}


The following image is the output for AutoComplete when EnableAutoFill is set to ‘True’.

![](Behavior-Settings_images/Behavior-Settings_img2.png)



_AutoComplete with AutoFill_

## Sorting Items

AutoComplete widget allows you to sort the suggestions list items and set the sorting order. To enable sorting, set AllowSorting to ‘True’. It is enabled by default. The SortOrder property takes enum values, either in ascending or descending order.

### Steps to define sorting order and distinct

The following steps explain how to enable the sorting property for an AutoComplete textbox.



1. In the View page, define the AutoComplete control and enable AllowSorting.


{% highlight html %}


@*Refer to the DataSource defined in Local Databinding Step 1 *@



@Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

    .AllowSorting(true).SortOrder(SortOrder.Descending)


{% endhighlight %}




The following image is the output for AutoComplete when “SortOrder” is configured.



![](Behavior-Settings_images/Behavior-Settings_img3.png)



_AutoComplete PopUp sorted in descending order_

## Distinct List items

AutoComplete widget provides an option to extract repeating items in the PopUp list. By setting EnableDistinct property to ‘True’, you can prevent the duplicate items in the suggestions list.

### Steps to enable distinct items

The following steps explain you how to enable this property.



1. In the View page, define the AutoComplete control and configure the EnableDistinct property.


{% highlight html %}



@*Refer to the DataSource defined in Local Databinding Step 1 *@

<div style="width: 400px">

    <div style="float: left;">

        <h6><span style="font-style: italic; font-weight: normal; position: absolute; margin-top: -30px;">

                Distinct disabled</span></h6>  

@Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

    .EnableDistinct(false)



    </div>

    <div id="binding" style="float: right;">

        <h6><span style="font-style: italic; font-weight: normal; position: absolute; margin-top: -30px;">

                Distinct enabled</span></h6>

        @Html.EJ().Autocomplete("autocompletedistinct")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

    .EnableDistinct(true)



    </div>	

</div>


{% endhighlight %}


The following images are the outputs for AutoComplete when EnableDistinct is set to “True” and “False”.

![](Behavior-Settings_images/Behavior-Settings_img4.png)



_AutoComplete PopUp items with Distinct property disabled and enabled_

## Show Popup button

Show Popup button property provides you with an option to display an icon, to show the popup list in the AutoComplete widget.

### Enabling Popup button

The following steps explains you how to configure the Popupbutton for an AutoComplete textbox.



1. In the View page, define the AutoComplete control and enable ShowPopupButton property.

{% highlight html %}	


@*Refer to the DataSource defined in Local Databinding Step 1 *@

@Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

    .ShowPopupButton(true)

{% endhighlight %}





The following image is the output for AutoComplete when ShowPopupButton is enabled.

![](Behavior-Settings_images/Behavior-Settings_img5.png)



_AutoComplete with popup icon_

## Restrict editing

AutoComplete textbox widget provides ReadOnly property to disable editing in the control, so that the value set to AutoComplete can only be read and cannot be modified by the user. The value property allows you to set the default value for AutoComplete widget, when it is created.

### Configure AutoComplete textbox to restrict editing

The following steps help you to disable editing in an AutoComplete textbox.



1. In the View page, define the AutoComplete control and configure Readonly property.


{% highlight html %}



@*Refer to the DataSource defined in Local Databinding Step 1 *@

@Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

    .Readonly(true).Value("BMW 7")

    .ShowPopupButton(true)


{% endhighlight %}




The following image is the output for the AutoComplete textbox configured to restrict editing.

![](Behavior-Settings_images/Behavior-Settings_img6.png)



_AutoComplete with readOnly property_

## Empty Result settings

The AutoComplete widget allows you to configure the display message when the list doesn’t return any values. By default, ShowEmptyResultText is set to ‘True’ and EmptyResultText is set to the string value “No suggestions_”._ 

### Configure Empty result setting

The following steps allow you to set text for emptyresults of an AutoComplete textbox.



1. In the View page, define the AutoComplete control and set the desired text message to be shown in EmptyResultText.


{% highlight html %}



@*Refer to the DataSource defined in Local Databinding Step 1 *@

@Html.EJ().Autocomplete("autocomplete")

    .Datasource((IEnumerable<CarsList>)ViewBag.datasource)

    .AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))

    .ShowEmptyResultText(true).EmptyResultText("Item not found in list")


{% endhighlight %}




The following image is the output of the AutoComplete textbox when the list doesn’t return any value.

![](Behavior-Settings_images/Behavior-Settings_img7.png)



_AutoComplete with customized emptyResultText_

