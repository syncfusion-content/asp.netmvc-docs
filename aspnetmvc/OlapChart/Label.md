---
layout: post
title: Label
description: label
platform: ejmvc
control: OLAP Chart
documentation: ug
---

## Label

Label represents the text on the axis data points in the Chart. Each axis data point are represented by separate label text information in order to provide precise information about each points. Label text is displayed in a customizable format.

Label font and color customization 

Font style and color of the label text is customized with the help of font and color properties within its respective axis.





[MVC]

@Html.EJ().Olap().OlapChart("OlapChart1").Url("../wcf/OlapChartService.svc").PrimaryXAxis(primaryXAxis => primaryXAxis.Font(Font => Font.Color("red").FontWeight(ChartFontWeight.Lighter).Size("14px").Style(ChartFontStyle.Italic).FontFamily("Algerian")).AxisLine(AxisLine => AxisLine.Visible(true)).AxisLine(AxisLine => AxisLine.Offset(1)).AxisLine(AxisLine =>AxisLine.Width(0.5)))





{ ![C:/Users/Tamilarasu .M/Pictures/document/Chart/Label font-color.png](Label_images/Label_img1.png) | markdownify }
{:.image }


Rotating Axis Labels

You can rotate the labels to desired angle. The axis labels are rendered in the degree specified in the label rotation property.



[MVC]

@Html.EJ().Olap().OlapChart("OlapChart1").Url("../wcf/OlapChartService.svc").PrimaryXAxis(primaryXAxis => primaryXAxis.LabelRotation(45))





{ ![C:/Users/Tamilarasu .M/Pictures/document/Chart/lable rotation.png](Label_images/Label_img2.png) | markdownify }
{:.image }


