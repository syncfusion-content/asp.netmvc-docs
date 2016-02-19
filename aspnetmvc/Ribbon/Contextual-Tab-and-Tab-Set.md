---
layout: post
title: Contextual Tab and Tab Set | Ribbon | ASP.NET MVC | Syncfusion
description: contextual tab and tab set
platform: ejmvc
control: Ribbon
documentation: ug
---

# Contextual Tab And Tab Set

Contextual Tabs are collection of Tabs that extended styling and can be shown based on some criteria. Contextual Tabs can be added like `RibbonTabs` including TabGroup and TabContent section. You can set `BackGroundColor` and `BorderColor` to highlight them as Tab set.

{% highlight CSHTML %}

     @(Html.EJ().Ribbon("Ribbon")
     .Width("500")
         .ApplicationTab(apptab => {
                 apptab.Type(ApplicationTabType.Menu).MenuItemID("ribbonmenu").MenuSettings(new MenuProperties()
                       {
                             OpenOnClick = false
                       });
          })
         .RibbonTabs(tab => {
         tab.Id("home").Text("HOME").TabGroups(tabgrp => {
                 tabgrp.Text("CustomControls").Type("custom").ContentID("Contents").Add();
         }).Add();
         })
         .ContextualTabs(ctabs => {
         ctabs.BackgroundColor("#FCFBEB").BorderColor("#F2CC1C").RibbonTabs(ctab => {
         ctab.Id("Design").Text("DESIGN").TabGroups(ctabgrp => {
                  ctabgrp.Text("Table Style Options").Type("custom").ContentID("contextualTab").Add();
     }).Add();
     });
         ctabs.BackgroundColor("blue").BorderColor("lightblue").RibbonTabs(ctab => {
         ctab.Id("tabset1").Text("Tabset1").TabGroups(ctabgrp => {
                ctabgrp.Text("Tabset1 Style").Type("custom").ContentID("headings").Add();
     }).Add();
         ctab.Id("tabset2").Text("Tabset2").TabGroups(ctabgrp => {
                ctabgrp.Text("Tabset2 Styles").Type("custom").ContentID("contextualTabset2").Add();
     }).Add();
     });
     })
     )
    <ul id="ribbonmenu">
    <li>
            <a>FILE</a>
            <ul>
                <li><a>New</a></li>
                <li><a>Open</a></li>
           </ul>
        </li>
    </ul>
    <div id="headings" class="e-headings">
        <div>
            <p>AaBbCcDd</p>
            <p>No Spacing</p>
        </div>
        <div>
            <p class="e-strong">AaBbCcDd</p>
            <p>Strong</p>
        </div>
        <div>
            <p class="e-emphasis">AaBbCcDd</p>
            <p>Emphasis</p>
        </div>
    </div>
    <div id="Contents">Custom Control</div>
    <div id="contextualTab">
    <button id="contextualBtn">Contextual Tab</button>
    </div>
    <div id="contextualTabset2">
    <button id="contextualTabsetBtn2">Contextual Tabset2</button>
    </div>
    @section StyleSection{
    <link href="~/Content/ej/ribbon-css/ej.icons.css" rel="stylesheet" />
    }

{% endhighlight  %}

![](Contextual-Tab-and-Tab-Set_images/Contextual-Tab-and-Tab-Set_img1.png)





