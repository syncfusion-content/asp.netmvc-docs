---
layout: post
title: Axis
description: axis
platform: wpf
control: Chart
documentation: ug
---

# Axis

Charts typically have two axes that are used to measure and categorize data: a vertical (y) axis, and a horizontal (x) axis. To make a Chart easier to understand, you can add axis titles, tick marks, and labels. You can also change the alignment of axis title and format the labels that are displayed on axes. By default horizontal (x) axis and vertical (y) axis gets added to the Chart with axis labels, gridlines, and tick lines. You can also customize these axis explicitly by adding axis title or removing gridlines, tick lines that are added to the axis by default.

## Chart Axis supports the following types:

* Double
* DateTime
* Category
* Logarithmic

You can choose any of the Chart axis type using the” ValueType” property in axis. Axis calculates the range and interval automatically based on the series data points. 
{% highlight html %}
[MVC]



@(Html.EJ().Chart("container")



         .PrimaryXAxis(xaxis=>xaxis.MajorTickLines(mt=>mt.Visible(false))

              .Title(tl=>tl.Text("Country")))

         .PrimaryYAxis(yaxis=>yaxis.Title(tl=>tl.Text("Production")))



       //...

         )

{% endhighlight %}

![](Axis_images/Axis_img1.png)



## Double 

By default the ValueType of the axis is double and it represents the numerical data.
{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")

       // ...

     .PrimaryXAxis(pr=>pr.Title(tl=>tl.Text("Year")).ValueType(AxisValueType.Double))

        .Series(sr =>

          {

            sr.Points(pt =>

             {

                pt.X(200).Y(10).Add();

                pt.X(210).Y(15).Add();

                pt.X(220).Y(24).Add(); 

                pt.X(230).Y(11).Add();

                pt.X(240).Y(23).Add();

                pt.X(250).Y(13).Add();

                pt.X(260).Y(16).Add();

                pt.X(270).Y(10).Add();

                pt.X(280).Y(18).Add();

              }).Name("product A").Add();

          })

         //...

      )


{% endhighlight  %}
With the default auto range calculation, the range padding properties allows you to customize the automatic range calculation.

### Range Padding:

### None:

By default, the RangePadding for Numerical Axis is none.

The following screenshot displays a Chart’s x-axis with RangePadding set to None.



![](Axis_images/Axis_img2.png)



### Additional:

If RangePadding for Numerical Axis is set to Additional, the interval of the axis is added as padding.

The following screenshot illustrates a Chart’s x-axis with RangePadding set to Additional.



![](Axis_images/Axis_img3.png)



### Normal:

Normal RangePadding for a Numerical Axis is used mostly for the y-axis to have padding based on the Range calculation.

The following screenshot illustrates a Chart’s y-axis with RangePadding set to Normal.



![](Axis_images/Axis_img4.png)



### Round:

Round RangePadding for a Numerical Axis rounds the range of the Chart axis to the nearest possible value divisible by the interval.

The following screenshot illustrates a Chart’s x-axis with RangePadding set to Round.



![](Axis_images/Axis_img5.png)



## DateTime Axis

The DateTime Axis has a property IntervalType that sets the DateTime interval to one of the following:

* Days
* Hours
* Milliseconds
* Minutes 
* Months
* Seconds
* Years

The Interval property of DateTime Axis can be any double value based on the IntervalType.
{% highlight html %}
 [MVC]



@(Html.EJ().Chart("chartcontainer")

          // ...    

   .PrimaryXAxis(pr=>pr.Title(tl=>tl.Text("Year")).ValueType(AxisValueType.Datetime)

    .Range(ra=>ra.Min(new DateTime(2000,6,1)).Max(new DateTime(2010,6,1)).Interval(1))

     .IntervalType(ChartIntervalType.Years))

     .Series(sr =>

       {

         sr.Points(pt =>

           {

             pt.X(new DateTime(2000, 06, 11)).Y(10).Add();

             pt.X(new DateTime(2002, 03, 07)).Y(30).Add();

             pt.X(new DateTime(2004, 03, 06)).Y(15).Add();

             pt.X(new DateTime(2006, 03, 30)).Y(65).Add();

             pt.X(new DateTime(2008, 03, 08)).Y(90).Add();

             pt.X(new DateTime(2010, 03, 08)).Y(85).Add();                          

            }).Name("sales").Type(SeriesType.Line).Add();

         })

          //...

          )


