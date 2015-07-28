---
layout: post
title: Localization
description: localization
platform: ejmvc
control: TimePicker
documentation: ug
---

# Localization

You can globalize the TimePicker, so that users of different cultures can make use of it and post their content. For your convenience, you can format the TimePicker control to your culture. When your blog is in your culture, the viewers of your culture can understand about your company and its products. You can achieve localization using the “Locale” property. 

TimePicker support all the cultures. Globalize.js is a simple JavaScript library that allows you to use different cultures. Globalize cultures is the open source and you can get all the culture files from [http://cdnjs.com/libraries/globalize/](http://cdnjs.com/libraries/globalize/) link. 

In this example, globalize.min.js file is used that includes all the cultures information. And in this example Spanish culture is used.

## Enabling Localization Support

The following steps explains you on how to enable Locale property for TimePicker.

1. Add the following code to the corresponding view page to render the TimePicker.



{% highlight html %}

@*Add the following code example to the corresponding CSHTML page to render TimePicker widget with Spanish culture*@

@Html.EJ().TimePicker("time").Locale("es-ES")

{% endhighlight %}

Execute the above code to render the following output.

![](Localization_images/Localization_img1.png)


_Figure 9: TimePicker with es-ES Localization_

