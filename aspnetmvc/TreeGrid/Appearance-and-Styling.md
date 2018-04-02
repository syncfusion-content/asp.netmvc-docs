---
layout: post
title: Appearance and Styling | TreeGrid | ASP.NET MVC | Syncfusion
description: appearance and styling
platform: ejmvc
control: TreeGrid
documentation: ug
---

# Appearance and Styling

The look and feel of the TreeGrid control can be customized by applying themes.

The following are the available themes in TreeGrid control.

1. Flat Azure                      
2. Flat Azure Dark                 
3. Flat Lime                             
4. Flat Lime Dark                
5. Flat Saffron                       
6. Flat Saffron Dark
7. Gradient Azure
8. Gradient Azure Dark
9. Gradient Lime
10. Gradient Lime Dark
11. Gradient Saffron
12. Gradient Saffron Dark
13. Bootstrap

You can apply the theme (Gradient lime) to the TreeGrid control by using the style sheet from the online link as follows.

{% highlight CSHTML %}

<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Getting Started with TreeGrid Control for JavaScript</title>
<!-- style sheet for default theme(gradient lime) -->
<link href=" http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet">
</html>

{% endhighlight %}

The following screenshot shows the TreeGrid control with Gradient-lime theme.

![](Appearance-and-Styling_images/Appearance-and-Styling_img1.png)

## Configuring CSS class

In TreeGrid `CssClass` property is used to apply different custom styles to multiple TreeGrid controls available in the webpage.

The following code example shows how to apply different background color for each TreeGrid control's toolbar element.

{% highlight CSHTML %}
<style>
    .c-class1.e-treegrid .e-toolbar {
        background-color: rgba(169, 45, 45, 0.31);
    }
    .c-class2.e-treegrid .e-toolbar {
        background-color: rgba(0, 128, 0, 0.2);
    }
</style>

@(Html.EJ().TreeGrid("TreeGridContainer")
        .CssClass("c-class1")
)
@(Html.EJ().TreeGrid("TreeGridContainer1")
        .CssClass("c-class2")
)
@(Html.EJ().ScriptManager())

{% endhighlight %}

The below screenshot shows the output of above code example.

![](Appearance-and-Styling_images/Appearance-and-Styling_img2.png)

![](Appearance-and-Styling_images/Appearance-and-Styling_img3.png)

## Customize rows and cells

In TreeGrid, while rendering rows  `RowDataBound` event will be triggered for rows. Similarly `QueryCellInfo` event will be triggered for every cells. Using these events we can customize the tree grid rows and cells at initial load.

The below code example shows how to customize the rows and cells in tree grid.

{% highlight CSHTML %}

@(Html.EJ().TreeGrid("TreeGridContainer")    
    .ClientSideEvents(eve=>
    {
        eve.QueryCellInfo("queryCellInfo");
        eve.RowDataBound("rowDataBound");
    })
)
@(Html.EJ().ScriptManager())
<script type="text/javascript">
function queryCellInfo(args) {
    if (args.column.mappingName == "progress") {
        if (args.data.item["progress"] < 75)
            $(args.cellElement).css("background-color", "rgba(255, 0, 0, 0.12)");
        else
            $(args.cellElement).css("background-color", "rgba(86, 226, 86, 0.25)");
    }
}
function rowDataBound(args) {
    if (args.data.item["taskID"] == 5)
        $(args.rowElement).css("background-color", "rgba(251, 255, 0, 0.24)");
}

</script>

{% endhighlight %}

The below screenshot shows the output of above code example.

![](Appearance-and-Styling_images/Appearance-and-Styling_img4.png)