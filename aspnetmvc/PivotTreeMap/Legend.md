---
layout: post
title: Legend | PivotTreeMap | ASP.NET MVC | Syncfusion
description: legend
platform: ejmvc
control: PivotTreeMap
documentation: ug
---

#Legend

##Legend Visibility

The legend shows the value range differences and color occurrence in the respective leaf node while you hover it with the cursor.

N> By default, the legend is visible in PivotTreeMap.

![](Legend_images/Legend_img1.png)

You can disable the legend by setting the property **showLegend** as **false**. The following code example shows how to disable the legend.

{% highlight js %}

@Html.EJ().Pivot().PivotTreeMap("PivotTreeMap1").DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("[Date].[Fiscal]").Add(); }).Columns(columns => { columns.FieldName("[Customer].[Customer Geography]").Add(); }).Values(values => { values.Measures(measures => { measures.FieldName("[Measures].[Customer Count]").Add(); }).Axis(AxisName.Column).Add(); }).Data("http://bi.syncfusion.com/olap/msmdpump.dll").Catalog("Adventure Works DW 2008 SE").Cube("Adventure Works")).ClientSideEvents(oEve => { oEve.RenderSuccess("showLegend"); })
<script type="text/javascript">     
   function showLegend(args) {	
            pivotTreeMap = $("#PivotTreeMap1TreeMapContainer").data("ejTreeMap");
            pivotTreeMap.model.showLegend = false;
            pivotTreeMap.refresh();
   } 
</script>

<! --Tooltip labels can be localized here-->
<script id="tooltipTemplate" type="application/jsrender">
    <div style="background:White; color:black; font-size:12px; font-weight:normal; border: 1px solid #4D4D4D; white-space: nowrap;border-radius: 2px; margin-right: 25px; min-width: 110px;padding-right: 5px; padding-left: 5px; padding-bottom: 2px ;width: auto; height: auto;">
        <div>Measure(s) : {{:~Measures(#data)}}</div><div>Row : {{:~Row(#data)}}</div><div>Column : {{:~Column(#data)}}</div><div>Value : {{:~Value(#data)}}</div>
    </div>
</script>

{% endhighlight %}

![](Legend_images/Legend_img2.png)