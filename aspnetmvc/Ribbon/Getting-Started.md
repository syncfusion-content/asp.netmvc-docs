---
layout: post
title: Getting Started | Ribbon | ASP.NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: Ribbon
documentation: ug
---

# Getting Started

This section explains briefly how to create a Ribbon in your application with ASP.NET MVC. You can refer [MVC Getting Started documentation](http://help.syncfusion.com/aspnetmvc/getting-started) to create new project and add necessary dll’s and script files.

## Control Initialization

Ribbon can be initialized with `ApplicationTab` and UL list is needed for binding Menu to application Menu which can be specified through `MenuItemID` which denotes `Id` of UL.

Define the Application Tab with `Type` as `Menu` to render simple Ribbon control.
          
{% highlight CSHTML %}

      @(Html.EJ().Ribbon("defaultRibbon")
     .Width("500")
     .ApplicationTab(apptab => {
         apptab.Type(ApplicationTabType.Menu).MenuItemID("Ribbonmenu").MenuSettings(new MenuProperties() {
             OpenOnClick = false
         });
        }))
        <ul id="Ribbonmenu">
        <li>
            <a>FILE</a>
            <ul>
                <li><a>New</a></li>
                <li><a>Open</a></li>
                <li><a>Save</a></li>
                <li><a>Save As</a></li>
                <li><a>Print</a></li>
            </ul>
        </li>
    </ul>

{% endhighlight  %}

![](Getting-Started_images/Getting-Started_img1.png)

N> Set the required `Width` to Ribbon, else default parent container or window Width will be considered.

## Adding Tabs

RibbonTab is a set of related groups which are combined into single item. For creating Tab, `Id` and `Text` properties should be specified. 

{% highlight CSHTML %}

        @(Html.EJ().Ribbon("defaultRibbon")
        .Width("500")
        .ApplicationTab(apptab => {
            apptab.Type(ApplicationTabType.Menu).MenuItemID("Ribbonmenu").MenuSettings(new MenuProperties() {
                OpenOnClick = false
            });
        })
        .RibbonTabs(tab => {
            tab.Id("home").Text("HOME").TabGroups(tabgrp => {}).Add();
        })
             )
     <ul id="Ribbonmenu">
        <li>
            <a>FILE</a>
            <ul>
                <li><a>New</a></li>
                <li><a>Open</a></li>
                <li><a>Save</a></li>
                <li><a>Save As</a></li>
                <li><a>Print</a></li>
            </ul>
        </li>
    </ul>

{% endhighlight  %}

![](Getting-Started_images/Getting-Started_img2.png)

## Configuring Groups

List of controls are combined as logical `ContentGroups ` into RibbonTabs. TabGroup alignment type as “Rows/Columns”, Default is `Rows`. 

Create TabGroup item with `Text` specified and add ContentGroup to ContentGroup collection with Button control settings.

{% highlight CSHTML %}

     @(Html.EJ().Ribbon("defaultRibbon")
    .Width("500")
    .ApplicationTab(apptab => {
        apptab.Type(ApplicationTabType.Menu).MenuItemID("Ribbonmenu").MenuSettings(new MenuProperties() {
            OpenOnClick = false
        });
    })
    .RibbonTabs(tab => {
        tab.Id("home").Text("HOME").TabGroups(tabgrp => {
            tabgrp.Text("New").AlignType(RibbonAlignType.Rows).Content(cnt => {
                cnt.ContentGroups(cntgrp => {
                    cntgrp.Id("new").Text("New").ButtonSettings(new ButtonProperties() {
                        ContentType = ContentType.ImageOnly,
                            ImagePosition = ImagePosition.ImageTop,
                            PrefixIcon = "e-Ribbon e-new",
                            Click = "executeAction"
                    }).Add();
                }).ContentDefaults(df => df.Type(RibbonButtonType.Button).Width("60px").Height("70px")).Add();
            }).Add();
        }).Add();
    }))
        <ul id="Ribbonmenu">
        <li>
            <a>FILE</a>
            <ul>
                <li><a>New</a></li>
                <li><a>Open</a></li>
                <li><a>Save</a></li>
                <li><a>Save As</a></li>
                <li><a>Print</a></li>
            </ul>
        </li>
    </ul>
    }
    @section StyleSection{
    <link href="~/Content/ej/Ribbon-css/ej.icons.css" rel="stylesheet" />
    }

{% endhighlight  %}

![](Getting-Started_images/Getting-Started_img3.png)

## Adding Controls to Group

Syncfusion ASP.NET MVC Controls can be added to TabGroup’s content with corresponding `Type` specified like Button, SplitButton, ToggleButton, DropDownList, Gallery, Custom, etc. Default type is `Button`.

{% highlight CSHTML %}

        @(Html.EJ().Ribbon("defaultRibbon")
    .Width("500")
    .ApplicationTab(apptab => {
        apptab.Type(ApplicationTabType.Menu).MenuItemID("Ribbonmenu").MenuSettings(new MenuProperties() {
            OpenOnClick = false
        });
    })
    .RibbonTabs(tab => {
        tab.Id("home").Text("HOME").TabGroups(tabgrp => {
            tabgrp.Text("SplitButton & Dropdown").AlignType(RibbonAlignType.Columns).Content(cnt => {
                cnt.ContentGroups(cntgrp => {
                    cntgrp.Id("paste").Text("Paste").SplitButtonSettings(new SplitButtonProperties() {
                        ContentType = ContentType.ImageOnly,
                            PrefixIcon = "e-Ribbon e-Ribbonpaste",
                            TargetID = "pasteSplit",
                            ArrowPosition = ArrowPosition.Bottom,
                            ButtonMode = ButtonMode.Dropdown
    
                    }).Add();
                }).ContentDefaults(df => df.Type(RibbonButtonType.SplitButton).Width("50px").Height("70px")).Add();
                cnt.ContentGroups(cntgrp => {
                    cntgrp.Id("fontfamily").DropdownSettings(new DropDownListProperties() {
                        DataSource = (IEnumerable < FontFamily > ) ViewBag.datasource,
                            Text = "Segoe UI",
                            Select = "executeAction",
                            Width = "150px"
                    }).Add();
    
                }).ContentDefaults(df => df.Type(RibbonButtonType.DropDownList).Height("28px")).Add();
            }).Add();
        }).Add();
    })))
    <ul id="Ribbonmenu">
        <li>
            <a>FILE</a>
            <ul>
                <li><a>New</a></li>
                <li><a>Open</a></li>
                <li><a>Save</a></li>
                <li><a>Save As</a></li>
                <li><a>Print</a></li>
            </ul>
        </li>
    </ul>
    <ul id="pasteSplit">
        <li><a>Paste</a></li>
    </ul>
    }
    @section StyleSection{
    <link href="~/Content/ej/Ribbon-css/ej.icons.css" rel="stylesheet" />
    <style>
        .e-pastetip {
            background-image: url("../Content/ej/common-images/Ribbon/paste.png");
            background-repeat: no-repeat;
            height: 64px;
            width: 64px;
        }
    </style>
    }

{% endhighlight  %}

![](Getting-Started_images/Getting-Started_img4.png)

