---
layout: post
title: RTL
description: rtl
platform: ejmvc
control: Toolbar
documentation: ug
---

# RTL

EnableRTL property is Boolean type, which allow us to change the left-to-right alignment of the Toolbar to right-to-left (RTL) that sets the Toolbar to do its actions from right to left. Default value of EnableRTL is false. You can specify the EnableRTL property in the script as below, 

{% highlight html %}

// Add this code in your CSHTML page and refer local data section for data source

<div class="cols-sample-area"> 
   @Html.EJ().Toolbar("toolbarcontent").Width("250").Datasource((IEnumerable<ToolbarLocalBinding>)
   ViewBag.datasource).ToolbarFields(f => f.ID("IconId").SpriteCssClass("SpriteCss").TooltipText("Tooltip")).EnableRTL(true)
   </div>



{% endhighlight %}



![](RTL_images/RTL_img1.png)


_Figure 31: Toolbar from RTL_

