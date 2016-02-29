---
layout: post
title: Quick Access Toolbar | Ribbon | ASP.NET MVC | Syncfusion
description: quick access toolbar
platform: ejmvc
control: Ribbon
documentation: ug
keywords: quick access toolbar,ribbon quick access toolbar
---

# Quick Access Toolbar

Quick Access Toolbar provides the shortcuts to the most commonly used commands by placing the controls at the Quick Access Toolbar section. It can be placed at the top or bottom of the Ribbon.

Set `ShowQAT` as true to enable Quick Access Toolbar in Ribbon. It supports the Button, Split Button, Toggle Button controls. The `QuickAccessMode` is used to change the controls state in Quick Access Toolbar through options as `Toolbar`,`Menu` and `none`. Default value is `none` and QAT toolbar is created with specified controls added in Toolbar.

The `ToolBar` option used to set controls visibility in Quick Access Toolbar.The `Menu` option shows the controls in Quick Access Menu and does not show controls in Quick Access Toolbar.

Once the controls are visible in Toolbar , then controls state will be set as ticked in Quick Access Menu and vice versa.

The client side event for Quick Access Toolbar menu click is ` QatMenuItemClick`.

`More Commands` command provides with Quick Access Menu. This can be customized using `QatMenuItemClick` event, such as to show popup dialog. 

{% highlight CSHTML %}

    @section ControlsSection {
    @(Html.EJ().Ribbon("defaultRibbon")
                .Width("500")
                .ShowQAT(true)
                .ApplicationTab(apptab =>
                {
                    apptab.Type(ApplicationTabType.Menu).MenuItemID("ribbonmenu");
                })
                .RibbonTabs(tab =>
                {
                    tab.Id("home").Text("HOME").TabGroups(tabgrp =>
                    {
                        tabgrp.Text("SplitButton").AlignType(RibbonAlignType.Columns).Content(cnt =>
                        {
                                cnt.ContentGroups(cntgrp =>
                                {
                                    cntgrp.Id("paste").Text("Paste").ToolTip("Paste").Type(RibbonButtonType.SplitButton).QuickAccessMode(QuickAccessMode.ToolBar).SplitButtonSettings(new SplitButtonProperties()
                                    {
                                        ContentType = ContentType.ImageOnly,
                                        PrefixIcon = "e-ribbon e-ribbonpaste",
                                        TargetID = "pasteSplit",
                                        ArrowPosition = ArrowPosition.Bottom,
                                        ButtonMode = ButtonMode.Dropdown,
                                    }).Add();
                                }).ContentDefaults(df => df.Type(RibbonButtonType.SplitButton).Width("50px").Height("70px")).Add();                            
                        }).Add();
                        tabgrp.Text("Button").AlignType(RibbonAlignType.Rows).Content(cnt =>
                        {
                            cnt.ContentGroups(cntgrp =>
                                {
                                    cntgrp.Id("italic").ToolTip("Italic").QuickAccessMode(QuickAccessMode.ToolBar).Type(RibbonButtonType.ToggleButton).ToggleButtonSettings(new ToggleButtonProperties()
                                    {
                                        ContentType = ContentType.ImageOnly,
                                        DefaultText = "Italic",
                                        ActiveText = "Italic",
                                        DefaultPrefixIcon = "e-ribbon e-ribbonitalic",
                                        ActivePrefixIcon = "e-ribbon e-ribbonitalic",                                        
                                    }).Add();
                        }).ContentDefaults(df => df.Type(RibbonButtonType.Button).Width("40px").Height("70px")).Add();
                        }).Add();
                        tabgrp.Text("Toggle").AlignType(RibbonAlignType.Columns).Content(cnt =>
                        {
                            cnt.ContentGroups(cntgrp =>
                            {
                                cntgrp.Id("bold").ToolTip("Bold").QuickAccessMode(QuickAccessMode.ToolBar).Type(RibbonButtonType.ToggleButton).ToggleButtonSettings(new ToggleButtonProperties()
                                {
                                    ContentType = ContentType.ImageOnly,
                                    DefaultText = "Bold",
                                    ActiveText = "Bold",
                                    DefaultPrefixIcon = "e-ribbon bold",
                                    ActivePrefixIcon = "e-ribbon bold",
                                }).Add();
                            }).ContentDefaults(df => df.IsBig(false)).Add();                                                
                        }).Add();
                    }).Add();
                }).ClientSideEvents(evt => evt.Create("createControl").QatMenuItemClick("qatMenuItemClick"))
    )
    <ul id="ribbonmenu">
        <li>
            <a>FILE</a>
            <ul>
                <li><a>New</a></li>
            </ul>
        </li>
    </ul>
    <ul id="pasteSplit">
        <li><a>Paste</a></li>
    </ul>
    }
    @section StyleSection{
    <link href="~/Content/ej/ribbon-css/ej.icons.css" rel="stylesheet" />
    <style>
       .e-ribbon .e-rbnquickaccessbar .e-ribbonpaste:before {
            font-size: 27px;
            left: -5px;
            top: -6px;
        }
        .e-ribbon .e-ribbonpaste:before {
            font-family: 'ej-ribbonfont';
            content: "\e169";
            font-size: 36px;
            position: relative;
            left: -9px;
            top: -4px;
        }
        .e-ribbon .e-ribbonitalic:before ,.e-ribbon .bold:before{
            font-family: 'ej-ribbonfont';
            font-size: 16px;
            left: -1px;
            position: relative;
            top: -1px;
        }
         .e-ribbon .e-ribbonitalic:before ,.e-ribbon .bold:before{
            content: "\e163";
        }
        .e-ribbon .bold:before {
            content: "\e15a";
        }
        .e-ribbon .e-rbnquickaccessbar .e-undo::before {
            font-size: 18px;
            line-height: 12px;
            text-indent: -3px;
        }    
    </style>
    }

{% endhighlight %}

![](Quick-Access-Toolbar_images/Quick-Access-Toolbar_img1.png)
