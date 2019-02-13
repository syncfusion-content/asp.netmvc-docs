---
layout: post
title: Defer Update | PivotClient | ASP.NET MVC | Syncfusion
description: defer update
platform: ejmvc
control: PivotClient
documentation: ug
---

# Defer Update

I> This feature is applicable only for OLAP data source bound from server-side.

Defer Update support allows the user to refresh the control on-demand and not during every user interaction. To enable this functionality, set the `EnableDeferUpdate` property to true. By default, the value is set to false.

{% highlight cshtml%}

    @Html.EJ().Pivot().PivotClient("PivotClient1").Url(Url.Content("/OlapClient")).Title("Olap Browser").EnableDeferUpdate(true)

{% endhighlight %}

After enabling this property, an icon for Defer Update will appear inside the toolbar.

![Defer update in ASP NET MVC pivot client control](Defer-Update_images/deferupdatebefore.png)

On clicking the icon, after making the necessary UI interactions, the PivotGrid and PivotChart controls will be updated according to the OlapReport available at that instant.

![Defer update view in ASP NET MVC pivot client control](Defer-Update_images/deferupdateafter.png)
