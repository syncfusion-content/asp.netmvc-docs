---
layout: post
title: Localization| Chart  | ASP.NET MVC | Syncfusion
description: Learn how to localize chart based on a specific culture.
platform: ejmvc
control: Chart
documentation: ug
---

# Localization

EjChart supports localization for its axis labels and tooltip. To render the chart with specific culture you have to refer the corresponding **globalize** culture script and need to specify the culture name in **Locale** property of chart.   

{% highlight cshtml %}

<!--Refer french globalize culture script-->
<script src="../scripts/cultures/globalize.culture.fr-FR.min.js"></script>

   
@(Html.EJ().Chart("chartContainer")

      // ...
      //Render chart in French locale
      .Locale("fr-FR")
      //...
 )


{% endhighlight %}

![](Localization_images/Localization_img1.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/localization) here to view the localization chart online demo sample.


