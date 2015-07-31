---
layout: post
title: Look-and-Feel
description: look and feel
platform: ejmvc
control: Dialog
documentation: ug
---

## Look and Feel

You can customize the appearance of Dialog widget using various themes that are available in Essential JavaScript. Applying themes customizes the entire control and its appearances. Refer the following link.
[http://help.syncfusion.com/ug/js/Documents/theming.htm](http://help.syncfusion.com/ug/js/Documents/theming.htm)

CSS Class

The CSS properties can be customized by using CSS Class in the Dialog control. The following steps explains the implementation of CSS Class option in the Dialog widget.

1. In the VIEW page set a helper element with the dialog content for rendering the Dialog control. 





[CSHTML]

// In the CSHTML page add the Dialog widget using helpers and assign the CssClass value from the custom class name.





@{Html.EJ().Dialog("dialog").Title("Syncfusion Dialog").ContentTemplate(@<div>

The Syncfusion Dialog control is rendered.</div>).Width(300).Height("200").

CssClass("customCss").Render();}







2. Customize the CSS class by setting CSS Properties. 



[CSS]



    <style>

        .customCss {            

            border-color: #661e19 !important;

        }



        /*Customize the dialog header*/

        .customCss .e-header {

            background-color: #2c683b;

        }



        /*Customize the dialog content*/

        .customCss .e-dialog, .customCss .e-dialog-scroller {

          color: #b21010;

          background-color: #f6e492;        

         }

    </style>





3. The output for Dialog control after customizing the “CssClass” is as follows.

{{ '![C:/Users/ApoorvahR/Desktop/13.png](Look-and-Feel_images/Look-and-Feel_img1.png)' | markdownify }}
{:.image }


_Figure_ _33__: Dialog with “CssClass"_