{% endhighlight  %}
![](Axis_images/Axis_img6.png)



With the default auto range calculation, the RangePadding properties for date-time axis allow you to customize the automatic range calculation.

### Range Padding:

### None:

By default, the RangePadding for a DateTime Axis is none.

The following screenshot illustrates a Chart’s x-axis with RangePadding set to none. 



![](Axis_images/Axis_img7.png)



### Additional:

If RangePadding for DateTime Axis is set to Additional, the DateTime interval of the axis is added as padding.

The following screenshot illustrates a Chart’s x-axis with RangePadding set to Additional.



![](Axis_images/Axis_img8.png)



### Round:

Round RangePadding for a DateTime Axis rounds the range of the Chart axis to the nearest possible Date Time value.

The following screenshot illustrates a Chart’s x-axis with RangePadding set to Round.



![](Axis_images/Axis_img9.png)



## Category Axis

Category (x) axis displays text labels instead of numerical intervals. By default, the interval is 1 for which all the labels are displayed. To display every nth label, you can set that in Interval property. For example, to display every 2nd label, you can set Interval as 2. 
{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")

          // ...      

         .PrimaryYAxis(pr=>pr.Title(tl=>tl.Text("Medals")) 

          .Range(ra=>ra.Min(0).Max(80).Interval(20)))

           .Series(sr =>

              {

                  sr.Points(pt =>

                      {

                          pt.X("USA").Y(50).Add();

                          pt.X("China").Y(40).Add();

                          pt.X("Japan").Y(70).Add();

                          pt.X("Australia").Y(60).Add();

                          pt.X("France").Y(50).Add();

                          pt.X("Germany").Y(40).Add();

                          pt.X("Italy").Y(40).Add();

                          pt.X("Sweden").Y(30).Add();      

                      }).Name("Gold").Type(SeriesType.Line).Add();

              })

          //...

          )



{% endhighlight %}

![](Axis_images/Axis_img10.png)



## Logarithmic Axis

An axis displaying a logarithmic scale is very useful when your data values span orders of magnitude. Log axis is enabled using ValueType property.
{% highlight html %}
 [MVC]



@(Html.EJ().Chart("chartcontainer")

          // ...

          .PrimaryYAxis(pr=>pr.ValueType(AxisValueType.Logarithmic))

          .Series(sr =>

              {

                  sr.Points(pt =>

                      {

                          pt.X(1990).Y(80).Add();

                          pt.X(1991).Y(200).Add();

                          pt.X(1992).Y(400).Add();

                          pt.X(1993).Y(600).Add();

                          pt.X(1994).Y(900).Add();

                          pt.X(1995).Y(140).Add();

                          pt.X(1996).Y(2000).Add();

                          pt.X(1997).Y(4000).Add();

                          pt.X(1998).Y(6000).Add();

                          pt.X(1999).Y(8000).Add();

                          pt.X(2000).Y(9000).Add();

                      }).Type(SeriesType.Line).Add();

              })

          //...

          )


{% endhighlight %}
![](Axis_images/Axis_img11.png)



### Chart Axis Properties:

_Table1: Chart Axis Properties Table_

<table>
<tr>
<th>
Chart Axis Properties</th><th>
Description</th></tr>
<tr>
<td>
DesiredIntervals</td><td>
An integer property used to indicate the preferred total number of intervals to be displayed for auto range calculation.</td></tr>
<tr>
<td>
MaximumLabels</td><td>
An Integer property used to indicate number of labels per 100 pixels. By default, 3 labels renders for 100 pixels of length.</td></tr>
</table>
## Multiple Axis

