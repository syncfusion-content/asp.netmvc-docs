---
layout: post
title: Getting Started | ListView | ASP.NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: ListView
documentation: ug
---

# Getting Started

This section explains briefly on how to create a ListView control in your application.

## Create your first ListView in MVC

The Essential StudioListView widget builds an interactive list view interface. This control allows you to select an item from a list-like interface and provides the infrastructure to display a set of data items in different layouts or views. Lists display data, data navigation, result lists, and data entry.    


![](Getting-Started_images/Getting-Started_img1.png)

List view Control
{:.caption}

The following steps guide you to add a ListView control in a MVC application.

## Create a simple ListView

1. You can create a MVC Project and add necessary Dll’s and Scripts with the help of the given [MVC-Getting Started](http://docs.syncfusion.com/aspnetmvc/listview/getting-started) Documentation.
2. Add the following code example to the corresponding view page for ListView rendering.

{% highlight CSHTML %}

@Html.EJ().ListView("Listview")

.Items(items=>

    {

        items.Add().Text("Inbox");

        items.Add().Text("VIP");

        items.Add().Text("Drafts");

        items.Add().Text("Sent");

        items.Add().Text("Junk");

        items.Add().Text("Trash");

        items.Add().Text("All mails");

        items.Add().Text("Mail");

   })

{% endhighlight %}

Run the above code to render the following output.

![](Getting-Started_images/Getting-Started_img2.png)


## Add header

You can add a header for ListView using ShowHeader property. Refer to the following code example.

{% highlight CSHTML %}

<!—Add Listview control with header -->

@Html.EJ().ListView("Listview").ShowHeader(true).HeaderTitle("Mailbox")

.Items(items=>

    {
        items.Add().Text("Inbox");

        items.Add().Text("VIP");

        items.Add().Text("Drafts");

        items.Add().Text("Sent");

        items.Add().Text("Junk");

        items.Add().Text("Trash");

        items.Add().Text("All mails");

        items.Add().Text("Mail");

   })
   
{% endhighlight %}

Run the above code to render the following output.

![](Getting-Started_images/Getting-Started_img3.png)