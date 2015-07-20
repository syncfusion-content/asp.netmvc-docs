---
layout: post
title: Legend
description: legend
platform: ejmvc
control: OLAP Chart
documentation: ug
---

## Legend

Legend is a color code that helps to differentiate between chart items. Legend also has labels beside each color to indicate that it applies to information from Series 1, Series 2, and so on.

Legend Symbol

In OlapChart, you can customize the legend symbol with different shapes like rectangle, circle, cross, diamond, pentagon, hexagon, star, ellipse, triangle etc. Default value of legend shape is “Rectangle”.



[MVC]

@Html.EJ().Olap().OlapChart("OlapChart1").Url("../wcf/OlapChartService.svc").Title(title => title.Text("OlapChart in Essential Studio")).Legend(legend => legend.Visible(true).RowCount(3).Shape(ChartShape.Star)) 



{{ '![C:/Users/Tamilarasu .M/Pictures/document/Chart/Legendshape.png](Legend_images/Legend_img1.png)' | markdownify }}
{:.image }


Legend Position

You can customize the legend position in top, bottom, left and right position of the Chart. Default value of legend position is “bottom”. 

[MVC]

@Html.EJ().Olap().OlapChart("OlapChart1").Url("../wcf/OlapChartService.svc").Legend(legend =>legend.Visible(true).RowCount(3).Shape(ChartShape.Star).Position(LegendPosition.Top))

{{ '![C:/Users/Tamilarasu .M/Pictures/document/Chart/Legend position.png](Legend_images/Legend_img2.png)' | markdownify }}
{:.image }


Legend Arrangement

You can align the legend using alignment property of legend. This allows you to align the legend in center, far and near position of Chart Area. The Default value of legend alignment is “Center”.



[MVC] 

@Html.EJ().Olap().OlapChart("OlapChart1").Url("../wcf/OlapChartService.svc").Legend(legend => legend.Visible(true).RowCount(3).Alignment(TextAlignment.Near))



{{ '![C:/Users/Tamilarasu .M/Pictures/document/Chart/legendalignment.png](Legend_images/Legend_img3.png)' | markdownify }}
{:.image }


Legend Style 

You can draw and customize the outline of Chart legend using border property of legend. Default value of legend border color is “Transparent”.



[MVC]

@Html.EJ().Olap().OlapChart("OlapChart1").Url("../wcf/OlapChartService.svc").Legend(legend => legend.Visible(true).RowCount(3).Border(border=>border.Color("red").Width(2)))





{{ '![C:/Users/Tamilarasu .M/Pictures/document/Chart/legend border.png](Legend_images/Legend_img4.png)' | markdownify }}
{:.image }


Legend Item 

Legend item is represented by an icon or image and a text. This gets rendered automatically corresponding to each Series in the OlapChart. You can customize the Legend item.



[MVC] 

@Html.EJ().Olap().OlapChart("OlapChart1").Url("../wcf/OlapChartService.svc").Legend(legend => legend.Visible(true).RowCount(3).ItemStyle(ItemSize =>ItemSize.Border(border =>border.Color("green").Width(0.5))))









{{ '![C:/Users/Tamilarasu .M/Pictures/document/Chart/legenditemborder.png](Legend_images/Legend_img5.png)' | markdownify }}
{:.image }


Legend Text

You can customize the legend text - font family, font style, font weight and size using font property of legend. The following code illustrates this.



[MVC]

@Html.EJ().Olap().OlapChart("OlapChart1").Url("../wcf/OlapChartService.svc").Title(title => title.Text("OlapChart in Essential Studio")).Legend(legend => legend.Visible(true).RowCount(3).Shape(ChartShape.Star))



{{ '![](Legend_images/Legend_img6.png)' | markdownify }}
{:.image }


