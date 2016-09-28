---
layout: post
title: Display Angle Settings| RadialSlider | ASP.NET MVC | Syncfusion
description: Display Angle Settings
platform: ejmvc
control: Radial Slider
documentation: ug
---

# Display Angle Settings

## Start Angle

The **RadialSlider** property **StartAngle** allows you to change the startAngle level of the  **RadialSlider**. By default, the **Radial Slider** StartAngle is set as 0. Refer to the following code example.


{% highlight CSHTML %}

    @Html.EJ().RadialSlider("radialSlider").InnerCircleImageUrl("../images/radialslider/chevron-right.png").StartAngle(20)

{% endhighlight %}

The following screenshot illustrates the output of the above code.

![](Display-Settings_images\Display-Settings_img1.png)


## End Angle

The **RadialSlider** property **EndAngle** allows you  to change the endAngle level of the **RadialSlider**. By default, the **Radial Slider** endAngle is set as 360. Refer to the following code example.

{% highlight CSHTML %}

    @Html.EJ().RadialSlider("radialSlider").InnerCircleImageUrl("../images/radialslider/chevron-right.png").EndAngle(300)

{% endhighlight %}


The following screenshot illustrates the output of the above code.

![](Display-Settings_images\Display-Settings_img2.png)




