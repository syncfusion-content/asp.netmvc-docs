---
layout: post
title: Legend
description: legend
platform: ejmvc
control: Chart
documentation: ug
---

# Legend

Essential Chart allows you to customize its legend position, color, border, size, shape, padding, font styles, opacity etc. You can enable and disable Chart legends using legend Visible property. Default value of legendVisible property is set to “true”. 

## Legend Title

EJ Chart provides Legend Title support to the information about the series. It also provides options to customize the Legend Title with fonts and alignment.


{% highlight js %}




       @(Html.EJ().Chart("chartcontainer")

		.Legend(lg=>lg.Visible(true)).Title(lt=>lt.Text("Countries").
                   TextAlignment(TextAlignment.Center).Font(fn=>fn.Color("black").Size("12px")))     

)           

{% endhighlight  %}

The following screenshot displays Legend Title:

![](Legend_images/Legend_img1.png)



## Legend Position

You can position the legend at top, bottom, left or right position of the Chart. Default value of legendposition is “Bottom”.  And you can align the legend position using “Alignment” property of legend.  This allows you to align the legend at center, far and near position of Chart area.  Default value of legendalignment is “Center”. 
{% highlight js %}


@(Html.EJ().Chart("chartcontainer")

// ...

   .Legend(lg=>lg.Visible(true).Position(LegendPosition.Bottom)

        .Alignment(TextAlignment.Center))

// ...

   )

{% endhighlight  %}

![](Legend_images/Legend_img2.png)



## Customization

### Legend border and shape:

In Essential Chart, you can customize the legend shape with different symbols like rectangle, circle, cross, diamond, pentagon, hexagon, star, ellipse, triangle etc. Default value of legend “Shape” is “Rectangle”. And you can draw and customize the outline of Chart legends using border property of legend. Default value of legend border color is “Transparent”. 

{% highlight js %}

@(Html.EJ().Chart("chartcontainer")

// ...

    .Legend(lg=>lg.Visible(true).Border(br=>br.Color("red").Width(2))

       .Shape(ChartShape.Circle))

// ...

   )

{% endhighlight  %}

![](Legend_images/Legend_img3.png)



### Legend RowCount and ColumnCount:

Essential Chart allows you to display the legend items for row and column wise using “RowCount” and “ColumnCount” property. This is used to avoid overlapping between legends and Chart area when using more legends in Chart area.

{% highlight js %}


@(Html.EJ().Chart("chartcontainer")

// ...

.Legend(lg=>lg.Visible(true).RowCount(2))

          // ...

)

{% endhighlight %}

![](Legend_images/Legend_img4.png)



### Legend item style and border customization:

Essential Chart allows you to customize the legend item size, and border color and width using “ItemStyle” property. Default value of legend item size is (10, 10), and legend item border color is “Transparent”.


{% highlight js %}

@(Html.EJ().Chart("chartcontainer")

// ...

     .Legend(lg=>lg.Visible(true).RowCount(2).ItemStyle(it=>it.Height(12).Width(12)

       .Border(br=>br.Color("magenta").Width(1.5))))

// ...

     )


{% endhighlight  %}
![](Legend_images/Legend_img5.png)



### Legend font

You can customize the legend font family, font style, font weight and size and font styles using “Font” property of Legend. This is illustrated in the following code example.


{% highlight js %}

@(Html.EJ().Chart("chartcontainer")

// ...

     .Legend(lg=>lg.Visible(true).Font(fn=>fn.FontFamily("Segoe UI")

       .FontStyle(ChartFontStyle.Normal).FontWeight(ChartFontWeight.Regular).Size("15px"))

       .RowCount(2).Border(br=>br.Color("red").Width(2)).Shape(ChartShape.Circle))

// ...

      )

{% endhighlight  %}

![](Legend_images/Legend_img6.png)



### Legend opacity and item padding:

Essential Chart allows you to set “Opacity” for Chart legends. And you can define the spacing between the legend items using “ItemPadding” property of legend. Default value of ItemPadding size is 10.


{% highlight js %}

@(Html.EJ().Chart("chartcontainer")

//...

    .Legend(lg=>lg.Visible(true).Opacity(1.5).ItemPadding(20)

       .ItemStyle(it=>it.Height(12).Width(12).Border(br=>br.Color("magenta")

       .Width(1.5))))

// ...

 )


{% endhighlight  %}
![](Legend_images/Legend_img7.png)



### Scrollbar for legends:

Essential Chart allows you to customize the legend height and width using size property. Default value of the height and width are null and it varies depending upon the legend position. If the legen is in top or bottom of the chart, default value of height is 20% of chart height and width is 100% of chart width. Similarly if it is in the left or right side of the chart, default value of height is 100% of chart height and width is 20% of chart width.

This property supports both pixels and percentage values. E.g. 100 or 10%.

Scrollbar is enabled for the legends, when the legend size is greater than the user specified value or than the default value of the legend size. 
{% highlight js %}


@(Html.EJ().Chart("chartcontainer")

        // ...

        .CommonSeriesOptions(series=>series.Type(CSeriesType.Pie))

        .Size(sz=>sz.Height(‘600’).Width(‘800’))

        .Legend(lg=>lg.Visible(true).Shape(ChartShape.Circle).ColumnCount(2)

                . Size(size=>size.Height(‘25%’).Width(‘150’)))                 	 // ...

 )

{% endhighlight  %}

![](Legend_images/Legend_img8.jpeg)



### Custom Legend Icons:

You can customize the shape of the legend icon. Normally the available shapes are circle, rectangle, star, wedge, uparrow, downarrow, pentagon, etc. By default, the shape of the legend icon is rectangle, you can modify this by setting Shape property of Legend. If you want series type as icon then set the Shape property value as “SeriesType”. You can customize the height and width of the icon by setting ItemStyle property
{% highlight js %}

@(Html.EJ().Chart("chartcontainer")

// ...

   .Legend(lg=>lg.Visible(true).Position(LegendPosition.Bottom)

           .Shape(ChartShape.SeriesType) .ItemStyle(item=>item.Height(15)

           .Width(15)))

// ...

   )


{% endhighlight  %}
![](Legend_images/Legend_img9.png)



