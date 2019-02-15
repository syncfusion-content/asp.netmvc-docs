---
layout: post
title: Member Editor | PivotGrid | ASP.NET MVC | Syncfusion
description: Member editor in pivot grid control
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Member Editor

Member editor is a dialog that displays the members of the current field in a tree view structure, which can be opened by clicking the filter icon available in the grouping bar. It helps to search, filter, and sort the field members available in the pivot grid control.

![Member editor in ASP NET MVC pivot grid control](Member_Editor_images/member_editor.png)

## Member editor - Paging

Member editor paging helps to improve the rendering performance of the dialog by dividing large amount of data into sections and displaying them.

You can enable member editor paging and set member editor page size in PivotGrid control by setting the `EnableMemberEditorPaging` and `MemberEditorPageSize` properties.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableMemberEditorPaging(true).MemberEditorPageSize(100)

{% endhighlight %}

Following are the navigation option available in Member Editor Pager.
* Move First - Navigates to the first page.
* Move Previous - Navigates to the previous page from the current page.
* Move Next - Navigates to the next page from the current page.
* Move Last - Navigates to the last page.
* Numeric Box - Navigates to the desired page by entering an appropriate page number in numeric value.


![Paging support in member editor of ASP NET MVC pivot grid control](Member_Editor_images/member_editor_paging.png)

## Member editor - Sorting

The sorting support in member editor helps you to sort the field members either in ascending or descending order.

You can enable the member editor sorting in the pivot grid control by setting the `EnableMemberEditorSorting` property.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").EnableMemberEditorSorting(true)

{% endhighlight %}

![Ascending order of field items in ASP NET MVC pivot grid control](Member_Editor_images/member_editor_sorting_ascending.png)

![Descending order of field items in ASP NET MVC pivot grid control](Member_Editor_images/member_editor_sorting_descending.png)