---
layout: post
title: Chart Axis |Chart  | ASP.NET MVC | Syncfusion
description: How to customize the grid lines, tick lines, labels and title of chart axis
platform: ejmvc
control: Chart
documentation: ug
---

# Axis

**Charts** typically have two axes that are used to measure and categorize data: a vertical (y) axis, and a horizontal (x) axis.

Vertical axis always uses numerical or logarithmic scale. Horizontal(x) axis supports the following types of scale:

* Category
* Numeric
* DateTime
* DateTime Category
* Logarithmic

## Category Axis

Category axis displays the text labels instead of numbers. To use the categorical axis, you can set the **ValueType** property of the axis to the **Category**. Default value of ValueType is **Double**.

{% highlight cshtml %}

  @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Use categorical scale in primary X axis
          px=>px.ValueType(AxisValueType.Category)
     )
        // ...
    )


{% endhighlight %}


![](Axis_images/axis_img1.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/column) here to view our online demo sample that uses Category axis.


### Place labels on ticks

Labels in the category axis can be placed on the ticks by setting the **LabelPlacement** property of axis to the onTicks. The default value of the LabelPlacement property is betweenTicks i.e. labels are placed between the ticks, by default.

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Placing X-axis labels on the ticks
          px=>px.LabelPlacement("onTicks")
     )
        // ...
    )


{% endhighlight %}

![](Axis_images/axis_img2.png)


### Display labels after a fixed interval

To display the labels after a fixed interval n, you can set the **Interval** property of the axis range as **n**. The default value of the interval is 1 i.e. all the labels are displayed.

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Displaying labels after 2 intervals
          axis=>axis.Range(range=>range.Interval(2))
     )
        // ...
    )


{% endhighlight %}

![](Axis_images/axis_img3.png)


### Indexed Category Axis

Category axis can also plot points based on index value of data points. Index based plotting can be enabled by setting **IsIndexed** property to true in the axis.

{% highlight cshtml %}

     @(Html.EJ().Chart("chartContainer")
            //...
            .PrimaryXAxis(px=>px.IsIndexed(true))
                .Series(sr =>
                {
                    //Adding Candle series
                    sr.Points(pt=>{
                        pt.X("Monday").Y(50).Add();
                        pt.X("Tuesday").Y(40).Add();
                        pt.X("Wednesday").Y(70).Add();
                        pt.X("Thursday").Y(60).Add();
                        pt.X("Friday").Y(50).Add();
                        pt.X("Monday").Y(40).Add();
                        pt.X("Monday").Y(30).Add();
                    }) .Add();
                })                
     )

{% endhighlight %}


![](Axis_images/axis_img50.png)

**While Category axis IsIndexed value false**

![](Axis_images/axis_img51.png)


## Numeric Axis 

Numeric axis uses numerical scale and displays numbers as labels. To use numeric axis, you can set the **ValueType** property of the axis to **Double**. 

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryYAxis(
          //Use numerical scale in primary Y axis
          px=>px.ValueType(AxisValueType.Double)
     )
        // ...
    )


{% endhighlight %}

![](Axis_images/axis_img4.png)


### Customize numeric range

To customize the range of an axis, you can use the **Range** property of the axis to set the **Minimum**, **Maximum** and **Interval** values. Nice range is calculated automatically based on the provided data, by default.


{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryYAxis(
          //Customizing Y-axis range
          px=>px.Range(range=>range.Min(0).Max(50))
     )
        // ...
    )


{% endhighlight %}

![](Axis_images/axis_img5.png)


#### Customizing numeric interval

Axis interval can be customized by using the **Interval** property of the axis range. Nice interval is calculated based on the minimum and maximum value of the provided data, by default.

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryYAxis(
          //Set interval to PrimaryYAxis
          px=>px.Range(range=>range.Interval(5))
     )
        // ...
    )


{% endhighlight %}

![](Axis_images/axis_img6.png)


### Apply padding to the range

Padding can be applied to the minimum and maximum extremes of the axis range by using the **RangePadding** property. Numeric axis supports the following types of padding

* None
* Round
* Additional
* Normal

**None**

