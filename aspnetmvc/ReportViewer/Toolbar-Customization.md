---
layout: post
title: Toolbar-Customization
description: toolbar customization
platform: ejmvc
control: ReportViewer
documentation: ug
---

## Toolbar Customization

The ReportViewer has an option to show or hide items in the toolbar. To customize the toolbar items, use the ReportViewer’sToolbarSettings property. The toolbar template can also be customized by specifying custom template to ReportViewertoolbar.



[EJMVC]

[CSHTML]

@(

            Html.EJ().ReportViewer("viewer")

.ToolbarSettings(tb=>tb.Items(Syncfusion.JavaScript.ReportViewerEnums.ToolbarItems.All & ~Syncfusion.JavaScript.ReportViewerEnums.ToolbarItems.Parameters

        ))

)