In cases of multiple series, a Chart can have multiple x and y axes to represent each series. The axes can be arranged in stacking or side-by-side mode. By default, the axes are arranged in side-by-side mode. In order to arrange the axis in a stacking mode, you can split the Chart into number of rows or columns using RowDefinitions and ColumnDefinitions and then you can place the required axis in the desired row and column. Heights of the vertical axes are customized using the RowHeight property in RowDefinitions and the width of the horizontal axes are customized using ColumnWidth property in ColumnDefinitions.
{% highlight html %}
 [MVC]



@(Html.EJ().Chart("chartcontainer")

  .RowDefinitions(rowdef=>

   {

     rowdef.RowHeight(50).Unit("percentage").Add();

     rowdef.RowHeight(50).Unit("percentage").Add();

    })

  .PrimaryXAxis(xaxis=>xaxis.Title(tit=>tit.Text("Month")))          

  .PrimaryYAxis(yaxis=>yaxis.Range(r=>r.Min(0).Max(60).Interval(10))

      .Title(tit=>tit.Text("Temperature(Fahrenheit)")))

  .Axes(ax=>

      {                     

        ax.Orientation(Orientation.Vertical).RowIndex(1). Name("yAxis")

          .Title(tl=>tl.Text("Temperature(Celsius)")).PlotOffset(20).Add();

      })

  .Series(ser=>

      {

         ser.Name("Germany").Points(po =>

          {

            po.X("Jan").Y(15).Add();

            po.X("Feb").Y(20).Add();

            po.X("Mar").Y(35).Add();

            po.X("Apr").Y(40).Add();

            po.X("May").Y(30).Add();

            po.X("Jun").Y(40).Add();

            po.X("Jul").Y(43).Add();

            po.X("Aug").Y(35).Add();

           }).Add(); 



          ser.Name("India").YAxisName("yAxis").Points(po=>

           {

             po.X("Jan").Y(33).Add();

             po.X("Feb").Y(31).Add();

             po.X("Mar").Y(30).Add();

             po.X("Apr").Y(28).Add();

             po.X("May").Y(29).Add();

             po.X("Jun").Y(30).Add();

             po.X("Jul").Y(33).Add();

             po.X("Aug").Y(32).Add();                                                                                                                                                          

            }).Add();

        })



       // ...

     )

{% endhighlight  %}

![](Axis_images/Axis_img12.png)



In the above code, you can remove the RowDefinition and RowIndex from axis to arrange the axes in the side-by- side mode.



![](Axis_images/Axis_img13.png)



### Spanning Axis:

Charts having multiple series have multiple x and y axis to represent each series. By default, the axes are arranged in the corresponding row/column position. Spanning feature allows you to span the axis across multiple panes/rows. 
{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")

       // split the chart area into 3 rows with different height       

   .RowDefinitions(rowdef=>

     {

       rowdef.RowHeight(25).Unit("percentage").Add();

       rowdef.RowHeight(25).Unit("percentage").Add();

       rowdef.RowHeight(50).Unit("percentage").Add();   

     })

   .PrimaryXAxis(xaxis=>xaxis.Title(tit=>tit.Text("Date")))

   .PrimaryYAxis(yaxis=>yaxis.Range(r=>r.Min(0).Max(100).Interval(25))

       .RowIndex(0)  // renders in 1st row                

       .Font(fn=>fn.Size("14px")).Title(tit=>tit.Text("Quater1")))

   .Axes(ax=>

    {                      

     ax.RowIndex(1).RowSpan(2) // renders in 2nd row and spans to 2 rows

       .AxisName("y1SecondQuater").Range(ra=>ra.Min(0).Max(100)

       .Interval(20)).Title(tl=>tl.Text("Quater 2")).PlotOffset(30).Add();                    

     ax.Name("y2SecondQuater").RowSpan(3) // renders in 1st row and spans to 3 rows

       .Range(ra=>ra.Min(0).Max(100)

       .Interval(10)).Title(tl=>tl.Text("Quater 3")).Add();

     })



    .Series(ser=>

     {

       ser.Name("Gold").Type(SeriesType.Column).Points(po =>

        {

          po.X("USA").Y(50).Add();

          po.X("China").Y(40).Add();

          po.X("Japan").Y(70).Add();

          po.X("Australia").Y(60).Add();

          po.X("France").Y(50).Add();

          po.X("Germany").Y(40).Add();

          po.X("Italy").Y(40).Add();

          po.X("Sweden").Y(30).Add();

        }).Add(); 



        ser.Name("Silver").YAxisName("y1SecondQuater").Points(po=>

         {

           po.X("USA").Y(70).Add();

           po.X("China").Y(60).Add();

           po.X("Japan").Y(40).Add();

           po.X("Australia").Y(36).Add();

           po.X("France").Y(25).Add();

           po.X("Germany").Y(30).Add();

           po.X("Italy").Y(35).Add();

           po.X("Sweden").Y(25).Add();                                                                                                                                                         

         }).Add();



        ser.Name("Bronze").YAxisName("y2SecondQuater").Type(SeriesType.Spline)

           .Points(po =>

         {

           po.X("USA").Y(10).Add();

           po.X("China").Y(19).Add();

           po.X("Japan").Y(40).Add();

           po.X("Australia").Y(70).Add();

           po.X("France").Y(35).Add();

           po.X("Germany").Y(82).Add();

             po.X("Italy").Y(57).Add();

             po.X("Sweden").Y(97).Add();

           }).Add();

       })



      // ...

   )