When the value of the RangePadding property is **None**, padding can not be applied to the axis. This is also the default value of the rangePadding. 

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryYAxis(
          //Applying none as range padding
          px=>px.RangePadding(ChartRangePadding.None)
     )
        // ...
 )


{% endhighlight %}

![](Axis_images/axis_img7.png)


#### Round

When the value of RangePadding property is **Round**, the axis range is rounded to the nearest possible value divided by the interval.

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryYAxis(
          //Applying round as range padding
          px=>px.RangePadding(ChartRangePadding.Round)
     )
        // ...
 )


{% endhighlight %}

**Chart before rounding axis range**

![](Axis_images/axis_img8.png)


**Chart after rounding axis range**

![](Axis_images/axis_img9.png)


**Additional**

When the value of the RangePadding property is **Additional**, the axis range is rounded and an interval of the axis is added as padding to the minimum and maximum values of the range.

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryYAxis(
          //Applying additional range padding
          px=>px.RangePadding(ChartRangePadding.Additional)
     )
        // ...
 )


{% endhighlight %}

![](Axis_images/axis_img10.png)


**Normal**

When the value of the RangePadding property is **Normal**, the padding is applied to the axis based on the range calculation.

{% highlight cshtml %}

  @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryYAxis(
          //Applying normal range padding
          px=>px.RangePadding(ChartRangePadding.Normal)
     )
        // ...
 )


{% endhighlight %}

![](Axis_images/axis_img11.png)


####Customizing the starting range of the axis

By default the Y axis will be always calculated from the value 0 for column, bar, stacking column and stacking bar series types. You can modify this behavior by setting false to the property **StartFromZero** in the axis. On setting this the axis minimum value will be calculated based on the value for the data points.

{% highlight cshtml %}

@(Html.EJ().Chart("container")
        .PrimaryYAxis(axis => axis.RangePadding(ChartRangePadding.None).StartFromZero(false))
    )

{% endhighlight %}

![](Axis_images/axis_img66.png)


## DateTime Axis

Date time axis uses date time scale and displays the date time values as axis labels in the specified format. To use date time axis, set the ValueType property of the axis to **Datetime**.

{% highlight cshtml %}

  @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Use date time scale in primary X axis
          px=>px.ValueType(AxisValueType.Datetime)
     )
        // ...
 )


{% endhighlight %}

![](Axis_images/axis_img12.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/datetimeaxis) here to view our online demo sample for date time axis.

 
### Customizing date time range
 
 Axis range can be customized by using the Range property to set the **Minimum**, **Maximum** and **Interval** values. Nice range is calculated automatically based on the provided data, by default.
 
 {% highlight cshtml %}

  @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Customizing X-axis date time range
          axis=>axis.Range(range=>range.Min("2000/6/1").Max("2010/6/1"))
     )
        // ...
 )


{% endhighlight %}

![](Axis_images/axis_img13.png)


### Date time intervals

Date time intervals can be customized by using the **Interval** and **IntervalType** properties of the axis. For example, when you set Interval as **2** and IntervalType as **Years**, it considers the 2 years as interval.

Essential Chart supports the following types of interval for date time axis.

* Days
* Hours
* Milliseconds
* Minutes
* Months
* Seconds
* Years

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Customizing X-axis date time range
          axis=>axis.Range(range=>range.Interval(2)).IntervalType(ChartIntervalType.Years)
     )
        // ...
 )

{% endhighlight %}


![](Axis_images/axis_img14.png)



### Apply padding to the range

Padding can be applied to the minimum and maximum extremes of the range by using the **RangePadding** property. Date time axis supports the following types of padding

* None
* Round
* Additional

**None**

When the value of the RangePadding property is **None**, padding is applied to the axis. This is also the default value of the rangePadding. 

{% highlight cshtml %}

  @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Applying none as range padding
          px=>px.RangePadding(ChartRangePadding.None)
     )
        // ...
 )

{% endhighlight %} 

![](Axis_images/axis_img15.png)


**Round**

When the value of the RangePadding property is **Round**, the axis range is rounded to the nearest possible date time value.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Applying round as range padding
          px=>px.RangePadding(ChartRangePadding.Round)
     )
        // ...
 )

{% endhighlight %} 

**Chart before rounding axis range**

