---
layout: post
title: Backstage Page | Ribbon | ASP.NET MVC | Syncfusion
description: backstage page
platform: ejmvc
control: Ribbon
documentation: ug
---

# Backstage Page

Ribbon control has Backstage page support.The left side of the backstage page contains backstage tab and button items,right side of the backstage page contains UserControl items.To render ribbon with backstage page set _**ApplicationTab’s** __**Type**_ as _**"Backstage"**_ and _**Text**_ property in _**ApplicationTab**_ to set text for Apllication tab.

 We can set height and width to backstage page using properties _**Height**_ and _**Width**_.

* _**Id**_ **–** Specify id of backstage tab and button .

* _**Text**_**–** Specify text of backstage tab and button.

* _**ContentID**_ **–**Specify id of UserControl’s Parent item.

* _**ItemType**_ **–**Specify the type of backstage page item to render backstage tab or button.

* ItemType.Tab —to render backstage tab.

* ItemType.Button -to render backstage button.

* _**EnableSeparator**_ **–**Set true to enable separator between backstage button and tab items.




{% highlight CSHTML %}

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
{% endhighlight %}


The following output is displayed as a result of the above code example.

![](BackstagePage_images\backstagepage_img1.png)
