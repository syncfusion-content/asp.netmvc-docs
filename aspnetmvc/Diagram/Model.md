---
layout: post
title: Represent the data to render the Diagram control
description: How to represent the data to render the Diagram control?
platform: ejmvc
control: Diagram
documentation: ug
---

# Model

The Diagram model represents the data to render the Diagram and to manipulate the Diagram elements. The following code illustrates how to define Diagram model.

{% highlight razor %}

  //Creates diagram
  <div>
     @Html.EJ().Diagram("diagram").Width("100%").Height("100%").PageSettings(s=>s.PageWidth(2000).PageHeight(2000))
  </div>
{% endhighlight %}

![](/aspnetmvc/Diagram/Model_images/Model_img1.png)

To explore more model properties, refer to [Model Properties](http://help.syncfusion.com/cr/aspnetmvc/Syncfusion.JavaScript.DataVisualization.Models.DiagramProperties.html "Model Properties").