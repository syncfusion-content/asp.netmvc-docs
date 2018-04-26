---
layout: post
title: Getting-Started
description: getting started
platform: ejmvc
control: Pager
documentation: ug
---

# Getting Started

This section briefly explains about how to create a **Pager** control in your application with ASP.NET MVC.

# Adding scroller control in your MVC application

1.	Create an MVC Project and add required assemblies, scripts and styles to it referring MVC-Getting-Started Documentation.
2.	The Essential ASP.NET MVC Pager control based on total records count, page size and page count values. Add the following code example to the corresponding view pages to render the Pager control in your MVC application. 

**TotalRecordsCount:** totalRecordsCount defines the total number of records which is bounded as a single data.

{% highlight javascript %}

        @Html.EJ().Pager("pager").TotalRecordsCount(20)
        
{% endhighlight %}

Run the above sample to get the below output.

![](Getting-Started_images/Getting-Started_img1.png)


 **PageSize:**  pageSize value defines the number of records to be displayed per page. The default value for the pageSize API is 12. 
 
 N> The page count value changes with change in the pageSize value.

  {% highlight javascript %}

        @Html.EJ().Pager("pager").TotalRecordsCount(20).PageSize(1)

{% endhighlight %}

Run the above sample to get the below output.

![](Getting-Started_images/Getting-Started_img2.png)

**PageCount:**  pageCount value defines the number of pages to be displayed in the pager control for navigation. The default value for pageCount is 10 and value will be updated based on totalRecordsCount and pageSize values.

{% highlight javascript %}

    @Html.EJ().Pager("pager").TotalRecordsCount(20).PageSize(1).PageCount(3)

{% endhighlight %}

Run the above sample to get the below output.

![](Getting-Started_images/Getting-Started_img3.png)

