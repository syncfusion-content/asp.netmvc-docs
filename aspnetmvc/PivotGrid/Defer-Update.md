---
layout: post
title: Defer Update | PivotGrid | ASP.NET MVC | Syncfusion
description: defer update
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Defer Update

Defer update support allows you to refresh the widget only on-demand and not during every user interaction

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("~/wcf/OLAPService.svc")).EnableDeferUpdate(true).ClientSideEvents(events => events.AfterServiceInvoke("OnAfterServiceInvoke"))

@Html.EJ().Pivot().PivotSchemaDesigner("PivotSchemaDesigner").Layout(PivotSchemaDesignerLayout.Excel)

OnAfterServiceInvoke = function(evt) {
    if (evt.action == "initialize") {
        var PivotSchemaDesigner = $("#PivotSchemaDesigner").data('ejPivotSchemaDesigner');
        if (PivotSchemaDesigner.model.pivotControl == null) {
            PivotSchemaDesigner.model.pivotControl = this;
            PivotSchemaDesigner.model.enableWrapper = true;
            PivotSchemaDesigner.model.layout = "excel";
            PivotSchemaDesigner._load();
        }
    }
}

{% endhighlight %}


![](Defer-Update_images/Defer-Update_images1.png)

