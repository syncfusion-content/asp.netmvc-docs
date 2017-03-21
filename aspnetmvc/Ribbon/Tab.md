---
layout: post
title: Tab | Ribbon | ASP.NET MVC | Syncfusion
description: Tab
platform: ejmvc
control: Ribbon
documentation: ug
---

# Tab

RibbonTabs is a collection of control `TabGroup` which enables you to organize related commands into single view. Tabs can be added to Ribbon using `RibbonTabs` property. `Id` & `Text` properties are used to set unique ID and header text to RibbonTabs.

{% highlight CSHTML %}

      @(Html.EJ().Ribbon("defaultRibbon")
      .Width("500")
      .ApplicationTab(app => {
          app.Type(ApplicationTabType.Menu).MenuItemID("Ribbon").MenuSettings(new MenuProperties() {
              OpenOnClick = false
          });
      })
      .RibbonTabs(tab => {
          tab.Id("home").Text("HOME").TabGroups(tabgroup => {
              tabgroup.Text("Save").AlignType(RibbonAlignType.Rows).Content(ctn => {
                  ctn.ContentGroups(ctngrp => {
                      ctngrp.Id("print").Text("Print").ButtonSettings(new ButtonProperties() {
                          ContentType = ContentType.TextAndImage,
                              ImagePosition = ImagePosition.ImageTop,
                              PrefixIcon = "e-Ribbon e-print"
                      }).Add();
                      ctngrp.Id("save").Text("Save").ButtonSettings(new ButtonProperties() {
                          ContentType = ContentType.TextAndImage,
                              ImagePosition = ImagePosition.ImageTop,
                              PrefixIcon = "e-Ribbon e-save"
                      }).Add();
                  }).ContentDefaults(df => df.Type(RibbonButtonType.Button).Width("50px").Height("70px")).Add();
              }).Add();
          }).Add();
          tab.Id("sendrec").Text("Send/Receive").TabGroups(tabgroup => {
              tabgroup.Text("Send/Receive").Type("custom").ContentID("sendReceive").AlignType(RibbonAlignType.Columns).Content(ctn => {

              }).Add();
          }).Add();
      })
     )
    <div id="sendReceive">
        Send/Receive All Folders
    </div>
    <ul id="Ribbon">
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
     @section StyleSection{
    <link href="~/Content/ej/Ribbon-css/ej.icons.css" rel="stylesheet" />
    }

{% endhighlight  %}

![](Tab_images/Tab_img1.png)