![](Axis_images/axis_img16.png)


**Chart after rounding axis range**

![](Axis_images/axis_img17.png)


**Additional** 

When the value of the RangePadding property is **Additional**, the range is rounded and date time interval of the axis are added as padding to the minimum and maximum extremes of the range.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Applying additional as range padding
          px=>px.RangePadding(ChartRangePadding.Additional)
     )
        // ...
 )

{% endhighlight %} 

![](Axis_images/axis_img18.png)


## DateTime Category Axis

DateTime category axis takes date time value as input but behaves like category axis. This is used to display the date time values with nonlinear intervals (used to depict the business days by skipping holidays). To use date time axis, set the **ValueType** property of the axis to **DatetimeCategory**.

{% highlight cshtml %}

    @(Html.EJ().Chart("container")
      .PrimaryXAxis(axis => axis.ValueType(AxisValueType.DateTimeCategory))
    )

{% endhighlight %}

![](Axis_images/axis_img63.png)

[Click](http://mvc.syncfusion.com/demos/web/chart/datetimecategoryaxis) here to view our online demo sample for date time axis.

### Customizing DateTime Category range

Axis range can be customized by using the *range* property to set the **Minimum**, **Maximum** and **Interval** values. Datetime category axis takes numeric input for minimum and maximum property.

{% highlight cshtml %}

@(Html.EJ().Chart("container")
         .PrimaryXAxis(
          //Customizing X axis date time category range
           axis => axis.Range(range => range.Min(0).Max(4)))
    )

{% endhighlight %}

![](Axis_images/axis_img64.png)

### DateTime Category intervals

Date time category intervals can be customized by using the **Interval** and **IntervalType** properties of the axis. For example, when you set the intervalType as months, it displays only the first label of all the months from the data.

Essential Chart supports the following types of interval for date time category axis.
* Days
* Hours
* Milliseconds
* Minutes
* Months
* Seconds
* Years
* Auto

{% highlight cshtml %}

    @(Html.EJ().Chart("container")
         .PrimaryXAxis(axis => axis.IntervalType(ChartIntervalType.Months))
    )

{% endhighlight %}

![](Axis_images/axis_img65.png)


## Logarithmic Axis

Logarithmic axis uses logarithmic scale and it is very useful in visualizing when the data has values with both lower order of magnitude **(eg: 10<sup>-6</sup>)** and higher order of magnitude **(eg: 10<sup>6</sup>)**. To use logarithmic axis, set the ValueType property of the axis to **Logarithmic**.  

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Use logarithmic scale in primary X axis
          px=>px.ValueType(AxisValueType.Logarithmic)
     )
        // ...
 )


{% endhighlight %}


![](Axis_images/axis_img19.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/logaxis) here to view our online demo sample link for logarithmic axis.

### Customize Logarithmic range

Logarithmic range can be customized by using the Range property of the axis to change the Minimum, Maximum and Interval values. Nice range is calculated automatically based on the provided data, by default.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryYAxis(
          //Customizing logarithmic range
          px=>px.Range(range=>range.Min(1).Max(5))
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img20.png)


### Logarithmic base

Logarithmic base can be customized by using the **LogBase** property of the axis. The default value of the LogBase is **10**.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryYAxis(
          //Customizing logarithmic base
          px=>px.LogBase(2)
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img21.png)


### Logarithmic interval

Logarithmic axis interval can be customized by using the Interval property of the axis. When the logarithmic base is 10 and logarithmic interval is 2, then the axis labels are placed at an interval of 10<sup>2</sup>. The default value of the interval is 1. 

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryYAxis(
          //Customizing logarithmic interval
          px=>px.Range(range=>range.Interval(2))
              //....
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img22.png)
      

## Label Format

### Format numeric labels

Numeric labels can be formatted by using the **LabelFormat** property. Numeric values can be formatted with n (number with decimal points), c (currency) and p (percentage) commands.

{% highlight cshtml %}

  @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Applying currency format to axis labels
          px=>px.LabelFormat("c")
              //....
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img23.png)


The following table describes the result of applying some commonly used label formats on numeric values. 
 
