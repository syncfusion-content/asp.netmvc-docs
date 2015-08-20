---
layout: post
title: Behavior-settings
description: behavior settings
platform: ejmvc
control: Toolbar
documentation: ug
---

# Behavior settings

The following are some miscellaneous properties that enables you to change the behavior of Toolbar control.

## Enabling Toolbar

Enabled property is Boolean type, which allow us to enable or disable the Toolbar control. By default Enabled value is true. You can specify the property Enabled in the script as follows.



{% highlight html %}

// Add this code in your CSHTML page and refer local data section for data source

<div class="cols-sample-area"> 
   @Html.EJ().Toolbar("toolbarcontent").Width("250").Datasource((IEnumerable<ToolbarLocalBinding>)ViewBag.datasource)
   .ToolbarFields(f => f.ID("IconId").SpriteCssClass("SpriteCss").TooltipText("Tooltip")).Enabled(false)

</div>

{% endhighlight %}

The following screenshot illustrates a Toolbar with Disable mode.

![](Behavior-settings_images/Behavior-settings_img1.png)



_Figure 8: ToolBar control in Enabled (false)_



## Hiding Toolbar 

The Hide property is Boolean type, which allow us to show or hide the Toolbar. Default value of Hide is false. You can specify the property Hide in the script as follows. 



 {% highlight html %}

// Add this code in your CSHTML page and refer local data section for data source

<div class="cols-sample-area"> 
   @Html.EJ().Toolbar("toolbarcontent").Width("250").Datasource((IEnumerable<ToolbarLocalBinding>)ViewBag.datasource)
   .ToolbarFields(f => f.ID("IconId").SpriteCssClass("SpriteCss").TooltipText("Tooltip")).Hide(true)

</div>

{% endhighlight %}



