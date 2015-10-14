---
layout: post
title: RTL Support | Dialog | ASP.NET MVC | Syncfusion
description: rtl support
platform: ejmvc
control: Dialog
documentation: ug
---

# RTL Support

The Dialog supports Right-To-Left feature. The alignment of Dialog content can be changed from Left-To-Right into Right-To-Left.

## Enable RTL Support

The following steps explain enabling the right-to-left property for Dialog control.

1. In the VIEW page set a helper element with dialog content for rendering the Dialog control. 

   ~~~ cshtml
   
	// In the CSHTML page add the Dialog widget using helpers and set EnableRTL to ‘true’. 



	@{Html.EJ().Dialog("rtldialog").Title("WinRT").ContentTemplate(@<div>

	Essential Studio for WinRT contains all the controls you need to build line-of-business tablet applications <span>including grid, chart, map, tree map, SSRS report viewer, rich-text editor, pdf viewer, gauges, barcode, editors, and much more.</span>

	It also includes a unique set of controls for reading and writing Excel, Word, and PDF documents in Windows store apps.</div>).Width(550).EnableRTL(true).Render();}

   ~~~
   





2. The output for Dialog when EnabelRTL is “True” is as follows.

   ![](RTL-Support_images/RTL-Support_img1.png)

	Dialog with “EnableRTL"
    {:.caption}
