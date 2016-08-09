---
layout: post
title: Defer Update | OLAPClient | ASP.NET MVC | Syncfusion
description: defer update
platform: ejmvc
control: OLAPClient
documentation: ug
---

# Defer Update

Defer Update support allows the user to refresh the control on-demand and not during every user interaction. To enable this functionality, set the `EnableDeferUpdate` property to true. By default, the value is set to false.
{% highlight C# %}

    @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("/OlapClient")).Title("OLAP Browser").EnableDeferUpdate(true)

{% endhighlight %}

After enabling this property, an icon for Defer Update will appear inside the toolbar.

![](Defer-Update_images/deferupdatebefore.png)

On clicking the icon, after making the necessary UI interactions, the PivotGrid and OlapChart controls will be updated according to the OlapReport available at that instant.

![](Defer-Update_images/deferupdateafter.png)
