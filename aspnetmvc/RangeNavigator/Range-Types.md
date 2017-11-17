---
layout: post
title: Range Types | RangeNavigator | ASP.NET MVC | Syncfusion
description: range types
platform: ejmvc
control: RangeNavigator
documentation: ug
---

# Range Types

**RangeNavigator** control is designed to visualize large number of data and navigate to particular data from the large collection at ease. The data for the RangeNavigator is either **Numeric** values or **DateTime** values and the `ValueType` property in RangeNavigator indicates the type of the data that should be passed for the control. By default the `ValueType` of RangeNavigator is DateTime

* Numeric                   
* DateTime

## Numeric Type

RangeNavigator is also used with numeric data and the `ValueType` for this data is **“numeric”** 
{% highlight CSHTML %}
 
@(Html.EJ().RangeNavigator("container")

.ValueType("numeric")

)

{% endhighlight  %}

The following screenshot displays the RangeNavigator with numeric data.



![](Range-Types_images/Range-Types_img1.png)



## DateTime

By default the `ValueType` of the RangeNavigator is **“datetime”** and represents the **DateTime** values. 
{% highlight CSHTML %}
 
@(Html.EJ().RangeNavigator("container")

.ValueType("datetime")

)

{% endhighlight  %}

![](Range-Types_images/Range-Types_img2.png)



## DateTime Intervals

The **DateTime** range type contains an `IntervalType` property that sets the DateTime interval to one of the following:

* Years
* Quarters
* Months
* Weeks
* Days 
* Hours

By default `IntervalType` for higher level labels are **Years** and for lower level labels its **Quarters**.

{% highlight CSHTML %}


@(Html.EJ().RangeNavigator("container")

.LabelSettings(ls=>ls

.HigherLevel(higher=>higher.IntervalType(NavigatorIntervalType.Years))            

.LowerLevel(li=>li.IntervalType(NavigatorIntervalType.Quarters))  

))

{% endhighlight  %}


![](Range-Types_images/Range-Types_img3.png)



