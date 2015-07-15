---
layout: post
title: Contextual-Tab-and-Tab-Set
description: contextual tab and tab set
platform: ejmvc
control: Ribbon
documentation: ug
---

## Contextual Tab and Tab Set

You can add _Contextual Tabs_ and _Tab Set_ in the _Ribbon_ control. In _ContextualTabs_ definition, use _RibbonTabs_ property to add _contextual tabs_ and _contextual tab set_. In _ContextualTabs_ definition, use _BackgroundColor_ property to apply background color to the _Contextual Tabs_ and _Tab Set_. Use _BorderColor_ property to apply border color to the _Contextual__Tabs_ and _Tab Set._



{% highlight html %}

[MVC]



[CSHTML]

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

    .ContextualTabs(ctabs => {

            ctabs.BackgroundColor("#FCFBEB").BorderColor("#F2CC1C").RibbonTabs(ctab =>

            {

                ctab.Id("Design").Text("DESIGN").TabGroups(ctabgrp =>

                {

                    ctabgrp.Text("Table Style Options").Type("custom").ContentID("contextualTab").Add();

                }).Add();

            });

            ctabs.BackgroundColor("blue").BorderColor("lightblue").RibbonTabs(ctab =>

            {

                ctab.Id("tabset1").Text("Tabset1").TabGroups(ctabgrp =>

                {

                    ctabgrp.Text("Tabset1 Styles").Type("custom").ContentID("contextualTabset1").Add();

                }).Add();

                ctab.Id("tabset2").Text("Tabset2").TabGroups(ctabgrp =>

                {

                    ctabgrp.Text("Tabset2 Styles").Type("custom").ContentID("contextualTabset2").Add();

                }).Add();

            });

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

    <div id="Contents">Custom Control</div>

    <div id="contextualTab">

        <button id="contextualBtn">Contextual Tab</button></div>

    <div id="contextualTabset1">

        <button id="contextualTabsetBtn1">Contextual Tabset1</button></div>

    <div id="contextualTabset2">

        <button id="contextualTabsetBtn2">Contextual Tabset2</button></div>



{% endhighlight %}





The following screenshot illustrates _Ribbon_ with _Contextual Tabs and Tab Set_.

{ ![](Contextual-Tab-and-Tab-Set_images/Contextual-Tab-and-Tab-Set_img1.png) | markdownify }
{:.image }


