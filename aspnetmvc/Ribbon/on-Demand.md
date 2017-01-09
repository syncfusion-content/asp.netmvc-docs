---
layout: post
title: OnDemand | Ribbon | ASP.NET MVC | Syncfusion
description: OnDemand
platform: ejmvc
control: Ribbon
documentation: ug
keywords: EnableOnDemand
---

# Load on Demand

Set `EnableOnDemand` as true to enable load tab and backstage contents dynamically. Loading content on demand improves the initial rendering time of the ribbon by rendering tab and backstage content when tabs and backstage items are clicked.
 
{% highlight CSHTML %}
              
              <div id="newCon">
                    <table>
                        <tr>
                            <td>
                                <button id="btn1" class="e-bsnewbtnstyle">Blank WorkBook</button>
                            </td>
                        </tr>
                    </table>
                </div>
                <div id="accountCon">
                    <div class="e-userDiv">
                        <span>User Information</span>
                        <div>
                            <div class="e-accuser e-newpageicon"></div>
                            <div class="e-userCon">
                                <div>user</div>
                                <div>xyz@syncfusion.com</div>
                            </div>
                        </div>
                    </div>
                    <a href="#">Sign out</a>
                </div>
                
   @(Html.EJ().Ribbon("defaultRibbon")
     .Width("50%")
     .EnableOnDemand(true)
     .ApplicationTab(apptab =>
         {
             apptab.Type(ApplicationTabType.Backstage).BackstageSettings(bsSettings =>
             {
                 bsSettings.Text("FILE").Height("350").Width("100%").HeaderWidth("120").Pages(bsPage =>
                 {
                     bsPage.Id("new").Text("New").ContentID("newCon").Add();
                     bsPage.Id("close").Text("Close").EnableSeparator(true).ItemType(ItemType.Button).Add();
                     bsPage.Id("account").Text("Office Account").ContentID("accountCon").Add();
                 });
             });
        })
     .RibbonTabs(tab =>
       {
        tab.Id("home").Text("HOME").TabGroups(tabgrp =>
        {
           tabgrp.Text("Clipboard").AlignType(RibbonAlignType.Columns).GroupExpanderSettings(grpExp =>
            {
                grpExp.ToolTip("Clipboard");
            }).Content(cnt =>
            {
                cnt.ContentGroups(cntgrp =>
                {
                    cntgrp.Id("paste").Text("Paste").ToolTip("Paste").ButtonSettings(new ButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        PrefixIcon = "e-icon e-ribbon e-ribbonpaste"
                    }).Add();
                }).ContentDefaults(df => df.Type(RibbonButtonType.Button).IsBig(true).Width("50px").Height("70px")).Add();
            }).Add();
           tabgrp.Text("New").AlignType(RibbonAlignType.Rows).Content(cnt =>
           {
               cnt.ContentGroups(cntgrp =>
               {
                   cntgrp.Id("new").Text("New").ToolTip("New").ButtonSettings(new ButtonProperties()
                   {
                       ContentType = ContentType.ImageOnly,
                       ImagePosition = ImagePosition.ImageTop,
                       PrefixIcon = "e-icon e-ribbon e-new"
                   }).Add();
               }).ContentDefaults(df => df.Type(RibbonButtonType.Button).Width("60px").Height("70px")).Add();
           }).Add();
        }).Add();
        tab.Id("layout").Text("LAYOUT").TabGroups(tabgrp =>
        {
            tabgrp.Text("Alignment").AlignType(RibbonAlignType.Rows).Content(cnt =>
            {
                cnt.ContentGroups(cntgrp =>
                {
                    cntgrp.Id("bullet").Text("Bullet Format").ToolTip("Bullets").ButtonSettings(new ButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        PrefixIcon = "e-icon e-ribbon e-bullet"
                    }).Add();
                    cntgrp.Id("number").Text("Number Format").ToolTip("Numbering").EnableSeparator(true).ButtonSettings(new ButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        PrefixIcon = "e-icon e-ribbon e-numbericon"
                    }).Add();
                }).ContentDefaults(df => df.Type(RibbonButtonType.Button).IsBig(false)).Add();
            }).Add();
        }).Add();
        })
      )
    <script>
        $("#btn1").ejButton({
            size: "large",
            height: 200,
            width: 225,
            contentType: "textandimage",
            imagePosition: "imagetop",
            prefixIcon: "e-blank e-infopageicon"
        });
    </script>
    
     <style>
       .e-accuser {
           background-image: url("../Content/ejthemes/common-images/ribbon/User.jpg");
        }
        .e-blank {
           background-image: url("../Content/ejthemes/common-images/ribbon/blank.png");
        }
        .e-infopageicon {
            background-repeat: no-repeat;
            height: 150px;
            width: 198px;
        }
        .e-newpageicon {
            background-repeat: no-repeat;
            height: 42px;
            width: 42px;
        }
        .e-bspagestyle {
            line-height: 0;
            font-size: 30px;
        }
        .e-ribbon .e-ribbonbackstagepage .e-bsnewbtnstyle {
            color: #212121;
            background: #fdfdfd;
            margin: 20px;
        }
    </style>

