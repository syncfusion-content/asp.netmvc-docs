---
layout: post
title: Resize | Ribbon | ASP.NET MVC | Syncfusion
description: Resize
platform: ejmvc
control: Ribbon
documentation: ug
keywords: resize,ribbon resize
---

# Resize 

Ribbon control dynamically resizes to display possible number of controls in the optimal layout as the application window size changes.

As the window is narrowed, controls in the Ribbon will be combined as group button with dropdown arrow, in which controls can be expanded with dropdown arrow.

## Tablet Layout 

Set `IsResponsive` as true to enable resizing in Ribbon.If client width is above  420px or control content exceeds the page then, the ribbon will render in Tablet mode.

{% highlight CSHTML %}

    @(Html.EJ().Ribbon("defaultRibbon").IsResponsive(true)
        .Width("40%")
        .ApplicationTab(app =>
        {
            app.Type(ApplicationTabType.Menu).MenuItemID("ribbon");
        })
        .RibbonTabs(tab =>
        {
            tab.Id("home").Text("HOME").TabGroups(tabgroup =>
            {
                tabgroup.Text("Clipboard").Content(ctn =>
                {
                    ctn.ContentGroups(ctngrp =>
                    {
                        ctngrp.Id("cut").Text("Cut").Add();
                        ctngrp.Id("copy").Text("Copy").Add();
                    }).ContentDefaults(df => df.Width("40px").Height("70px")).Add();
                }).Add();
                tabgroup.Text("Font").Content(ctn =>
                {
                    ctn.ContentGroups(ctngrp =>
                    {
                        ctngrp.Id("bold").Text("Bold").Add();
                        ctngrp.Id("italic").Text("Italic").Add();
                    }).ContentDefaults(df => df.Width("40px").Height("70px")).Add();
                }).Add();
                tabgroup.Text("Align").Content(ctn =>
                {
                    ctn.ContentGroups(ctngrp =>
                    {
                        ctngrp.Id("left").Text("Left").Add();
                        ctngrp.Id("right").Text("Right").Add();
                    }).ContentDefaults(df => df.Width("40px").Height("70px")).Add();
                }).Add();
            }).Add();
        })
    )
        <ul id="ribbon">
				<li><a>FILE</a>
            <ul>
                <li><a>New</a></li>
                <li><a>Open</a></li>
            </ul>
			    </li>
                </ul>

{% endhighlight %}

![](Resize_images/Resize_img1.png)

## Mobile Layout

If client width is less than 420px, the ribbon will render in mobile mode. In which, you can see that ribbon user interface is customized and redesigned for best view in small screens.
The customized features includes responsive tab & group rendering, backstage, gallery and button controls.

### Responsive Tab and group

Set `IsResponsive` as true to enable responsive mode in Ribbon.
   

{% highlight html %}

    @(Html.EJ().Ribbon("defaultRibbon")
    .IsResponsive(true)
    .RibbonTabs(tab =>
    {
        tab.Id("home").Text("HOME").TabGroups(tabgroup =>
        {
            tabgroup.Text("Font").AlignType(RibbonAlignType.Rows).Content(ctn =>
            { 
                ctn.ContentGroups(ctngrp =>
                {
                    ctngrp.Id("bold").IsMobileOnly(true).Type(RibbonButtonType.ToggleButton).ToggleButtonSettings(new ToggleButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        DefaultText="Bold",
                        ActiveText="Bold",
                        DefaultPrefixIcon = "e-icon e-ribbon e-resbold",
                        ActivePrefixIcon = "e-icon e-ribbon e-resbold",
                    }).Add();
                    ctngrp.Id("italic").IsMobileOnly(true).Type(RibbonButtonType.ToggleButton).ToggleButtonSettings(new ToggleButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        DefaultText = "Italic",
                        ActiveText = "Italic",
                        DefaultPrefixIcon = "e-icon e-ribbon e-resitalic",
                        ActivePrefixIcon = "e-icon e-ribbon e-resitalic",
                    }).Add();
                    ctngrp.Id("underline").IsMobileOnly(true).Type(RibbonButtonType.ToggleButton).ToggleButtonSettings(new ToggleButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        DefaultText = "Underline",
                        ActiveText = "Underline",
                        DefaultPrefixIcon = "e-icon e-ribbon e-resunderline",
                        ActivePrefixIcon = "e-icon e-ribbon e-resunderline",
                    }).Add();
                    ctngrp.Id("strikethrough").IsMobileOnly(true).Type(RibbonButtonType.ToggleButton).ToggleButtonSettings(new ToggleButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        DefaultText = "Strikethrough",
                        ActiveText = "Strikethrough",
                        DefaultPrefixIcon = "e-icon e-ribbon strikethrough",
                        ActivePrefixIcon = "e-icon e-ribbon strikethrough",
                    }).Add();
                    ctngrp.Id("superscript").IsMobileOnly(true).Text("Superscript").ButtonSettings(new ButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        PrefixIcon = "e-icon e-ribbon e-superscripticon",
                    }).Add();
                }).ContentDefaults(df => df.IsBig(false)).Add();
            }).Add();
        }).Add();
        })
    )

