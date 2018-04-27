---
layout: post
title: RTL Support | Button | ASP.NET MVC | Syncfusion
description: rtl support
platform: ejmvc
control: GroupButton
documentation: ug
---

## RTL Support

In some cases, where you want to display the content in Right to Left direction, you can use RTL support by using the EnableRTL property. In RTL mode, when you have more than one content (image/text, image/image) in button, then these content are aligned in right to left format. With this property enabled, the Groupbutton items are rendered in reverse order.

In the view page, add the following Groupbutton to configure the Items with Right to left alignment

{% highlight html %}

<%--Enable the alignment format for GroupButton control as follows--%>

 @Html.EJ().GroupButton("GroupButton").EnableRTL(true).Items(item =>
                   {
                       item.Add().Text("Save");
                       item.Add().Text("Open");
                       item.Add().Text("Delete");
                   })

{% endhighlight %}

Here the items are rendered in the reverse order.

![](RTL-Support_images/rtl.png)


