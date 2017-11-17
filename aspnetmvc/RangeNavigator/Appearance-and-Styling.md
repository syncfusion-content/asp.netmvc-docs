---
layout: post
title: Appearance and Styling | RangeNavigator | ASP.NET MVC | Syncfusion
description: appearance and styling
platform: ejmvc
control: RangeNavigator
documentation: ug
---

# Appearance and Styling

**RangeNavigator** is enriched with lots of customization options for labels, gridlines and slider to develop high quality graphic rich control.

## Customize labels

The labels are found along the range, displaying the value of the data it correspond, both on (higher level label) and below (lower level label) the RangeNavigator. **RangeNavigator** labels are further customized using higher level label `Style` property of `Font` and lower level label `Style` property of `Font` property in `LabelSettings`.

The higher level labels font `Color`, `FontFamily`, `FontStyle`, `FontWeight`, `Opacity` and `Size` can be customized using `HigherLevel` property.

The lower level labels font `Color`, `FontFamily`, `FontStyle`, `FontWeight`, `Opacity` and `Size` can be customized using `LowerLevel` property. 
{% highlight CSHTML %}

@(Html.EJ().RangeNavigator("container")

.LabelSettings(ls=>ls

// customizing higher level labels.

.HigherLevel(higher =>higher                                     

.Style(style => style

		  .Font(f =>f

			   .Color("#ff0000") 

			   .Opacity(1)

			   .Size("12px")                                                                     

			   .Style(RangeNavigatorFontStyle.Normal)

			 .Weight(RangeNavigatorFontWeight.Regular)

					)

				 )

		   )

// customizing lower level labels.

.LowerLevel(ll => ll

. Style(style => style

	  .Font(f => f

			   .Color("#ff0000")

			   .Opacity(1)

			   .Size("12px")                                              

			   .Style(RangeNavigatorFontStyle.Normal)                                                              

			 .Weight(RangeNavigatorFontWeight.Regular)

			 )

		)

	)                                                                                                                                                                                                                                                                                                                                   

))

{% endhighlight  %}

![](Appearance-and-Styling_images/Appearance-and-Styling_img1.png)

Customize labels
{:.caption}

## Label Placement:

Labels in **RangeNavigator** are placed inside or outside of the control. You can customize both the higher and lower level labels using `LabelPlacement` property in label setting of RangeNavigator. By default `LabelPlacement` is “outside” for the both higher and lower level labels.

The following screen shot illustrates both the lower and higher level labels that are placed outside the control with LabelPlacement specified as outside. 

{% highlight CSHTML %}


@(Html.EJ().RangeNavigator("container")

.LabelSettings(ls=>ls

				.HigherLevel(higher =>higher.LabelPlacement("inside"))                                                                          

				.LowerLevel(ll => ll.LabelPlacement("inside"))                                                                                                                                                                                                                                                                                                                                                              

			   )    

)

{% endhighlight  %}
The following screenshot illustrates a **RangeNavigator** with labels inside the control after specifying the LabelPlacement as inside.



![](Appearance-and-Styling_images/Appearance-and-Styling_img2.png)



## Customize RangeNavigator

### Customize NavigatorStyleSettings

RangeNavigator is customized using `NavigatorStyleSettings` properties. You can customize the selected and unselected region color using `SelectedRegionColor` and `UnselectedRegionColor`, `SelectedRegionOpacity` and `UnselectedRegionOpacity` in **NavigatorStyleSettings** and the thumb of the slider using `ThumbColor`, `ThumbRadius` and `ThumbStroke` in NavigatorStyleSettings.  `MajorGridLineStyle` and `MinorGridLineStyle` are used to customize the major grid line `Color`, `Visible` property and minor gridline `Color` and `Visible`. You can customize the `Background`, `Opacity` and `Border` `Color`, `DashArray` and `Width` of navigatorStyleSettings.

### Customize Labels

The visibility of labels are enabled by setting `Visible` in higher level and `Visible` in lower level. The labels can be aligned by specifying `HorizontalAlignment` of higher level style and `HorizontalAlignment` of lower level style.

You can customize the `Border` `Color` and `Width`, `Fill`, `GridLineStyle` `Color`, `DashArray` and `Width`, `Position` property of higher level labels in labelSettings.

You can also customize the `Border` `Color` and `Width`, `Fill`, `GridLineStyle` `Color`, `DashArray` and `Width`, `Position` property for lower level labels of labelSettings.

{% highlight CSHTML %}
 
@(Html.EJ().RangeNavigator("container")


//  To customize the navigator element     

.NavigatorStyleSettings (navigator=>navigator

.Border(br=>br.Color("black").Width(3))

.Background("transparent")

.UnselectedRegionColor("white")

.SelectedRegionColor("#5EABDE")

.ThumbRadius(10)

.ThumbColor("white")

.MajorGridLineStyle(mr=>mr.Color("transparent").Visible(true))

.MinorGridLineStyle(mi=>mi.Color("transparent").Visible(true))

)

//  To customize the labels

.LabelSettings(ls=>ls

.HigherLevel(higher =>higher

.LabelPlacement("inside")

.IntervalType(NavigatorIntervalType.Years)                                      

.Style(style => style                                                       

.HorizontalAlignment(HorizontalAlignment.Left)

.Font(f =>f

		  .Color("black") 

		  .Opacity(1)

		  .Size("13px")

	 )

)

)

.LowerLevel(ll => ll

.LabelPlacement("inside")                                              

.IntervalType(NavigatorIntervalType.Quarters)

.Style(style => style                                              

.HorizontalAlignment(HorizontalAlignment.Center)

.Font(f => f

		 .Color("black")

		 .Opacity(1)

		 .Size("12px")

	 )

)

)                                                                                                                                                                                                                                                                                                                                   

))

{% endhighlight  %}

![](Appearance-and-Styling_images/Appearance-and-Styling_img3.png)



## Themes

RangeNavigator `Theme` is a set of pre-defined options that are applied to the control before each RangeNavigator is instantiated. Following predefined themes are available in ASP.NET MVC RangeNavigator.

1. flatlight                  
2. flatdark                  
3. gradientlight           
4. gradientdark           
5. azure                      
6. azuredark               
7. lime 
8. limedark
9. saffron
10. saffrondark
11. gradientazure
12. gradientazuredark
13. gradientlime
14. gradientlimedark
15. gradientsaffron

### gradientsaffrondark

{% highlight CSHTML %}


@(Html.EJ().RangeNavigator("container")

.Theme("azuredark")

)

{% endhighlight  %}

![](Appearance-and-Styling_images/Appearance-and-Styling_img4.png)



