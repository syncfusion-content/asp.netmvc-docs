---
layout: post
title: behavior settings
description: behavior settings
platform: asp.net mvc
control: Pager
documentation: ug
---

# Behavior Settings

## Page Size List

The **PageSizeList** property of the pager control allows an option to have multiple options of page size values.By defining pageSizeList, a dropdown will render in a pager with given values along with the current pageSize as selected value in droodown. 

Selected value in a dropdown will be set to pageSize api and pager will refersh based on this new pageSize.

{% highlight javascript %}

@{List<int> pageSizeList = new List<int>();
pageSizeList.Add(1);
pageSizeList.Add(2);
pageSizeList.Add(3);
}

<div class="control">
@Html.EJ().Pager("pager").TotalRecordsCount(20).PageSize(1).PageSizeList(pageSizeList).PageCount(3)
</div>

{% endhighlight %}

![](behavior-settings_images\pageSizeList.png)

## Page Size Message

The **PageSizeMessage** property allows to show a message along with the dropdown when **pageSizeList** API of pager control is defined. In the below sample, the **PageSizeMessage** of pager displays the current **pageSize** value of the pager control and will also be updated whenever the pageSize value is changed by selecting a value from the dropdown.

{% highlight javascript %}

<div class="control">
    @Html.EJ().Pager("pager").TotalRecordsCount(20).PageSize(1).PageCount(3).PageSizeMessage("PageSize value: 1").ClientSideEvents(eve => { eve.PageSizeSelected("pageSizeInfo"); 
</div>
<script>
    function pageSizeInfo(e) {
        var a = $("#pager").ejPager("instance");
        a.option("pageSizeMessage", "PageSize value: " + e.pageSize);
    }
</script>

{% endhighlight %}

![](behavior-settings_images\pageSizeMessage.png)

## Responsive

The pager control has responsive support such that control also fit with mobile resolutions. By enabling **isResponsive** API, you can make the pager control responsive. While resizing the browser window, the inner elements in the pager control will adjust automatically to equalize the size. By default, **isResponsive** API value is false. 

{% highlight javascript %}

      @Html.EJ().Pager("pager").PageCount(3).PageSize(1).CurrentPage(1).IsResponsive(true).TotalRecordsCount(20)

{% endhighlight %}

![](behavior-settings_images\pager_Responsive.png)

## Current Page

The **CurrentPage** value of the pager determines which page to be displayed currently. The default value of the **currentPage** API is 1

{% highlight javascript %}

       @Html.EJ().Pager("pager").PageSize(1).PageCount(3).CurrentPage(2).TotalRecordsCount(20)

{% endhighlight %}

![](behavior-settings_images\pager_Currentpage.png)

## Enable/Disable

You can enable or disable pager control by using **Enabled** property. Setting enabled API value as false will disable the user interaction with the pager control.

{% highlight javascript %}

    @Html.EJ().Pager("pager").PageSize(1).PageCount(3).Enabled(false).TotalRecordsCount(20)

{% endhighlight %}

![](behavior-settings_images\pager_EnableDisable.png)