<table>
<tr>
<td><b>Label Value</b></td>
<td><b>Label Format property value</b></td>
<td><b>Result </b></td>
<td><b>Description </b></td>
</tr>        
<tr>
<td>1000</td>
<td>n1</td>
<td>1000.0</td>
<td>The Number is rounded to 1 decimal place</td>
</tr> 
<tr>
<td>1000</td>
<td>n2</td>
<td>1000.00</td>
<td>The Number is rounded to 2 decimal place</td>
</tr> 
<tr>
<td>1000</td>
<td>n3</td>
<td>1000.000</td>
<td>The Number is rounded to 3 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p1</td>
<td>1.0%</td>
<td>The Number is converted to percentage with 1 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p2</td>
<td>1.00%</td>
<td>The Number is converted to percentage with 2 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p3</td>
<td>1.000%</td>
<td>The Number is converted to percentage with 3 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c1</td>
<td>$1,000.0</td>
<td>The Currency symbol is appended to number and number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c2</td>
<td>$1,000.00</td>
<td>The Currency symbol is appended to number and number is rounded to 2 decimal place</td>
</tr>
</table>


### Format date time values

Date time labels can be formatted by using the **LabelFormat** property of the axis.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Formatting date time labels in date/Month name/Year format
          px=>px.LabelFormat("dd/MMMM/yyyy")
              //....
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img24.png)


The following table describes the result of applying some common date time formats to the labelFormat property

<table>
<tr>
<td><b>Label Value</b></td>
<td><b>Label Format Property Value</b></td>
<td><b>Result </b></td>
<td><b>Description </b></td>
</tr>        
<tr>
<td>new Date(2000, 03, 10)</td>
<td>dddd</td>
<td>Monday</td>
<td>The Date is displayed in day format</td>
</tr> 
<tr>
<td>new Date(2000, 03, 10)</td>
<td>MM/dd/yyyy</td>
<td>04/10/2000</td>
<td>The Date is displayed in month/date/year format</td>
</tr> 
<tr>
<td>new Date(2000, 03, 10)</td>
<td>n3</td>
<td>1000.000</td>
<td>The Number is rounded to 3 decimal place</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>MMM</td>
<td>Apr</td>
<td>The Shorthand month for the date is displayed</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>t</td>
<td>12:00 AM</td>
<td>Time of the date value is displayed as label</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>hh:mm:ss</td>
<td>12:00:00</td>
<td>The Label is displayed in hours:minutes:seconds format</td>
</tr>
</table>

### Custom label format

Prefix and suffix can be added to the category labels by using the LabelFormat property. You can use the *{value}* as placeholder text in your custom text, it is replaced with the corresponding axis label at the runtime.

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Adding prefix and suffix to axis labels
          px=>px.LabelFormat("${value} K")
              //....
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img25.png)


## Common axis features

Customization of features such as axis title, labels, grid lines and tick lines are common to all the axis. Each of these features are explained in this section.

### Axis Crossing

Axis can be positioned anywhere in chart area using the **CrossesAt** property of axis. This property specifies where the horizontal axis should intersect or cross the vertical axis and vice versa. Default value of *CrossesAt* property is null.

{% highlight cshtml %}

	@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Crosses primary Y axis at 0
          px=>px.CrossesAt(0)
              //....
     )
        // ...
	)

{% endhighlight %}

![](Axis_images/axis_img52.png)


#### Crossing a specific Axis

The **CrossesInAxis** property takes axis name as input and determines the axis used for crossing. By default all the horizontal axes crosses in primary Y axis and all the vertical axes crosses in primary X axis.

{% highlight cshtml %}

	@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Crosses secondary vertical axis at -0.2
          px=>px.CrossesAt(-0.2)
		        .CrossesInAxis('SecondaryYAxis')
              //....
     )
        // ...
	)

{% endhighlight %}

![](Axis_images/axis_img53.png)

Axis will be placed in the opposite side if value of *CrossesAt* property is greater than the maximum value of crossing axis (axis name provided through *CrossesInAxis* property or primary Y axis for horizontal axis).

{% highlight cshtml %}

	@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Crosses primary Y axis at 200
          px=>px.CrossesAt(200)
              //....
     )
        // ...
	)

{% endhighlight %}

![](Axis_images/axis_img54.png)

