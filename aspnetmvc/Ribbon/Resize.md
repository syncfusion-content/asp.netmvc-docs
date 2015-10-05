---
layout: post
title: Resize | Ribbon | ASP.NET MVC | Syncfusion
description: resize 
platform: ejmvc
control: Ribbon
documentation: ug
---

# Resize 

_Ribbon control_ supports resizing functionality .To enable resizing in the ribbon, you need to set the _AllowResizing_ property to _true_. When you resize the ribbon window, the _Ribbon control_ automatically resizes to fit into the layout panel. 



{% highlight CSHTML %}

@(Html.EJ().Ribbon("defaultRibbon")

.Width("70%")

.AllowResizing(true)


.ApplicationTab(apptab =>

{

	apptab.Type(ApplicationTabType.Menu).MenuItemID("ribbonmenu");


})

.RibbonTabs(tab =>

{

tab.Id("insert").Text("INSERT").TabGroups(tabgrp =>

{

tabgrp.Text("Clipboard").AlignType(RibbonAlignType.Rows).Content(cnt =>

{

	cnt.ContentGroups(cntgrp =>

	{

		cntgrp.Id("cut").Text("Cut").Add();

		cntgrp.Id("copy").Text("Copy").Add();



	}).Add();

}).Add();

tabgrp.Text("Font").AlignType(RibbonAlignType.Rows).Content(cnt =>

{

	cnt.ContentGroups(cntgrp =>

	{

		cntgrp.Id("bold").Text("Bold").Add();

		cntgrp.Id("italic").Text("Italic").Add();

		cntgrp.Id("underline").Text("Underline").Add();

		cntgrp.Id("strikethrough").Text("Strikethrough").Add();



	}).ContentDefaults(df => df.Height("70")).Add();

}).Add();

tabgrp.Text("New").AlignType(RibbonAlignType.Rows).Content(cnt =>

{

	cnt.ContentGroups(cntgrp =>

	{

		cntgrp.Id("New").Text("New").Text("New").Add();

	}).Add();



}).Add();

tabgrp.Text("Actions").AlignType(RibbonAlignType.Rows).Content(cnt =>

{

	cnt.ContentGroups(cntgrp =>

	{

		cntgrp.Id("undo").Text("Undo").Add();

		cntgrp.Id("redo").Text("Redo").ToolTip("Redo").Add();

	}).Add();

}).Add();



}).Add();

})

)

<ul id="ribbonmenu">

	<li><a>FILE</a>

 <ul><li><a>New</a></li></ul>

	</li>

</ul>



{% endhighlight %}

The following screenshot displays _Ribbon control_ without resizing the window.

![](Resize_images/Resize_img1.png)



When you resize the window, the ribbon groups are converted  into _group button_ based on the window width.When you click the group button, the corresponding group items are displayed .The following screenshot displays the _Ribbon_ control when  clicking the group button _Actions_.



![](Resize_images/Resize_img2.png)



