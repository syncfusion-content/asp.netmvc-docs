---
layout: post
title: Title | PivotChart | ASP.NET MVC | Syncfusion
description: title
platform: ejmvc
control: PivotChart
documentation: ug
---

# Title

## Title Text

By using the `title.Text` property, you can add the title text for PivotChart.

{% highlight CSHTML %}

//Adding Chart title
@Html.EJ().Pivot().PivotChart("PivotChart1").Title(title => title.Text("PivotChart in JS")).Url(Url.Content("/RelationalChartService.svc")).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

![](/js/PivotChart/Title_images/Title_img1.png)

## Title Alignment
By using the `title.TextAlignment` property, you can align the PivotChart controls title text to center, far or near.

{% highlight CSHTML %}

//Change title text alignment
@Html.EJ().Pivot().PivotChart("PivotChart1").Title(title => title.Text("PivotChart in JS").TextAlignment(TextAlignment.Near)
).Url(Url.Content("/RelationalChartService.svc")).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

![](/js/PivotChart/Title_images/Title_img2.png)

## Title Customization

By using the `Title` property, you can add the title text for X-axis and Y-axis. Also title text can be customized by using the `Text` and `Font` properties. On setting `EnableTrim` to true, title text could be trimmed based on its length.

{% highlight CSHTML %}

//Customizing axis title
@Html.EJ().Pivot().PivotChart("PivotChart1").PrimaryXAxis(primaryX => primaryX.Title(title => title.Text("Fiscal Year").Font(font=> font.Size("16px").FontFamily("Segoe UI").FontWeight(ChartFontWeight.Bold).Color("grey")))).Url(Url.Content("/RelationalChartService.svc")).Size(size => size.Height("460px").Width("950px"))

{% endhighlight %}

![](/js/PivotChart/Title_images/Title_img3.png) 