#### Positioning the axis elements while crossing

The `ShowNextToAxisLine` property is used for controlling the axis elements movement along with the axis line while axis crossing is performed. When the showNextToAxisLine is set as false only the axis line and the tick lines are placed at the crossing Value and the axis elements will be placed outside the chart area. The default value of `ShowNextToAxisLine` is **true**.  

{% highlight cshtml %}

	@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Crosses primary Y axis at 0
          px=>px.CrossesAt(0)
          .ShowNextToAxisLine(false)
              //....
     )
        // ...
	)
{% endhighlight %}

The axis is placed at the crossing value without the axis elements 

![](Axis_images/axis_img67.png)


### Axis Visibility

Axis visibility can be controlled by using the **Visible** property of the axis. The default value of the Visible property is **true**. 

{% highlight cshtml %}

  @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryYAxis(
          //Disabling visibility of Y-axis
          px=>px.Visible(false)
              //....
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img26.png)


### Axis title

The **Title** property in the axis provides options to customize the text and font of the axis title. Axis does not display the title, by default. Title text can also be trimmed based on the title text length or specified length.

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Customizing axis title
          px=>px.Title(title=>title.EnableTrim(true)
              .MaximumTitleWidth(80)
              .Text("Month")
              .Font(ft=>ft.Color("grey").
                  FontWeight(ChartFontWeight.Bold)
                  .FontFamily("Segoe UI")
                  .Size("16px")))
              //....
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img27.png)

You can modify the position of the axis title either inside or outside the chart area using the property **Position**. By default, it will be placed outside the chart area. In addition, you can also change the alignment of the title to near, far and center by **Alignment** property, using **Offset** property you can change the position with respect to pixels.

{% highlight cshtml %}

    @(Html.EJ().Chart("container")
      .PrimaryXAxis(pr => pr.Title(title => title
      .AxisTitlePosition(AxisTitlePosition.Inside).Alignment(Alignment.Near).Offset(10))
    ))

{% endhighlight %}

![](Axis_images/axis_img62.png)

### Label customization

The **Font** property of the axis provides options to customize the FontFamily, Color, Opacity, Size and FontWeight of the axis labels.  

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Customizing label appearance
          px=>px.Font(ft=>ft.Color("blue").
                  FontWeight(ChartFontWeight.Bold)
                  .FontFamily("Segoe UI")
                  .Size("14px"))
              //....
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img28.png)

#### Axis Labels Line Break

Axis Labels can be placed in multiple lines by specifying **<br>** for data points x value and in label format.

For category value type, **<br>** can be specified in x value of data points.

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...
      //Initializing Series
      .Series(sr =>
      {
          sr
            .Points(pt =>
            {
                pt.X("India").Y(61.3).Add();
                pt.X("United<br>States<br>of<br>America").Y(31).Add();
                pt.X("South<br>Korea").Y(39.4).Add();
                pt.X("United<br>Arab<br>Emirates").Y(65.1).Add();
                pt.X("United<br>Kingdom").Y(75.9).Add();
            }).Add();
      })
        
        //...
 )

{% endhighlight %}

![](Axis_images/axis_img68.png)

For numeric, datetime and datetimeCategory value type, **<br>** can be specified in labelFormat.

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          px=>px.LabelFormat("MMM<br>dd<br>yyyy").ValueType(AxisValueType.Datetime)
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img69.png)

### Label and tick positioning
 
Axis labels and ticks can be positioned inside or outside the chart area by using the **LabelPosition** and **TickPosition** properties. The labels and ticks are positioned outside the chart area, by default.
 
{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Customizing label and tick positions
          px=>px.AxisLabelPosition(AxisLabelPosition.Inside).TickLinesPosition(TickLinesPosition.Inside)
              //....
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img29.png)


### Edge labels placement

Labels with long text at the edges of an axis may appear partially outside the chart. The **EdgeLabelPlacement** property can be used to avoid the partial appearance of the labels at the corners. 

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Customizing edge label placement
          px=>px.EdgeLabelPlacement(EdgeLabelPlacement.Shift)
              //....
     )
        // ...
 )

{% endhighlight %}

**Chart before setting edge label placement to X-axis**

