---
layout: post
title: Application-Tab
description: application tab
platform: ejmvc
control: Ribbon
documentation: ug
---

# Application Tab

The_Application Menu_ support is provided in the _Ribbon_ control _Application tab_. Use _ApplicationTab_ property to define the application tab with menu. In _ApplicationTab_ definition, _Type_ property defines the application menu and the value is _ApplicationMenu_,_ItemID_ property to specify ID of _UL_ list for application menu and _MenuSettings_ property to specify all the members and events of the menu.



{% highlight html %}

@(Html.EJ().Ribbon("Ribbon")

.Width("800px")

.ApplicationTab(apptab =>

{

apptab.Type("ApplicationMenu").ItemID("menu").MenuSettings(new MenuProperties()

{

OpenOnClick = false

});

})

.RibbonTabs(tab =>

{

tab.Id("home").Text("HOME").TabGroups(tabgrp =>

{

tabgrp.Text("CustomControls").Type("custom").ContentID("Contents").Add();

}).Add();

})

)



<ul id="menu">

<li><a>FILE</a>

<ul>

<li><a>New</a></li>

<li><a>Open</a></li>

</ul>

</li>

</ul>

<div id="Contents">Custom control</div>



{% endhighlight %}



The following screenshot illustrates _Ribbon_ with application menu.

![](Application-Tab_images/Application-Tab_img1.png)





