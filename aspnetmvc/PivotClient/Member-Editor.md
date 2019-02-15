---
layout: post
title: Member Editor | PivotClient | ASP.NET MVC | Syncfusion
description: Member editor in pivot client control
platform: ejmvc
control: PivotClient
documentation: ug
---

# Member Editor

Member editor is a dialog that displays the members of the current field in a tree view structure, which can be opened by clicking the pivot button available in the axis elements. It helps to search, filter, and sort the field members available in the pivot client control.

![Member editor in ASP NET MVC pivot client control](Member_Editor_images/member_editor.png)

## Member editor - Paging

Member editor paging helps to improve the rendering performance of the dialog by dividing large amount of data into sections and displaying them.

You can enable member editor paging and set member editor page size in PivotClient control by setting the [`EnableMemberEditorPaging`](/js/api/ejpivotclient#members:enableMemberEditorPaging) and [`MemberEditorPageSize`](/js/api/ejpivotclient#members:memberEditorPageSize) properties.


{% highlight CSHTML %}

@Html.EJ().Pivot().PivotClient("PivotClient1").EnableMemberEditorPaging(true).MemberEditorPageSize(100)

{% endhighlight %}

Following are the navigation option available in Member Editor Pager.
* Move First - Navigates to the first page.
* Move Previous - Navigates to the previous page from the current page.
* Move Next - Navigates to the next page from the current page.
* Move Last - Navigates to the last page.
* Numeric Box - Navigates to the desired page by entering an appropriate page number in numeric value.


![Member editor paging in ASP NET MVC pivot client control](Member_Editor_images/member_editor_paging.png)

## Member editor - Sorting

The sorting support in member editor helps you to sort the field members either in ascending or descending order.

You can enable the member editor sorting in the pivot grid control by setting the [`EnableMemberEditorSorting`] property.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotClient("PivotClient1").EnableMemberEditorSorting(true)

{% endhighlight %}

![Member editor sorting with ascending order in ASP NET MVC pivot client control](Member_Editor_images/member_editor_sorting_ascending.png)

![Member editor sorting with descending order in ASP NET MVC pivot client control](Member_Editor_images/member_editor_sorting_descending.png)