{% endhighlight %}

![](Axis_images/Axis_img14.png)



## Axis Title

You can customize the ejChart Axis title text, font styles and color using “Title” property of axis. 
{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")



 .PrimaryXAxis(xaxis=>xaxis.Title(tit=>tit.Text("Expenditure")

    .Font(fn=>fn.Color("#AA3EEF").FontFamily("Segoe UI").FontStyle(ChartFontStyle.Normal)

    .Size("16px").Opacity(1).FontWeight(ChartFontWeight.Regular))))



 .PrimaryYAxis(xaxis=>xaxis.Title(tit=>tit.Text("Expense")

    .Font(fn=>fn.Color("#AA3EEF").FontFamily("Segoe UI").FontStyle(ChartFontStyle.Normal)

    .Size("16px").Opacity(1).FontWeight(ChartFontWeight.Regular))))



  // ...

)

{% endhighlight  %}

![](Axis_images/Axis_img15.png)



### Trim Title

Essential Chart supports TrimmingAxisTitles with the properties, EnableTrim and MaximumTitleWidth. These are useful for shortening the lengthy titles. On hovering with the mouse, you can see the full title in the tooltip.

![](Axis_images/Axis_img16.png)



![](Axis_images/Axis_img17.png)



__
{% highlight html %}
[MVC]



@(Html.EJ().Chart("container") 



     .PrimaryXAxis(pr => pr.Title(tl => tl.Text("List of countries which are using solar power in the year 2014")))



     .PrimaryYAxis(pr => pr.Range(ra => ra.Min(0).Max(40).Interval(5)).Title(tl => tl.Text("Measurements of Solar power used in different countries in the year 2014( in GW)")).LabelFormat("{value}GW"))



           //.......

  )   
{% endhighlight  %}

## Labels

The axis labels are present along the axis showing the value of the data it corresponds to. You can further customize the Chart axis labels using “Font” and “LabelFormat” properties of the axis. 
{% highlight html %}
 [MVC]



@(Html.EJ().Chart("chartcontainer")



  .PrimaryXAxis(xaxis=>xaxis.Title(tit=>tit.Text("Expenditure")

    .Font(fn=>fn.Size("11px").Color("red"))))



  .PrimaryYAxis(xaxis=>xaxis.Title(tit=>tit.Text("Efficiency")

    .Font(fn=>fn.Size("11px").Color("red"))).LabelFormat("{value}%"))



   // ...            

  )


{% endhighlight %}
![](Axis_images/Axis_img18.png)



### LabelPlacement:

The category axis includes the LabelPlacement property that is used to set the labels of the axis between the tick lines or on the tick lines of the category axis. By default the LabelPlacement value for the category axis is BetweenTicks.

