---
layout: post
title: backstage page
description: backstage page
platform: js
control: Control Name undefined
documentation: ug
---

### Backstage Page

Ribbon control has Backstage page support.The left side of the backstage page contains the backstage tab and button items. The right side of the backstage page contains the UserControl items.To render the ribbon with backstage page, set _**ApplicationTab’s** __**Type**_ as _**"Backstage"**_ and _**Text**_ property in the _**ApplicationTab**_ is set as text for Apllication tab.

 You can set the height and width to the backstage page by using the _**Height**_ and _**Width**_ properties.

* _**Id**_ **–** Specify id of the backstage tab and button .

* _**Text**_**–** Specify text of the backstage tab and button.

* _**ContentID**_ **–**Specify id of the UserControl’s Parent item.

* _**ItemType**_ **–**Specify the type of the backstage page item to render the backstage tab or button.

* ItemType.Tab — To render the backstage tab.

* ItemType.Button - To render the backstage button.

* _**EnableSeparator**_ **–**Set true to enable the separator between backstage button and tab items.



**[MVC]**

**[CSHTML]**


	@(Html.EJ().Ribbon("Ribbon")
	.Width("600px")
	.ApplicationTab(apptab => apptab.Type(ApplicationTabType.Backstage)
		.BackstageSettings(bs => bs.Text("FILE").Height("230").Width("550").Pages(bspage =>
		{
			bspage.Id("info").Text("Info").ContentID("infoCon").ItemType(ItemType.Tab).Add();
	
			bspage.Id("new").Text("New").ContentID("newCon").Add();
	
			bspage.Id("close").Text("Close").ItemType(ItemType.Button).EnableSeparator(true).Add();
	
			bspage.Id("account").Text("Office Account").ContentID("accountCon").Add();
	
		})))
	.RibbonTabs(tab => tab.Id("home").Text("HOME").TabGroups(tabgrp => tabgrp.Text("New").Type("custom").ContentID("Contents").Add()).Add())
	)

	<div id="infoCon">Info Tab</div>
	
	<div id="newCon">New Tab</div>
	
	<div id="accountCon">Account Tab</div>
	
	<div id="Contents">Home control</div>

The following output is displayed as a result of the above code example.

![](backstagepage_images\backstagepage_img1.png)
