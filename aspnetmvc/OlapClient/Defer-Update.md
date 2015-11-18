---
layout: post
title: Defer Update | OLAPClient | ASP.NET MVC | Syncfusion
description: defer update
platform: ejmvc
control: OLAPClient
documentation: ug
---

# Defer Update

Defer Update support allows you to refresh the control only on-demand and not during every UI interaction.  To enable this functionality, set the `enableDeferUpdate` property to "True".

The following code example explains how you can enable the Defer Update in OlapClient.

{% highlight C# %}

    @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/wcf/OlapClientService.svc")).EnableDeferUpdate(true).Title("OLAP Browser"))

{% endhighlight %}


![](Defer-Update_images/Defer-Update_images1.png)

Before Defer Update
{:.caption}

![](Defer-Update_images/Defer-Update_images2.png)

After Defer Update
{:.caption}

