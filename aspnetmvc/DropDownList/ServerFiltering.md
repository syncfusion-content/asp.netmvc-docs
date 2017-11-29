---
layout: post
title: Server Filtering in the DropDownList control for Syncfusion ASP.NET MVC
description: Description about server filtering in the DropDownList control for Syncfusion ASP.NET MVC
platform: mvc
control: DropDownList
documentation: ug
keywords: DropDownList, dropdown, Filtering, Server Filtering
---

# Server Filtering

Server filtering for displaying only a fixed amount of dataset from the whole dataset. In general, DropDownList displays just the data returned from the server. This feature is convenient for you to apply when the user does not want to see the whole dataset in the popup wrapper.
EnableServerFiltering If set to true, the filtering operations performed in the remote service and returns the result.

{% highlight html %}
     <div class="ctrllabel">Select a Company Name</div>
    @(Html.EJ().DropDownList("ContactName")
                .Datasource(ds => ds.URL("http://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Customers").CrossDomain(true))
        .DropDownListFields(f => f.Text("ContactName").Value("ContactName"))
        .Width("100%")
        .EnableFilterSearch(true)
        .EnableServerFiltering(true)
        .WatermarkText("Select a Contact Name")
    )

{% endhighlight %}

![](ServerFiltering_images/ServerFiltering_image2.png)

This sample raises the query on Customer service. Returns ContactName records for customers with ContactName containing the string “d”.

![](ServerFiltering_images/ServerFiltering_image1.png)

