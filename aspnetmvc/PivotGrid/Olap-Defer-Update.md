---
layout: post
title: Defer Update | PivotGrid | ASP.NET MVC | Syncfusion
description: defer update
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Defer Update

I> This feature is applicable for OLAP datasource only at Server Mode.

Defer Update support allows you to refresh the control only on-demand and not during every UI interaction.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("/OLAPService")).ClientSideEvents(events => events.AfterServiceInvoke("OnAfterServiceInvoke"))

@Html.EJ().Pivot().PivotSchemaDesigner("PivotSchemaDesigner").Layout(PivotSchemaDesignerLayout.Excel)

<script type="text/javascript">
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
</script>

{% endhighlight %}


![Defer update in ASP NET MVC pivot grid OLAP server mode](Defer-Update_images/Defer-Update_images1.png)