There are two types of LabelPlacement:

* BetweenTicks
* OnTicks
{% highlight html %}
 [MVC]



@(Html.EJ().Chart("chartcontainer")



    .PrimaryXAxis(xaxis=>xaxis.Title(tit=>tit.Text("Countries")

         .Font(fn=>fn.Size("11px").Color("red"))).LabelPlacement("onTicks"))



    // ...

  )


{% endhighlight  %}
![](Axis_images/Axis_img19.png)





![](Axis_images/Axis_img20.png)



### Label Position

Axis labels can further be customized to render inside the chart area using the property LabelPosition. By default, it is set as outside. This helps to display labels in a proper manner while multiple axes are used in the chart.
{% highlight html %}
[MVC]



 @(Html.EJ().Chart("chartcontainer") 

      .PrimaryXAxis(pr=>pr.AxisLabelPosition(AxislabelPosition.Inside))

      .PrimaryYAxis(pr=>pr.AxisLabelPosition(AxislabelPosition.Inside))

)   

{% endhighlight %}

![](Axis_images/Axis_img21.png)

































_Figure46: Label inside Chart_



### Axis label trimming 

Chart provides support for trimming y axis labels and x axis labels by using the properties EnableTrim and MaximumLabelWidth. These are used to show the lengthy labels in a shorter form. On mouse hover, it shows the full label in the tooltip.


{% highlight html %}
[MVC]

@(Html.EJ().Chart("chartcontainer")

 .PrimaryXAxis(pr => pr.EnableTrim(true).MaximumLabelWidth(34))

 .PrimaryYAxis(pr => pr.EnableTrim(true).MaximumLabelWidth(34))

)

{% endhighlight  %}

The following screenshot displays the Chart Axis with trimming

![](Axis_images/Axis_img22.png)



## Tick Marks

Tick lines are displayed horizontally and vertically in Chart axis based on the orientation of the axis.

### Major Tick Lines
It is rendered in Chart axis for each interval of axis range. By default, it is visible. You can collapse it by setting ‘Visible’ as false. You can customize the major tick lines width, opacity, and color.

### Minor Tick Lines

It is rendered between the major tick lines of Chart axis. To display MinorTickLines in Chart axis enable visible property of “MinorTickLines” and set values to “MinorTicksPerInterval” in the respective axis. By default, it is invisible. You can customize the minor tick lines width, and color.


{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")



  .PrimaryXAxis(xaxis=>xaxis.MajorTickLines(mr=>mr.Width(1.5).Size(6).Visible(true))

    .MinorTickLines(mt=>mt.Width(1).Size(4).Visible(true)).MinorTicksPerInterval(5))



  .PrimaryYAxis(yaxis=>yaxis.MajorTickLines(mr=>mr.Width(1.5).Size(6).Visible(true))

    .MinorTickLines(mt=>mt.Width(1).Size(4).Visible(true)).MinorTicksPerInterval(5))



  // ...

)

{% endhighlight  %}

![](Axis_images/Axis_img23.png)



### Tick lines placement

You can customize tick lines and render them inside the chart area using the property TickLinesPosition. By default, it is set as outside. This property will be used when labels are inside.

{% highlight html %}

[MVC]

@(Html.EJ().Chart("chartcontainer") 

       .PrimaryXAxis(pr=>pr.TickLinesPosition(TickLinesPosition.Inside))

       .PrimaryYAxis(pr=>pr.TickLinesPosition(TickLinesPosition.Inside))

  ) 

{% endhighlight  %}

![](Axis_images/Axis_img24.png)



## Grid Lines	

Grid lines are displayed in horizontal and vertical position in Chart area based on the intervals.

### Major Grid Lines

It is rendered in Chart area for each interval of axis range. By default, it is visible. You can collapse it by setting ‘Visible’ property to false. You can customize the major gridlines width, opacity, and dashArray of gridline.

### Minor Grid Lines

