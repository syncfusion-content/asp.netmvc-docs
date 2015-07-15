---
layout: post
title: Look-and-Feel
description: look and feel
platform: ejmvc
control: RichTextEditor
documentation: ug
---

## Look and Feel

RTE control supports a rich appearance. This control consist of six flat themes and six gradient themes. To use these twelve themes, you can refer to the themes files in HTML. 

You need two style sheets to apply styles to RTE control; ej.widgets.core.min.css and ej.theme.min.css. If you use ej.widgets.all.min.css, then you do not need to use ej.widgets.core.min.css and ej.theme.min.css because ej.widgets.all.min.css is a combination of these two.

The core style sheet applies styles related to positioning and size, but are not related to the color scheme and are always required for the control to look right and function properly. The theme style sheet applies theme-specific styles, like colors and backgrounds.

The following is the list of the twelve themes supported by RTE. 

* default-theme
* flat-azure-dark
* flat-lime
* flat-lime-dark
* flat-saffron
* flat-saffron-dark
* gradient-azure
* gradient-azure-dark
* gradient-lime
* gradient-lime-dark
* gradient-saffron
* gradient-saffron-dark
1. Add the following code in your CSHTML page to initialize the RTE with gradient-saffron-dark theme.



[_cshtml]

@*Add the following code in your view page.*@

@{Html.EJ().RTE("rteSample").Width("850px").ContentTemplate(@&lt;p&gt;&lt;/p&gt;).Render(); }



The following screenshot displays the output.

{ ![](Look-and-Feel_images/Look-and-Feel_img1.png) | markdownify }
{:.image }


Css Class

RTE control also allows you to customize its appearance by using the user-defined CSS and custom skin options for colors and backgrounds. To apply custom themes, use this cssClass property . cssClass property sets the root class for RTE theme.

You can override the existing styles under the theme style sheet by using this property. The theme style sheet applies theme-specific styles like colors and backgrounds. In the following example, the value of cssClass property is set as “light-Pink”. ”[light-Pink](http://www.w3schools.com/tags/ref_color_tryit.asp?color=DeepPink)” is added as the root class to RTE control at runtime. From this root class, you can customize the RTE control theme.

1. Add the following code in your CSHTML page.



[_cshtml]

@*Add the following code in your view page to initialize the RTE.*@

@{Html.EJ().RTE("rteSample").Width("850px").ContentTemplate(@&lt;p&gt;&lt;/p&gt;).CssClass("light-Pink").Render(); }





In the following style sheet, the active theme style sheet file has been overridden by using the root class “light-Pink”.

2. Add the following styles in your styles section.



[Style]

    .light-Pink .e-toolbar {

        color: black;

    }

    .light-Pink .e-toolbarspan {

        background-color: #E9A1CE;

    }

    .light-Pink .e-toolbar .e-active {

        background-color: #4C0F2E;

    }

    .light-Pink .editarea {

        background-color: pink;

    }



The following screenshot displays the output.

{ ![](Look-and-Feel_images/Look-and-Feel_img2.png) | markdownify }
{:.image }




