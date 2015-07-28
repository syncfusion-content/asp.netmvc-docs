---
layout: post
title: Title
description: title
platform: ejmvc
control: OLAP Chart
documentation: ug
---

# Title

Title is the area on top of the Chart control that displays the text explaining the OlapChart data. Title text is displayed in a customizable format.  

## Setting value to Chart Title

Title property allows you to set the default title for a Chart as follows. 

{% highlight html %}

[MVC]

@Html.EJ().Olap().OlapChart("OlapChart1").Url("../wcf/OlapChartService.svc").Title(title => title.Text("OLAP Chart in Essential Studio"))

{% endhighlight  %}



![C:/Users/Tamilarasu .M/Pictures/document/Chart/ChartSettingtitile.png](Title_images/Title_img1.png)



## Title Text Customization 

You can customize the title text font using title.font property.

{% highlight html %}

[MVC]

@Html.EJ().Olap().OlapChart("OlapChart1").Url("../wcf/OlapChartService.svc").Title(title => title.Text("OlapChart in Essential Studio")).ClientSideEvents(oEve => { oEve.Load("load"); })

{% endhighlight %}
{% highlight js %}
<script type="text/javascript">

    function load(args) {

        this.model.title.font.size = "30px",

        this.model.title.font.fontStyle = "italic",

        this.model.title.font.fontWeight = "bold"

    }

</script>


{% endhighlight  %}


![C:/Users/Tamilarasu .M/Pictures/document/Chart/chartTitle.png](Title_images/Title_img2.png)