It is rendered between the major gridlines of Chart area.To display minor grid lines in Chart area enable Visible property of “MinorGridLines” and set values to “MinorTicksPerInterval” in the respective axis. By default, ‘Visibile’ property is set to “false”. You can customize the minor grid lines width, and dashArray of gridline.


{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")



 .PrimaryXAxis(xaxis=>xaxis.MajorGridLines(mr=>mr.Width(2).DashArray("").Visible(true)

    .Opacity(1)).MinorGridLines(mg=>mg.Width(1).DashArray("").Visible(true))

    .MinorTicksPerInterval(1))



 .PrimaryYAxis(yaxis=>yaxis.MajorGridLines(mr=>mr.Width(2).DashArray("").Visible(true)

     .Opacity(1)).MinorGridLines(mg=>mg.Width(1).DashArray("").Visible(true))     

     .MinorTicksPerInterval(1))



  // ...

)

{% endhighlight  %}

![](Axis_images/Axis_img25.png)



### Alternate Grid Band

Grid Band is the distance between two adjacent major grid lines which are displayed in horizontal and vertical position.

### Even Grid Band

Even Grid Band are counted from axes lines, i.e the band which is immediate adjacent for axes lines. By default, the even grid band color is transparent. You can highlight the even grid band by setting Fill property of Even. You can customize the Opacity of the even grid band color.

### Odd Grid Band

Immediate adjacent band of every even grid bands are Odd Grid Bands. You can discriminate the odd grid band from even by setting Fill property of Odd. You can customize the Opacity of the odd grid band color.


{% highlight html %}
[MVC]

@(Html.EJ().Chart("container")



      .PrimaryXAxis(pr => pr.AlternateGridBand(ag => ag.Even(ev =>   

                    ev.Fill("#E896E8").Opacity(0.5))))              

      .PrimaryYAxis(pr => pr.AlternateGridBand(ag => ag.Odd(od => 

                    od.Fill("#E6F0E7").Opacity(0.5))))

  // ...

)
{% endhighlight  %}
_Figure48: Chart explaining grid band_

![C:/Users/dineshkumarn/Desktop/ug line.png](Axis_images/Axis_img26.png)































## Inversed Axis

You can display the Chart series in to inversed position using “IsInversed” property of Chart Axis. This is illustrated in the following code.


{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")



  .PrimaryYAxis(yaxis=>yaxis.IsInversed(true))



    // ...

 )

{% endhighlight  %}

![](Axis_images/Axis_img27.png)



## Opposed Position

By default, the x-axis is arranged horizontally at the bottom of the Chart and the y-axis is arranged vertically at the left side of the Chart. You can change the alignment of the axis by setting OpposedPosition to true, which arranges the x-axis at the top and the y-axis at the right of the Chart.  
{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")

    .PrimaryXAxis(xaxis =>xaxis.OpposedPosition(true))

    .PrimaryYAxis(yaxis=>yaxis.OpposedPosition(true))



   // ...

    )

{% endhighlight  %}

![](Axis_images/Axis_img28.png)



## Smart Axis Labels

Sometimes the Chart dimensions could cause the labels to intersect. You can avoid overlapping labels using “LabelIntersectAction” property of char axis. The Chart by default renders the texts one over the other. But, it also has some built-in capabilities to work around this overlap and lets you dictate the technique to follow. Refer to the following properties.

* Rotate45 – Rotate the labels to 45 degree.
* Rotate90 – Rotate the labels to 90 degree
* Trim – Intersecting labels will be trim and mouse over the labels, it displays the trimmed text like tooltip.
* MultipleRows – Split the intersecting labels in to multiple rows and display on the axis
* Wrap – Wrap the intersecting text and display
* Hide – It doesn’t display the intersecting label texts on the axis.


{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")



  .PrimaryXAxis(xaxis=>xaxis.LabelIntersectAction(LabelIntersectAction.Rotate45))                  

  .PrimaryYAxis(yaxis=>yaxis.LabelIntersectAction(LabelIntersectAction.None))



  // ...

)

{% endhighlight  %}

![](Axis_images/Axis_img29.png)



