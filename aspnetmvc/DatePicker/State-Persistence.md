---
layout: post
title: State Persistence | DatePicker  | DatePicker | Syncfusion
description: state persistence 
platform: ejmvc
control: DatePicker
documentation: ug
---

# State Persistence 

It Enables or Disables the state maintenance of DatePicker.DatePicker widget can store the model value in the browser cookies and on every time after initial rendering, the control gets the model from the cookie only. Using EnablePersistence property, you can store the model value in cookies. So when any changes are made dynamically then those values are updated in cookie. On refreshing the page, the past state of the DatePicker widget is rendered from cookies. By default “EnablePersistence” property is set as ‘false’ in DatePicker.

The following steps explain you how to enable the state maintenance for DatePicker widget.

1. In the CSHTML page, add the following code to render the DatePicker widget.



{% highlight cshtml %}

@*Add the following code example to the corresponding CSHTML page to render DatePicker widget with state maintenance*@

@Html.EJ().DatePicker("datepicker").EnablePersistence(true)

{% endhighlight %}

