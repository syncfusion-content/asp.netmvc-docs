---
layout: post
title: Highlight
description: What are the different modes of highlight present in the Sunburst Chart
platform: ejmvc
control: Sunburst Chart
documentation: ug
---

# Highlight 
SunburstChart provides highlighting support for the points on mouse hover. To enable the highlighting , set the *Enable* property to true in the **HighlightSettings**. 

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     .HighlightSettings(highlight=>highlight.Enable(true))
 )

{% endhighlight %}

![](Highlight_images/Highlight_img1.png)

 
## Highlight Display mode

 You can customize the highlighted segment appearance by using color or opacity. You can choose between color or opacity using the **Type** property in the highlight Settings.

*	HighlightByColor – To display the highlighted segment appearance using color.
*	HighlightByOpacity – To display the highlighted segment appearance using opacity.

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     .HighlightSettings(highlight=>highlight.Enable(true).Type(SunburstHighlightType.Color).Color("Red"))
 )

 {% endhighlight %}

![](Highlight_images/Highlight_img2.png)

## Highlight Mode

Sunburst chart provides multiple option to represent the highlighted categories. You can highlight the segment categories by using the **Mode** property in highlightSettings
*	Child – To highlight the child of selected parent.
*	All – To highlight the entire categories in group.
*	Parent – To highlight the parent of selected child.
*	Single - To highlight single item in the category.

### Child
The following code shows how to set the highlight type as child 

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     .HighlightSettings(highlight=>highlight.Enable(true).Mode(SunburstHighlightMode.Child))
 )

{% endhighlight %}

![](Highlight_images/Highlight_img3.png)
 
### Parent

The parent mode can be enabled by using the below code 

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     .HighlightSettings(highlight=>highlight.Enable(true).Mode(SunburstHighlightMode.Parent))
 )


{% endhighlight %}

![](Highlight_images/Highlight_img4.png)
 
### Point

To highlight the particular segment, the point mode of the highlight settings is used.

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     .HighlightSettings(highlight=>highlight.Enable(true).Mode(SunburstHighlightMode.Point))
 )

 {% endhighlight %}

![](Highlight_images/Highlight_img5.png)
 
### All

The following code snippet is used for the all mode of highlight settings

{% highlight cshtml %}

@(Html.EJ().SunburstChart("chartContainer")

     .HighlightSettings(highlight=>highlight.Enable(true).Mode(SunburstHighlightMode.All))
 )


{% endhighlight %}

![](Highlight_images/Highlight_img6.png)

[Click](http://mvc.syncfusion.com/demos/web/sunburst/selection) here to view the online demo sample of Highlight in  the Sunburst Chart.
