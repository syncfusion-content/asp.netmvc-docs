---
layout: post
title: Miscellaneous
description: miscellaneous
platform: ejmvc
control: Checkbox
documentation: ug
---

# Miscellaneous

## Checkbox Id

Checkbox id is not displayed in user interface. Here, Id mentions the id attribute of the root element of Checkbox control. When you assign a value for Id property, then this older id is replaced by new id. This id value should be unique. 

Set id for Checkbox control as follows.



{% highlight js %}



    @*set id for checkbox *@

    @Html.EJ().CheckBox("checkbox_id").Id("sync")



{% endhighlight %}



## Checkbox Id Prefix

Id prefix value is the one that is appended to id value. It is used to mention the prefix for the wrapper’s id attribute. When you assign a value for IdPrefix property, the older prefix id is replaced by new prefix id. 

Set prefix id for Checkbox control as follows.



{% highlight js %}

    @*set prefix id for checkbox *@

    @Html.EJ().CheckBox("checkbox_idPrefix").IdPrefix("JS")

{% endhighlight %}



## Checkbox Name

The name attribute is used to identify from data after it is submitted to the server. Checkbox also contains name attribute. This name should be a unique one. It is used to receive the Checkbox value. Without using name, you can’t get the particular checkbox values at the time of submitting form.

## Checkbox Value

For Checkbox, the contents of the value property do not appear in the user interface. The value property contains only a meaning when submitting a form. When a Checkbox is in checked state and when the form is submitted, the name of the Checkbox is sent along with the value of the value property (When the checkbox is not checked, no information is sent).

You can set name and value for Checkbox control as follows.



{% highlight js %}

    @*set name and value for checkbox *@

    @Html.EJ().CheckBox("checkbox").Name("Conformation").Value("received")

{% endhighlight %}











