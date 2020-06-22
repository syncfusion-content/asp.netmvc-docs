---
layout: post
title: DataLabel in ASP.NET MVC SunburstChart widget | Syncfusion
description: You can learn here about Data Label support in Syncfusion ASP.NET MVC SunburstChart control and more details.
platform: ejmvc
control: SunburstChart
documentation: ug
---

# Data Label in ASP.NET MVC SunburstChart 

Sunburst data labels are used to display the data related to the segment. It helps to provide the information about the data points to the users.
You can enable or disable the data labels by setting the visible property of the **DataLabelSettings** to true as shown in the below code

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     //...Palette colors
    .DataLabelSettings(dt => dt.Visible(true))
      //...
 )

{% endhighlight %}

![Visual representation of Data Label using SunburstChart in ASP.NET MVC](DataLabel_images/DataLabel_img1.png)

## Label Overflow mode

When you represent huge data with data labels, they may intersect each other. You can avoid this using the *SunburstLabelOverflowMode* property.

The following properties are used to avoid the overlapping.
*	Trim – To trim the large data labels.
*	Hide – To hide the overlapped data labels.
The following code shows how to set Hide and Trim mode.

{% highlight cshtml %}
@(Html.EJ().SunburstChart("chartContainer")

     //.
    .DataLabelSettings(dt => dt.Visible(true).SunburstLabelOverflowMode(SunburstLabelOverflowMode.Hide))
      //...
 )

 {% endhighlight %}

![Label Overflow mode - Trim using SunburstChart in ASP.NET MVC](DataLabel_images/DataLabel_img2.png) 

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     //.
    .DataLabelSettings(dt => dt.Visible(true).SunburstLabelOverflowMode(SunburstLabelOverflowMode.Trim))
      //...
 )

 {% endhighlight %}

![Label Overflow mode - Hide using SunburstChart in ASP.NET MVC](DataLabel_images/DataLabel_img3.png)

## Label Rotation Mode
You can rotate the data label by using *SunburstLabelRotationMode* property. By default, the labelRotationMode is set as **angle**. 

The following code shows how to set labelRotationMode as normal and angle.

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     //.
    .DataLabelSettings(dt => dt.Visible(true).SunburstLabelRotationMode(SunburstLabelRotationMode.Normal)
      //...
 )

 {% endhighlight %}

![Label Rotation Mode - Normal using SunburstChart in ASP.NET MVC](DataLabel_images/DataLabel_img4.png)

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     //.
    .DataLabelSettings(dt => dt.Visible(true).SunburstLabelRotationMode(SunburstLabelRotationMode.Angle)
      //...
 )

{% endhighlight %}

![Label Rotation Mode - Angle using SunburstChart in ASP.NET MVC](DataLabel_images/DataLabel_img5.png)
 
## Customizing the data labels

You can customize the appearance of the data point using the `Font` property.

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     //.
    .DataLabelSettings(dt => dt.Visible(true).Font(font=>font.Color("Black").Font-Weight("Bold").Size("15px")))
      //...
 )


{% endhighlight %}

![Customizing the data labels using SunburstChart in ASP.NET MVC](DataLabel_images/DataLabel_img6.png)