![](Axis_images/axis_img30.png)


**Chart after setting edge label placement to X-axis**

![](Axis_images/axis_img31.png)


### Grid lines customization

The **MajorGridLines** and **MinorGridLines** properties in the axis are used to customize the major grid lines and minor grid lines of an axis. They provide options to change the Width, Color, Visibility and Opacity of the grid lines. The minor grid lines are not visible, by default.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Customizing grid lines
          px=>px.MajorGridLines(ma=>ma.Color("blue").Visible(true).Width(1))
              .MinorGridLines(mi=>mi.Color("red").Visible(false).Width(1))
              .MinorTicksPerInterval(0)
              //....
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img32.png)


### Tick lines customization

The **MajorTickLines** and **MinorTickLines** properties in the axis are used to customize the major tick lines of an axis and minor tick lines of an axis. They provide options to change the Width, Size, Color and Visibility of the grid lines. The minor tick lines are not visible, by default.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Customizing tick lines
          px=>px.MajorTickLines(ma=>ma.Color("blue").Visible(true).Width(1).Size(5))
              .MinorTickLines(mi=>mi.Color("red").Visible(false).Width(1).Size(5))
              .MinorTicksPerInterval(0)
              //....
     )
        // ...
 )

{% endhighlight %}

![](Axis_images/axis_img33.png)

  
### Inversing axis

Axis can be inversed by using the **IsInversed** property of the axis. The default value of the IsInversed property is **false**.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Inversing the X-axis
          px=>px.IsInversed(false)
              //....
     )
        // ...
 )

{% endhighlight %}

**Chart before inversing the axes**

![](Axis_images/axis_img34.png)


**Chart after inversing the axes**

![](Axis_images/axis_img35.png)
   

### Place axes at the opposite side

The **OpposedPosition** property of axis can be used to place the axis at the opposite side of its default position. The default value of the OpposedPosition property is **false**. 

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Placing axis at the opposite side of its normal position
          px=>px.OpposedPosition(true)
              //....
     )
        // ...
 )

{% endhighlight %}

**Chart with X and Y axes at normal position**

![](Axis_images/axis_img36.png)


**Chart with Y-axis at opposed position**

![](Axis_images/axis_img37.png)


### Maximum number of labels per 100 pixels

A maximum of 3 labels are displayed for each 100 pixels in the axis, by default. The maximum number of labels that is present within the 100 pixels length can be customized by using the **MaximumLabels** property of the axis. This property is applicable only for an automatic range calculation and it does not work when you set the value for Interval property in the axis range.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     .PrimaryXAxis(
          //Maximum number of labels per 100 pixels
          px=>px.MaximumLabels(1)
              //....
     )
        // ...
 )

{% endhighlight %}

**Chart before setting maximum labels per 100 pixels**

![](Axis_images/axis_img38.png)


**Chart after setting maximum labels one per 100 pixels**

![](Axis_images/axis_img39.png)



## Multiple Axis

Multiple axes can be used in the Chart and chart area can be split into multiple panes to draw multiple series with multiple axes.

![](Axis_images/axis_img40.png)


An additional horizontal or vertical axis can be added to the chart by adding an axis instance to the **Axes** collection and then you can associate it to a series by specifying the name of the axis to the **XAxisName** or **YAxisName** property of the series.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     //  Creating a secondary horizontal axis
     .Axes(ax => { ax.Name("SecondaryX").Add(); ax.Name("SecondaryY").Add(); })
     .Series(sr =>
     {
         //  Binding secondary X-axis with a series
         sr.XAxisName("SecondaryX")
             //  Binding secondary Y-axis with a series
             .YAxisName("SecondaryX").Add();
     })
        // ...
 )


{% endhighlight %}



![](Axis_images/axis_img41.png)

