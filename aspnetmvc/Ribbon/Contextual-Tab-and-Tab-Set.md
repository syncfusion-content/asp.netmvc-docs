---
layout: post
title: Contextual Tab and Tab Set | Ribbon | ASP.NET MVC | Syncfusion
description: contextual tab and tab set
platform: ejmvc
control: Ribbon
documentation: ug
---

# Contextual Tab And Tab Set

Contextual Tabs are collection of Tabs that extended styling and can be shown based on some criteria. Contextual Tabs can be added like `RibbonTabs` including TabGroup and TabContent section. You can set `BackGroundColor` and `BorderColor` to highlight them as Tab set. Contextual tabs can be added or set dynamically in ribbon control using [`addContextualTabs`](https://help.syncfusion.com/api/js/ejribbon#methods:addcontextualtabs) with it's object and index position.

{% highlight CSHTML %}

     @(Html.EJ().Ribbon("Ribbon")
     .Width("500")
         .ApplicationTab(app => {
                 app.Type(ApplicationTabType.Menu).MenuItemID("ribbon").MenuSettings(new MenuProperties()
                       {
                             OpenOnClick = false
                       });
          })
         .RibbonTabs(tab => {
         tab.Id("home").Text("HOME").TabGroups(tabGroup => {
                 tabGroup.Text("CustomControls").Type("custom").ContentID("Contents").Add();
         }).Add();
         })
         .ContextualTabs(contextualTab => {
         contextualTab.BackgroundColor("#FCFBEB").BorderColor("#F2CC1C").RibbonTabs(ribbonTab => {
         ribbonTab.Id("Design").Text("DESIGN").TabGroups(contextTabGroup => {
                  contextTabGroup.Text("Table Style Options").Type("custom").ContentID("contextualTab").Add();
     }).Add();
     });
         contextualTab.BackgroundColor("blue").BorderColor("lightblue").RibbonTabs(ribbonTab => {
         ribbonTab.Id("tabset1").Text("Tabset1").TabGroups(contextTabGroup => {
                contextTabGroup.Text("Tabset1 Style").Type("custom").ContentID("headings").Add();
     }).Add();
         ribbonTab.Id("tabset2").Text("Tabset2").TabGroups(contextTabGroup => {
                contextTabGroup.Text("Tabset2 Styles").Type("custom").ContentID("contextualTabset2").Add();
     }).Add();
     });
     })
     )
    <ul id="ribbon">
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
            <p>First Heading</p>
            <p>No Spacing</p>
        </div>
        <div>
            <p class="e-strong">Second Heading</p>
            <p>Strong</p>
        </div>
        <div>
            <p class="e-emphasis">Third Heading</p>
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





