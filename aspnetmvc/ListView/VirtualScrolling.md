---
layout: post
title: Virtual Scrolling | ListView | ASP.NET MVC | Syncfusion
description: virtual scrolling
platform: ejmvc
control: ListView
documentation: ug
---

# Virtual Scrolling

   We can load large data on demand using "AllowVirtualScrolling" property. By default, "AllowVirtualScrolling" set as boolean value of **"false"**. When it is set true, list items will be loaded on every scroll action. The number of items to be loaded per request can be specified using the “ItemRequestCount” property.By default “ItemRequestCount” value will be 5. We have provided two type of option for virtualScrolling,

## Normal Mode
    This mode allows you to load the list view data while scrolling i.e. each time the scroll bar is scrolled, it will send request to the server to load the data.

## Continuous Mode
    This mode allows you to load the list view data when the scrollbar reaches the end point. In this mode, we can specify the number of items to be loaded per request.

Please refer the following code examples.

{% highlight CSHTML %}

    @Html.EJ().ListView("locallistview").Width(400).Height(300).DataSource(ds => ds.URL("http://js.syncfusion.com/ejservices/Wcf/Northwind.svc/").CrossDomain(true)).Query("ej.Query().from('Customers')").FieldSettings(f => f.Text("CustomerID")).AllowVirtualScrolling(true).VirtualScrollMode(VirtualScrollMode.Continuous)

{% endhighlight %}
