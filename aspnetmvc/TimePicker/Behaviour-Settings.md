---
layout: post
title: Behaviour-Settings
description: behaviour settings
platform: ejmvc
control: TimePicker
documentation: ug
---

# Behaviour Settings

## Set value of the TimePicker widget

You can use Value property to set default time for the TimePicker.

The following steps explains you on how to set the default value of the TimePicker.

1. Add the following code to the corresponding view page to render the TimePicker.



{% highlight html %}

@*Add the following code example to the corresponding CSHTML page to render TimePicker widget with given time value*@

@Html.EJ().TimePicker("time").Value("10:10 AM")

{% endhighlight %}


Execute the above code to render the following output.

![](Behaviour-Settings_images/Behaviour-Settings_img1.png)



_Figure_ _1__2: TimePicker default value_

## Enable/Disable TimePicker widget

TimePicker widget provides you an option to enable /disable the widget. You can disable the TimePicker by setting the “Enabled” property value as false.

The following steps explain you to enable/disable property in TimePicker widget.

1. Add the following code to the corresponding view page to render the TimePicker.



{% highlight html %}

@*Add the following code example to the corresponding CSHTML page to render disabled TimePicker widget*@

@Html.EJ().TimePicker("time").Enabled(false)

{% endhighlight %}

_Figure 10: Disabled TimePicker widget_

![](Behaviour-Settings_images/Behaviour-Settings_img2.png)

Execute the above code to render the following output.



## Restrict editing

TimePicker widget provides ReadOnly property to disable editing in the control. Therefore you can only read the value set to TimePicker and cannot modify it. The Value property allows you to set the default value for TimePicker widget when it is created.

### Configure TimePicker textbox to restrict editing

The following steps allows you to disable editing value in TimePicker.

1. Add the following code to the corresponding view page to render the TimePicker.



{% highlight html %}

@*Add the following code example to the corresponding CSHTML page to render TimePicker widget*@

@Html.EJ().TimePicker("time").ReadOnly(true)

{% endhighlight %}

The following screenshot illustrates a TimePicker textbox configured to restrict editing.



![](Behaviour-Settings_images/Behaviour-Settings_img3.png)' 



_Figure_ _1__1: TimePicker with PopUp button and enable ReadOnly property_

## Rounded Corner

You can customize the shape of the TimePicker widget from regular rectangular shape to rounded rectangle shape using ShowRoundedCorner property that is set to false by default.

Configure Rounded corner to TimePicker Text box

The following steps explain you to change the edges of the textbox to rounded corner.

1. Add the following code to the corresponding view page to render the TimePicker.



{% highlight html %}

@*Add the following code example to the corresponding CSHTML page to render TimePicker widget with rounded corner*@

@Html.EJ().TimePicker("time").ShowRoundedCorner(true)

{% endhighlight %}

The following screenshot illustrates a TimePicker when ShowRoundedCorner is set to “true”.

![](Behaviour-Settings_images/Behaviour-Settings_img4.png)



_Figure_ _1__2: Rounded corner of_ _TimePicker_ _Textbox_

## Scaling

TimePicker widget provides you options to change its height, width and also to change popup height and width.

### Change TimePicker widget Height and Width

You can use Height and Width property to customize TimePicker width and height.

1. Add the following code to the corresponding view page to render the TimePicker.



{% highlight html %}

@*Add the following code example to the corresponding CSHTML page to render TimePicker widget with specified height and width*@

@Html.EJ().TimePicker("time").Height("50px").Width("150px")

{% endhighlight %}

Execute the above code to render the following output.

![](Behaviour-Settings_images/Behaviour-Settings_img5.png)



_Figure_ _1__3: Changing Width and Height of the TimePicker._

### Changing TimePicker PopupHeight and PopupWidth

You can use PopupHeight and PopupWidth property to customize TimePicker width and height.

1. Add the following code to the corresponding view page to render the TimePicker.



{% highlight html %}

@*Add the following code example to the corresponding CSHTML page to render TimePicker widget with specified popup height and width*@

@Html.EJ().TimePicker("time").PopupHeight("170px").PopupWidth("150px")
{% endhighlight %}


Execute the above code to render the following output.

![](Behaviour-Settings_images/Behaviour-Settings_img6.png)



_Figure_ _1__4: Changing popup height and width_

## State persistence

TimePicker widget provide options to maintain the selected value after you refresh the page by using EnablePersistence property.

### Steps to use State persistence of the TimePicker

The following steps explains you to use EnablePersistence property.

1. Add the following code to the corresponding view page to render the TimePicker.

{% highlight html %}

@*Add the following code example to the corresponding CSHTML page to render TimePicker widget*@

@Html.EJ().TimePicker("time").Value("10:10 AM").EnablePersistence(true)
{% endhighlight %}

## Strict mode of the TimePicker

TimePicker widget provides you an option to set default value when there is no default value between MinTime and MaxTime by using EnableStrictMode property.  

### Steps to use EnableStrictMode property

The following steps explains you to use EnableStrictMode property.

1. Add the following code to the corresponding view page to render the TimePicker.


{% highlight html %}

@*Add the following code example to the corresponding CSHTML page to render TimePicker widget with specifies min and max time*@

@Html.EJ().TimePicker("time").Value("09:00 AM").MinTime("10:00 AM").MaxTime("09:00 PM").EnableStrictMode(true) 

{% endhighlight %}

Execute the above code to render the following output.

![](Behaviour-Settings_images/Behaviour-Settings_img7.png)



_Figure_ _1__5: Using EnableStrictMode property_

## Interval

TimePicker widget provides you an option to change the interval of the hour, minute and seconds. 

### Steps to change the Time interval of the TimePicker control

The following steps explains you to change the Time Interval of the TimePicker.

1. Add the following code to the corresponding view page to render the TimePicker.



{% highlight html %}

@*Add the following code example to the corresponding CSHTML page to render TimePicker widget*@

@Html.EJ().TimePicker("time").TimeFormat("hh:mm:ss tt").HourInterval(2).MinutesInterval(60).SecondsInterval(20)


{% endhighlight %}