[Click](http://mvc.syncfusion.com/demos/web/chart/multipleaxes) here to view the multiple axis online demo sample.


## Smart Axis Labels

When the Axis labels overlap with each other based on the chart dimensions and label size, you can use the **LabelIntersectAction** property of the axis to avoid overlapping. The default value of the LabelIntersectAction is **None**. The other available values of the Label Intersect Actions are **Rotate45**, **Rotate90**, **Trim**, **MultipleRows**, **Wrap** and **Hide**.

{% highlight cshtml %}

 @(Html.EJ().Chart("chartContainer")

      // ...

     // Avoid overlapping of x-axis labels
     .PrimaryXAxis(px=>px.LabelIntersectAction(LabelIntersectAction.MultipleRows)
         
     // ...
 )


{% endhighlight %}



![](Axis_images/axis_img42.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/smartaxislabels) here to view our online demo sample for smart axis labels.



The following screenshot displays the result, when the LabelIntersectAction property is set as **Rotate45**.

![](Axis_images/axis_img43.png)


The following screenshot displays the result, when the LabelIntersectAction property is set as **Rotate90**.

![](Axis_images/axis_img44.png)


The following screenshot displays the result, when the LabelIntersectAction property is set as **Wrap**.

![](Axis_images/axis_img45.png)


The following screenshot displays the result, when of setting the **trim** as value to the LabelIntersectAction property.

![](Axis_images/axis_img46.png)


The following screenshot displays the result, when the LabelIntersectAction property is set as **Hide**.

![](Axis_images/axis_img47.png)


The following screenshot displays the result, when the LabelIntersectAction property is set as **MultipleRows **.

![](Axis_images/axis_img48.png)


The following screenshot displays the result, when the LabelIntersectAction property is set as **WrapByWord**.

![](/js/Chart/Axis_images/axis_img49.png)

## Multi-level Labels
Axis can be customized with multiple levels of labels using the **MultiLevelLabels** property. These labels are placed based on the start and end range values and we can add any number of labels to an axis.

{% highlight cshtml %}     

        @(Html.EJ().Chart("container") 
            .PrimaryXAxis(axis => axis.MultiLevelLabels(multiLevelLabels=> {
                multiLevelLabels.Visible(true).Text("Quarter 1").Start(-0.5).End(2.5).Add();
           })
        ))  

{% endhighlight %}

![](Axis_images/axis_img57.png)

### Customizing the multi-Level labels
The color, width and type of the border can be customized. The default border type is **Rectangle**. And the other supported border types are namely brace, curly brace, without top/bottom border and none. 

{% highlight cshtml %}

     @(Html.EJ().Chart("container")
        .PrimaryXAxis(axis => axis.MultiLevelLabels(
            multiLevelLabels=> {multiLevelLabels. Border(br=>br.Type(MultiLevelLabelBorder.Brace).Width(2).Color("Black"))).Add();
         })
      ))  

{% endhighlight %}

![](Axis_images/axis_img58.png)

The text of the labels can be customized using the **Text** and **Font** properties 

{% highlight cshtml %}

       @(Html.EJ().Chart("container")
        .PrimaryXAxis(axis =>axis.MultiLevelLabels(multiLevelLabels=> {multiLevelLabels.Text("Year - 2015")
            .Font(ft=> ft.FontFamily("Algerian").Size("12px").Color("Black")).Add();
        })
       ))  
     
{% endhighlight %}

![](Axis_images/axis_img59.png)

You can change the alignment of the text to far, near and center position using the **TextAlignment** property. By default, the text will be center aligned. 

{% highlight cshtml %}

        @(Html.EJ().Chart("container")
        .PrimaryXAxis(axis =>axis.MultiLevelLabels(multiLevelLabels=> {
            multiLevelLabels.TextAlignment(Alignment.Far).Add();
         })
        ))  
       
{% endhighlight %}

![](Axis_images/axis_img60.png)

You can trim, wrap or wrapAndTrim the text if it exceeds the maximum text width value using the property **TextOverflow**

{% highlight cshtml %}

       @(Html.EJ().Chart("container")
       .PrimaryXAxis(axis =>axis.MultiLevelLabels(multiLevelLabels=> {
        multiLevelLabels.TextOverflow(TextOverflow.Trim).MaximumTextWidth(40).Add();
       })
      ))  
        
{% endhighlight %}

The below screenshot shows the trimmed multi-level labels

![](Axis_images/axis_img61.png)

And these labels can be placed in various rows using the **Level** property.
[Click](http://mvc.syncfusion.com/demos/web/chart/multilevellabels) here to view the multi-level labels online demo sample.