{% endhighlight %}

![](On_Demand_images/onDemand_img1.png)

# Initially Collapsible

Set `Collapsible` as true to render ribbon control in collapsed state, which results ribbon tabs to render without any content initially.
While using initially collapsible ribbon with `EnableOnDemand` feature improves the performance by reducing initial loading time of ribbon.

{% highlight CSHTML %}
              
              <div id="newCon">
                    <table>
                        <tr>
                            <td>
                                <button id="btn1" class="e-bsnewbtnstyle">Blank WorkBook</button>
                            </td>
                        </tr>
                    </table>
                </div>
                <div id="accountCon">
                    <div class="e-userDiv">
                        <span>User Information</span>
                        <div>
                            <div class="e-accuser e-newpageicon"></div>
                            <div class="e-userCon">
                                <div>user</div>
                                <div>xyz@syncfusion.com</div>
                            </div>
                        </div>
                    </div>
                    <a href="#">Sign out</a>
                </div>
                
   @(Html.EJ().Ribbon("defaultRibbon")
     .Width("50%")
     .EnableOnDemand(true)
     .Collapsible(true)
     .ApplicationTab(apptab =>
         {
             apptab.Type(ApplicationTabType.Backstage).BackstageSettings(bsSettings =>
             {
                 bsSettings.Text("FILE").Height("350").Width("100%").HeaderWidth("120").Pages(bsPage =>
                 {
                     bsPage.Id("new").Text("New").ContentID("newCon").Add();
                     bsPage.Id("close").Text("Close").EnableSeparator(true).ItemType(ItemType.Button).Add();
                     bsPage.Id("account").Text("Office Account").ContentID("accountCon").Add();
                 });
             });
        })
     .RibbonTabs(tab =>
       {
        tab.Id("home").Text("HOME").TabGroups(tabgrp =>
        {
           tabgrp.Text("Clipboard").AlignType(RibbonAlignType.Columns).GroupExpanderSettings(grpExp =>
            {
                grpExp.ToolTip("Clipboard");
            }).Content(cnt =>
            {
                cnt.ContentGroups(cntgrp =>
                {
                    cntgrp.Id("paste").Text("Paste").ToolTip("Paste").ButtonSettings(new ButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        PrefixIcon = "e-icon e-ribbon e-ribbonpaste"
                    }).Add();
                }).ContentDefaults(df => df.Type(RibbonButtonType.Button).IsBig(true).Width("50px").Height("70px")).Add();
            }).Add();
           tabgrp.Text("New").AlignType(RibbonAlignType.Rows).Content(cnt =>
           {
               cnt.ContentGroups(cntgrp =>
               {
                   cntgrp.Id("new").Text("New").ToolTip("New").ButtonSettings(new ButtonProperties()
                   {
                       ContentType = ContentType.ImageOnly,
                       ImagePosition = ImagePosition.ImageTop,
                       PrefixIcon = "e-icon e-ribbon e-new"
                   }).Add();
               }).ContentDefaults(df => df.Type(RibbonButtonType.Button).Width("60px").Height("70px")).Add();
           }).Add();
        }).Add();
        tab.Id("layout").Text("LAYOUT").TabGroups(tabgrp =>
        {
            tabgrp.Text("Alignment").AlignType(RibbonAlignType.Rows).Content(cnt =>
            {
                cnt.ContentGroups(cntgrp =>
                {
                    cntgrp.Id("bullet").Text("Bullet Format").ToolTip("Bullets").ButtonSettings(new ButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        PrefixIcon = "e-icon e-ribbon e-bullet"
                    }).Add();
                    cntgrp.Id("number").Text("Number Format").ToolTip("Numbering").EnableSeparator(true).ButtonSettings(new ButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        PrefixIcon = "e-icon e-ribbon e-numbericon"
                    }).Add();
                }).ContentDefaults(df => df.Type(RibbonButtonType.Button).IsBig(false)).Add();
            }).Add();
        }).Add();
        })
      )
    <script>
        $("#btn1").ejButton({
            size: "large",
            height: 200,
            width: 225,
            contentType: "textandimage",
            imagePosition: "imagetop",
            prefixIcon: "e-blank e-infopageicon"
        });
    </script>
    
     <style>
       .e-accuser {
           background-image: url("../Content/ejthemes/common-images/ribbon/User.jpg");
        }
        .e-blank {
           background-image: url("../Content/ejthemes/common-images/ribbon/blank.png");
        }
        .e-infopageicon {
            background-repeat: no-repeat;
            height: 150px;
            width: 198px;
        }
        .e-newpageicon {
            background-repeat: no-repeat;
            height: 42px;
            width: 42px;
        }
        .e-bspagestyle {
            line-height: 0;
            font-size: 30px;
        }
        .e-ribbon .e-ribbonbackstagepage .e-bsnewbtnstyle {
            color: #212121;
            background: #fdfdfd;
            margin: 20px;
        }
    </style>

{% endhighlight %}

![](On_Demand_images/onDemand_img2.png)