{% endhighlight %}

![](Resize_images/responsive1.png)

N> To make the Ribbon control to react as responsive in mobile devices, it is necessary to refer the additional `ej.responsive.css` file in the application.

## Mobile Toolbar Customization

 Set `IsMobileOnly` as true to group control to show the controls 
 in the Mobile Toolbar of the ribbon. For each tab , first row of mobile ribbon will pick and display the controls which is set as `IsMobileOnly` with look adapt to mobile mode.If `IsMobileOnly` property is not defined to any of the control within tab, then by default fist group content will be displayed in first row toolbar.

 To adapt to proper display of controls , following layout will be customized with constants display.

  * First ribbon toolbar and Button controls with min-height. 
  * Drop down control will adapt to full screen width.
  * All button controls icon will be displayed commonly as Top position.
  
  
  {% highlight html %}

     @(Html.EJ().Ribbon("defaultRibbon")
    .IsResponsive(true)
    .RibbonTabs(tab =>
    {
        tab.Id("home").Text("HOME").TabGroups(tabgroup =>
        {
            tabgroup.Text("Font").AlignType(RibbonAlignType.Rows).Content(ctn =>
            { 
                ctn.ContentGroups(ctngrp =>
                {
                    ctngrp.Id("bold").IsMobileOnly(true).Type(RibbonButtonType.ToggleButton).ToggleButtonSettings(new ToggleButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        DefaultText="Bold",
                        ActiveText="Bold",
                        DefaultPrefixIcon = "e-icon e-ribbon e-resbold",
                        ActivePrefixIcon = "e-icon e-ribbon e-resbold",
                    }).Add();
                    ctngrp.Id("italic").IsMobileOnly(true).Type(RibbonButtonType.ToggleButton).ToggleButtonSettings(new ToggleButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        DefaultText = "Italic",
                        ActiveText = "Italic",
                        DefaultPrefixIcon = "e-icon e-ribbon e-resitalic",
                        ActivePrefixIcon = "e-icon e-ribbon e-resitalic",
                    }).Add();
                    ctngrp.Id("underline").IsMobileOnly(true).Type(RibbonButtonType.ToggleButton).ToggleButtonSettings(new ToggleButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        DefaultText = "Underline",
                        ActiveText = "Underline",
                        DefaultPrefixIcon = "e-icon e-ribbon e-resunderline",
                        ActivePrefixIcon = "e-icon e-ribbon e-resunderline",
                    }).Add();
                    ctngrp.Id("strikethrough").Type(RibbonButtonType.ToggleButton).ToggleButtonSettings(new ToggleButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        DefaultText = "Strikethrough",
                        ActiveText = "Strikethrough",
                        DefaultPrefixIcon = "e-icon e-ribbon strikethrough",
                        ActivePrefixIcon = "e-icon e-ribbon strikethrough",
                    }).Add();
                    ctngrp.Id("superscript").Text("Superscript").ButtonSettings(new ButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        PrefixIcon = "e-icon e-ribbon e-superscripticon",
                    }).Add();
                }).ContentDefaults(df => df.IsBig(false)).Add();
            }).Add();
        }).Add();
        })
    )
{% endhighlight %}

