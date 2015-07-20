---
layout: post
title: Tooltip
description: tooltip
platform: ejmvc
control: OLAP Gauge
documentation: ug
---

## Tooltip

Tooltip provides the information about the OlapGauge when you move the mouse pointer over the control. You can enable it using “showtooltip”property.





[MVC]

@Html.EJ().Olap().OlapGauge("OlapGauge1").Url("../wcf/OlapGaugeService.svc").BackgroundColor("transparent").EnableTooltip(true).Scales(scale =>

{

    scale.ShowRanges(true).Radius(150).ShowScaleBar(true).Size(1).Border(bor=>bor.Width(0.5)).ShowIndicators(false).ShowLabels(true).Pointers(pointer =>

        {

            pointer.Type(PointerType.Needle).ShowBackNeedle(true).BackNeedleLength(20).Length(120).NeedleType(NeedleType.Rectangle).Width(7).Add();

            pointer.Type(PointerType.Marker).DistanceFromScale(5).Placement(PointerPlacement.Center).BackgroundColor("#29A4D9").Length(25).Width(15).MarkerType(MarkerType.Diamond).Add();

        }).

    Ticks(ticks =>

    {

        ticks.Type(CircularTickTypes.Major).DistanceFromScale(15).Height(16).Width(1).Color("#8c8c8c").Add();

        ticks.Type(CircularTickTypes.Minor).Height(6).Width(1).DistanceFromScale(2).Color("#8c8c8c").Add();

    })

    .Labels(labels => { labels.Color("#8c8c8c").Add(); })

    .Ranges(ranges =>

    {

        ranges.DistanceFromScale(-10).BackgroundColor("black").Border(bor=> bor.Color("red")).Add();

        ranges.DistanceFromScale(-10).Add();

    })

    .CustomLabels(customLabel =>

    {

        customLabel.Position(location => location.X(180).Y(290)).Font(font => font.Size("10px").FontFamily("Segoe UI").FontStyle("Normal")).Color("#666666").Add();

        customLabel.Position(location => location.X(180).Y(320)).Font(font => font.Size("10px").FontFamily("Segoe UI").FontStyle("Normal")).Color("#666666").Add();

        customLabel.Position(location => location.X(180).Y(150)).Font(font => font.Size("12px").FontFamily("Segoe UI").FontStyle("Normal")).Color("#666666").Add();

    }).Add();

})



### Customizing the tooltip using CSS

You can customize the Tooltip by overriding the existing style attributes and referring it in web page.



[CSS]

<style>

.e-olapgauge-tooltip {

  background-color: aqua !important;

  border: 2px solid red !important;

  color: black !important;

  border-radius: 18px!important;

  margin-top: 20px;

  text-align: left;

  font: 12px Segoe UI;

  line-height: 20px;

}

</style>





{{ '![](Tooltip_images/Tooltip_img1.png)' | markdownify }}
{:.image }


