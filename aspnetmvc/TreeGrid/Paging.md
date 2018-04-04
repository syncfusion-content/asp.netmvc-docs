---
layout: post
title: Paging | TreeGrid | ASP.NET MVC | Syncfusion
description: paging
platform: ejmvc
control: TreeGrid
documentation: ug

---

# Paging

TreeGrid provides support for displaying records in paginated view. Paging can be enabled in TreeGrid by setting the `AllowPaging` property as `true`.

The below code snippet explains enable paging in TreeGrid.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
    .AllowPaging(true)
    )
@(Html.EJ().ScriptManager())

{% endhighlight %}

The output of the TreeGrid with paging enabled is displayed below.

![](Paging_images/Paging_img1.png)

## Paging settings

The paging in TreeGrid can be customized by using the `PageSettings` property.

* **PageSize** - Using this property we can limit the number of records to be displayed per page.
* **PageSizeMode** - By setting this property as `Root` we can limit the number of root nodes or the 0th level records to be displayed per page . 
When the `PageSizeMode` property is set as `Root` the number of records to be displayed per page which is defined in the the `PageSize` property will be considered only for the root nodes or the 0th level records.
* **PageCount** - It is used to display the page number to be displayed in the pager.
* **CurrentPage** - This property is used to set the active page to be displayed initially.
* **TotalRecordsCount** - This property is used to limit the total number of records from the data source to be displayed in TreeGrid.
 The following code example explains the properties in pageSettings. 

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
    .AllowPaging(true)
    .PageSettings(page=>
         {
             page.PageCount(5);
             page.CurrentPage(3);
             page.TotalRecordsCount(50);
             page.PageSizeMode(TreeGridPageSizeMode.All);
             page.PageSize(12);
         })
    )
@(Html.EJ().ScriptManager())

{% endhighlight %}

[Click](http://mvc.syncfusion.com/demos/web/treegrid/treegridpagingapi) here to find our online demo sample for Paging.

## Pager Template

It is possible to customize the default pager in TreeGrid by using the `PageSettings.Template` property.
The below code snippet explains how to customize the default pager with template

{% highlight CSHTML %}

<script type="text/x-jsrender" id="Template">
    <div class="e-pagercontainer">
        <div class="e-first e-icon e-mediaback e-firstpagedisabled e-disable" title="Go to first page"></div><div class="e-prev e-icon e-arrowheadleft-2x e-prevpagedisabled e-disable" style="border-right:none" title="Go to previous page"></div>
    </div>
    <div class="e-pagercontainer e-currentPageContainer" style="border-radius:0px">
        <input id="currentPage" type="text" style="text-align:center; margin:0px;border:none;width:32px;height:23px" />
    </div>
    <div id="totalPages" class="e-pagercontainer" style="margin-left:2px; margin-bottom:5px;border:none">
        <span></span>
    </div>
    <div class="e-pagercontainer">
        <div class="e-nextpage e-icon e-arrowheadright-2x e-default" title="Go to next page"></div><div class="e-lastpage e-icon e-mediaforward e-default" title="Go to last page"></div>
    </div>
</script>

@(Html.EJ().TreeGrid("TreeGridContainer")
    .ClientSideEvents(eve => eve.ActionComplete("complete").Create("create"))
    .AllowPaging(true)
    .PageSettings(pg => pg.Template("#Template"))
    )
@(Html.EJ().ScriptManager())

<script type="text/javascript">

function create(args) {
    //Code for navigating to the page 
    $("#currentPage").keydown(function (e) {
        var obj = $("#TreeGridContainer").data("ejTreeGrid");
        var val = parseInt($("#currentPage").val());
        if (e.keyCode == 13 && !isNaN(val)) {
            if (val > obj.model.pageSettings.totalPages)
                val = obj.model.pageSettings.totalPages;
            if (val <= 0)
                val = 1;
            obj.gotoPage(val);
            return false;
        }
    });
}
function complete(args) {
    $("#totalPages").find('span').text('of ' + this.model.pageSettings.totalPages);

    $(".e-pagercontainer:first").css('border-style', 'none');
    if (args.requestType == 'paging' || args.requestType == 'refresh') {
        if (this.model.pageSettings.currentPage == this.model.pageSettings.totalPages) {
            this.element.find('.e-nextpage').addClass('e-nextpagedisabled').removeClass('e-nextpage');
            this.element.find('.e-lastpage').addClass('e-lastpagedisabled').removeClass('e-lastpage');
        }
        else {
            this.element.find('.e-nextpagedisabled').addClass('e-nextpage').removeClass('e-nextpagedisabled');
            this.element.find('.e-lastpagedisabled').addClass('e-lastpage').removeClass('e-lastpagedisabled');
        }
        if (this.model.pageSettings.currentPage == 1) {
            this.element.find('.e-prevpage').addClass('e-prevpagedisabled e-disable').removeClass('e-prevpage');
            this.element.find('.e-firstpage').addClass('e-firstpagedisabled e-disable').removeClass('e-firstpage');
        }
        else {
            this.element.find('.e-prevpagedisabled').addClass('e-prevpage').removeClass('e-prevpagedisabled e-disable');
            this.element.find('.e-firstpagedisabled').addClass('e-firstpage').removeClass('e-firstpagedisabled e-disable');
        }
        $("#currentPage").val(this.model.pageSettings.currentPage);
    }            
}
</script>

{% endhighlight %}

{% highlight css %}
    #currentPage {
        background-color: white;
    } 

    .darktheme #currentPage {
        background-color: black;
    }

    .e-pagercontainer .e-icon {
        display: inline-block;
        height: 8px;
    }

    .e-pager .e-pagercontainer {
        margin: 0px;
        margin-left: 6px;
    }
{% endhighlight %}

 [Click](http://mvc.syncfusion.com/demos/web/treegrid/treegridpagertemplate) here to find our online sample for Pager Template

The below image displays TreeGrid with paging template.
![](Paging_images/Paging_img2.png)

It is possible to navigate to a specific page with a custom action instead of clicking pager button by using the [`gotoPage`]( /api/js/ejtreegrid#methods:gotopage "gotoPage") method.

The below code snippet explains how to navigate to 3rd page in TreeGrid by using `gotoPage` method

{% highlight CSHTML %}

        var treeObject = $("#TreeGridContainer").data("ejTreeGrid");
        treeObject.gotoPage(3);

{% endhighlight %}

## Paging - Touch Option

With paging and responsive mode enabled in TreeGrid, it is possible to change the current page using swipe action.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")
    .AllowPaging(true)
    .IsResponsive(true)
    )
@(Html.EJ().ScriptManager())

{% endhighlight %}