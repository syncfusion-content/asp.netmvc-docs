---
layout: post
title: DrillOperation | OLAPChart | ASP.NET MVC | Syncfusion
description: drill operation
platform: ejmvc
control: OLAP Chart
documentation: ug
---

# Drill Operation

Drill Operation is a basic feature of OlapChart where the amount of information can be limited for a better view. It allows you to drill down to access the detailed level of data or drill up to display the summarized data by using the context menu present in the OlapChart. 

Drill up is also called as roll up that navigates from more detailed data to less detailed data. That is, by climbing up a concept hierarchy for a dimension. 

Drill down is also called as roll down which is the reverse of drill up. It navigates from less detailed data to more detailed data. That is, by climbing down a concept hierarchy for a dimension.

![](Drill-Operation_images/Drill-Operation_img1.png)

Drill-down operation in OlapChart
{:.caption}

![](Drill-Operation_images/Drill-Operation_img2.png)

Drill-up operation in OlapChart
{:.caption}

DrillSuccess event gets triggered when you right-click on the OlapChart and select any option available in the context menu to perform drill up or drill down operation.

{% highlight CSHTML %}
@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).ClientSideEvents(oEve => {oEve.DrillSuccess("DrillSuccess")}); 



<script type="text/javascript">

    function DrillSuccess(args) {

        alert("Drill Success");

    }

</script>
{% endhighlight %}


