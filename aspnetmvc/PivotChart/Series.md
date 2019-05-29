---
layout: post
title: Series | PivotChart | ASP.NET MVC | Syncfusion
description: This document illustrates that how to enable series and its customization in ASP.NET MVC PivotChart control
platform: ejmvc
control: PivotChart
documentation: ug
---

# Series

## Series Point customization
By using the `fill` and `border` properties of Chart series, you can customize the PivotChart series color, border color and border width.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/RelationalChartService.svc")).Size(size => size.Height("460px").Width("950px")).ClientSideEvents(
    oEve => { oEve.SeriesRendering("onSeriesRenders"); })
<script>
   function onSeriesRenders(args) {
      this.model.series[0].points[0].fill = "aqua";
      this.model.series[0].points[0].border = {
        color: "black",
         width: 2
      };
   }
</script>

{% endhighlight %}

![Series customization in ASP NET MVC pivot chart control](Series_images/Series_img1.png)