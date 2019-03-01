---
layout: post
title: How to - Tab control for Syncfusion ASP.NET MVC
description: How To Section in tab control for Syncfusion ASP.NET MVC
platform: ejmvc
control: Tab
documentation: ug
---

# How To

## Add a tab item dynamically based on condition

To add tab item dynamically based on condition, we can use the conditional operators to check and add the items within the items property. Refer to the following code.

{% tabs %}

    {% highlight html %}

        @{Html.EJ().Tab("defaultTabs").Items(data =>
        {
            data.Add().ID("reviews").Text("Reviews").ContentTemplate(@<div>@{ Html.RenderPartial("_ReviewList"); }</div>);
            if (user == "admin") { // check the condition to load the item in tab
                    data.Add().ID("calendar").Text("Calendar").ContentTemplate(@<div> @{ Html.RenderPartial("_Calendar"); }</div>);
            }
        }).ShowRoundedCorner(true).Render();}
       
    {% endhighlight %}

{% endtabs %}

In the above code, based on the “user” the second tab will be displayed.

[Sample](http://www.syncfusion.com/downloads/support/directtrac/162785/ze/DropdownCascading_(5)696317518)