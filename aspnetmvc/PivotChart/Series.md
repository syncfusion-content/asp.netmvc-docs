---
layout: post
title: Series | OLAPChart | ASP.NET MVC | Syncfusion
description: series
platform: ejmvc
control: OLAPChart
documentation: ug
---

#Series

##Series Point customization
By using the `Fill` and `Border` properties of Chart series, you can customize the OlapChart series color, border color and border width.
 
{% highlight CSHTML %}

@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px")).ClientSideEvents(
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

![](Series_images/Series_img1.png)