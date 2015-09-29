---
layout: post
title: Defer-Update
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

_Before Defer Update_


![](Defer-Update_images/Defer-Update_images2.png)

_After Defer Update_