![](Resize_images/responsive2.png)
{:caption}
Ribbon Responsive with MobileToolbar 

### Customized Features

The customized layout for  Quick Access Toolbar, backstage, gallery can be seen following screen shots.
 
 ![](Resize_images/responsive3.png)
 {:caption}
Ribbon Responsive with Quick Access Toolbar 
 
 ![](Resize_images/responsive4.png)
 ![](Resize_images/responsive5.png)
 {:caption}
Ribbon Responsive with backstage
 
 ![](Resize_images/responsive6.png)
 {:caption}
Ribbon Responsive with gallery



## Group Button Customization
 
Based on window size, detailed group is shrined into single button and you can expand group items with group button click.

For each group shirked for resizing, Custom Class will be added based on group text.For example, `e-Action` whereas `Action` is group text. Using this custom class, group button can be customized such as to set icons etc.

{% tabs %}

{% highlight CSHTML %}

    @section ControlsSection{
    <div id="resizediv" style="width:100%">
        @(Html.EJ().Ribbon("defaultRibbon").AllowResizing(true)
     .Width("36%")
     .ApplicationTab(app =>
    {
        app.Type(ApplicationTabType.Menu).MenuItemID("ribbon");
    })
     .RibbonTabs(tab =>
    {
        tab.Id("home").Text("HOME").TabGroups(tabgroup =>
        {
            tabgroup.Text("Clipboard").AlignType(RibbonAlignType.Columns).EnableGroupExpander(true).Content(ctn =>
               {
                   ctn.ContentGroups(ctngrp =>
                   {
                       ctngrp.Id("paste").Text("Paste").ToolTip("Paste").ButtonSettings(new ButtonProperties()
                       {
                           ContentType = ContentType.ImageOnly,
                           PrefixIcon = "e-ribbon e-ribbonpaste",
                       }).Add();
                   }).ContentDefaults(df => df.IsBig(true).Width("50px").Height("70px")).Add();
                   ctn.ContentGroups(ctngrp =>
                   {
                       ctngrp.Id("cut").Text("Cut").ToolTip("Cut").ButtonSettings(new ButtonProperties()
                       {
                           ContentType = ContentType.TextAndImage,
                           PrefixIcon = "e-ribbon e-ribboncut",
                       }).Add();
                       ctngrp.Id("copy").Text("Copy").ToolTip("Copy").ButtonSettings(new ButtonProperties()
                       {
                           ContentType = ContentType.TextAndImage,
                           PrefixIcon = "e-ribbon e-ribboncopy",
                       }).Add();
                   }).ContentDefaults(df => df.Type(RibbonButtonType.Button).Width("60px").Height("40px").IsBig(false)).Add();
               }).Add();
            tabgroup.Text("Font").AlignType(RibbonAlignType.Rows).Content(ctn =>
            {
                ctn.ContentGroups(ctngrp =>
                {
                    ctngrp.Id("fontFamily").ToolTip("Font").DropdownSettings(new DropDownListProperties()
                    {
                        DataSource = (IEnumerable<FontFamily>)ViewBag.datasource,
                        Text = "Segoe UI",
                        Width = "150px"
                    }).Add();
                    ctngrp.Id("fontsize").ToolTip("FontSize").DropdownSettings(new DropDownListProperties()
                    {
                        DataSource = (IEnumerable<FontPoint>)ViewBag.datasource1,
                        Text = "1pt",
                        Width = "65px"
                    }).Add();
                }).ContentDefaults(df => df.Type(RibbonButtonType.DropDownList).Height("28px").IsBig(false)).Add();
            }).Add();
            tabgroup.Text("New").AlignType(RibbonAlignType.Rows).Content(ctn =>
            {
                ctn.ContentGroups(ctngrp =>
                {
                    ctngrp.Id("new").Text("New").ToolTip("New").ButtonSettings(new ButtonProperties()
                    {
                        ContentType = ContentType.ImageOnly,
                        ImagePosition = ImagePosition.ImageTop,
                        PrefixIcon = "e-ribbon e-new",
                    }).Add();
                }).ContentDefaults(df => df.Type(RibbonButtonType.Button).Width("60px").Height("40px")).Add();
            }).Add();
            tabgroup.Text("Actions").AlignType(RibbonAlignType.Rows).Content(ctn =>
            {
                ctn.ContentGroups(ctngrp =>
                {
                    ctngrp.Id("undo").Text("Undo").ToolTip("Undo").ButtonSettings(new ButtonProperties()
                    {
                        ContentType = ContentType.TextAndImage,
                        ImagePosition = ImagePosition.ImageTop,
                        PrefixIcon = "e-ribbon e-undo",
                    }).Add();
                    ctngrp.Id("redo").Text("Redo").ToolTip("Redo").ButtonSettings(new ButtonProperties()
                    {
                        ContentType = ContentType.TextAndImage,
                        ImagePosition = ImagePosition.ImageTop,
                        PrefixIcon = "e-ribbon e-redo",
                    }).Add();
                }).ContentDefaults(df => df.Type(RibbonButtonType.Button).Width("40px").Height("70px")).Add();
            }).Add();
        }).Add();
        tab.Id("layout").Text("LAYOUT").TabGroups(tabgroup =>
        {
            tabgroup.Text("Print Layout").AlignType(RibbonAlignType.Rows).Content(ctn =>
            {
                ctn.ContentGroups(ctngrp =>
                {
                    ctngrp.Id("printlayout").Text("Print Layout").ToolTip("Print Layout").ButtonSettings(new ButtonProperties()
                    {
                        ContentType = ContentType.TextAndImage,
                        ImagePosition = ImagePosition.ImageTop,
                        PrefixIcon = "e-ribbon e-printlayout",
                    }).Add();
                }).ContentDefaults(df => df.Type(RibbonButtonType.Button).Width("80px").Height("70px")).Add();
            }).Add();
        }).Add();
    })
        )
    </div>
    <ul id="ribbon">
        <li>
            <a>FILE</a>
            <ul>
                <li><a>New</a></li>
                <li><a>Open</a></li>
            </ul>
        </li>
    </ul>
    }

    @section StyleSection{
    <link href="~/Content/ej/ribbon-css/ej.icons.css" rel="stylesheet" />
    <style type="text/css">
        .e-ribbon .e-New:before, .e-ribbon .e-Actions:before {
            font-family: "ej-ribbonfont";
            font-size: 28px;
            line-height: 35px;
        }
        .e-ribbon .e-New:before {
            content: "\e167";
            text-indent: -1.5px;
        }
        .e-ribbon .e-Actions:before {
            content: "\e184";
            text-indent: 7px;
        }
    </style>
     }
     
{% endhighlight %}

{% highlight C# %}

    public partial class RibbonController: Controller
    {
		List<FontFamily> fontFamily1 = new List<FontFamily>();
        List<FontPoint> fontPoint1 = new List<FontPoint>();
        public ActionResult RibbonFeatures()
        {
            fontFamily1.Add(new FontFamily { text = "Segoe UI" });
            fontFamily1.Add(new FontFamily { text = "Arial" });
            fontFamily1.Add(new FontFamily { text = "Times New Roman" });
            fontFamily1.Add(new FontFamily { text = "Tahoma" });
            fontFamily1.Add(new FontFamily { text = "Helvetica" });
            ViewBag.datasource = fontFamily1;
            fontPoint1.Add(new FontPoint { text = "1pt" });
            fontPoint1.Add(new FontPoint { text = "2pt" });
            fontPoint1.Add(new FontPoint { text = "3pt" });
            fontPoint1.Add(new FontPoint { text = "4pt" });
            fontPoint1.Add(new FontPoint { text = "5pt" });
            ViewBag.datasource1 = fontPoint1;
            return View();
         } 
    }

{% endhighlight %}

{% endtabs %}

![](Resize_images/Resize_img2.png)
