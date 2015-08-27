---
layout: post
title: Getting-Started
description: getting started
platform: ejmvc
control: Chart
documentation: ug
---

# Getting Started

This section explains briefly you on how to create a Chart in your application with ASP.NET MVC.

## Create your first Chart in ASP.NET MVC

This section encompasses how to configure the MVC Charts for your business needs. You can also pass the required data to default Chart and customize it according to your requirements. In this example, you can see how to display the average climate data for Washington, DC during the period 1961 -1990.





![](Getting-Started_images/Getting-Started_img1.png)



### Configure Chart

Getting started with your MVC Chart is very easy. You can start by creating a simple line Chart.

1. Create an MVC Project and add necessary Dll’s and Scripts by referring [MVC-Getting Started](http://docs.syncfusion.com/aspnetmvc/chart/getting-started) Documentation.
2. You can create a simple div tag.

{% highlight html %}
<div>

</div>
{% endhighlight  %}


3. You can add the following code in the index.cshtml file to create the Chart control in the View page. 

{% highlight html %}
    <div> 



           @(Html.EJ().Chart("chartcontainer")



           ) 

    </div> 

{% endhighlight  %}

The above code example renders a Chart with the default Columnseries type and some random values assigned to the column series. 

The following screenshot displays the Chart.



![](Getting-Started_images/Getting-Started_img2.png)



### Add a Chart series

By default, line series is used. To create a series, you need to add the following code example to the scripts. For example, the following steps illustrate how to add a column series to the Chart.

1. You need to add the name of the series displayed in the Chart legend.
2. Then, you need to specify the type of series you want to render using “type” property.
3. You can add x and y points to the series as in the following code example.

{% highlight html %}
  @(Html.EJ().Chart("chartcontainer")

     .Series(sr =>

            {

                sr.Points(pt =>

                    {

                        pt.X("Jan").Y(3.03).Add();

                        pt.X("Feb").Y(2.48).Add();

                        pt.X("Mar").Y(3.23).Add();

                        pt.X("Apr").Y(3.15).Add();

                        pt.X("May").Y(4.13).Add();

                        pt.X("Jun").Y(3.23).Add();

                        pt.X("Jul").Y(4.13).Add();

                        pt.X("Aug").Y(4.88).Add();

                        pt.X("Sep").Y(3.82).Add();

                        pt.X("Oct").Y(3.07).Add();

                        pt.X("Nov").Y(2.83).Add();

                        pt.X("Dec").Y(2.8).Add();

                    }).Name("Precipitation").Type(SeriesType.Column).Add();

            })



        )

{% endhighlight  %}
The following screenshot displays a Chart series:


![](Getting-Started_images/Getting-Started_img3.png)



### Add JSON data to the Chart

You can add JSON data to the Chart using the datasource property in Chart series.

In Controllers/HomeController.cs.

{% highlight c# %}

public ArrayList GetData()

        {

            ArrayList dataTable = new ArrayList();



            dataTable.Add(new ChartData("Jan", 42, 27, 3.03));

            dataTable.Add(new ChartData("Feb", 44, 28, 2.48));

            dataTable.Add(new ChartData("Mar", 53, 35, 3.23));

            dataTable.Add(new ChartData("Apr", 64, 44, 3.15));

            dataTable.Add(new ChartData("May", 75, 54, 4.13));

            dataTable.Add(new ChartData("Jun", 83, 63, 3.23));

            dataTable.Add(new ChartData("Jul", 87, 68, 4.13));

            dataTable.Add(new ChartData("Aug", 84, 66, 4.88));

            dataTable.Add(new ChartData("Sep", 78, 59, 3.82));

            dataTable.Add(new ChartData("Oct", 67, 48, 3.07));

            dataTable.Add(new ChartData("Nov", 55, 38, 2.83));

            dataTable.Add(new ChartData("Dec", 45, 29, 2.8));

            return dataTable;

        }



    private class ChartData

        {

            private String xmonth;



            public String Xmonth

            {

                get { return xmonth; }

                set { xmonth = value; }

            }



            private double precipitation;



            public double Precipitation

            {

                get { return precipitation; }

                set { precipitation = value; }

            }



            private double high;



            public double High

            {

                get { return high; }

                set { high = value; }

            }



            private double low;



            public double Low

            {

                get { return low; }

                set { low = value; }

            }



            public ChartData(String xdate, double high, double low, double precipitation)

            {

                this.Xmonth = xdate;

                this.Precipitation = precipitation;

                this.High = high;

                this.Low = low;

            }

        }



        public ActionResult Index()

        {

            var DataSource = GetData();

            ViewBag.datasource = DataSource;

            return View();

        }

{% endhighlight  %}

In Index.cshtml


{% highlight html %}


@(Html.EJ().Chart("chartcontainer")

        .Series(sr =>

                    {

                        sr.Name("Precipitation")

                          .Type(SeriesType.Column)



                         .DataSource((System.Collections.IEnumerable)ViewBag.datasource)

                         .XName("Xmonth")

                         .YName("Precipitation")

                          .Add();

                        sr.Name("Low")

                        .Type(SeriesType.Line)

                         .DataSource((System.Collections.IEnumerable)ViewBag.datasource)

                         .XName("Xmonth")

                         .YName("Low")

                          .Add();

                        sr.Name("High")

                          .Type(SeriesType.Line)

                         .DataSource((System.Collections.IEnumerable)ViewBag.datasource)

                         .XName("Xmonth")

                         .YName("Low")



                          .Add();



                    })

       )

{% endhighlight  %}

The following screenshot displays the Chart when JSON data is added.



![](Getting-Started_images/Getting-Started_img4.png)



### Add Chart Axis of your choice

In the Chart when JSON is added, the axes are provided explicitly and the Chart initializes the right axis based on the data type. You can also specify the axis type of your choice using ValueType option and customize the options available in the axis. The following axis types are supported:

* Category -   String data can be plotted using category axis. Category axis can be initialized only as x-axis.
* Double -   Numeric values can be plotted using double axis.
* Datetime - DateTime can be plotted using datetime axis. This type of axis can be initialized only as x-axis.
* Logarithmic - Numeric values can be plotted using logarithm axis.

You can use PrimaryXAxis and PrimaryYAxis options to initialize the axes. As the data contains string values along x-axis, you can set ValueType as category for PrimaryXAxis and double for PrimaryYAxis. 

Since the values are in Farenheit for Temperature and Inches for Precipetation, you need to initialize different axis instance for each unit. You can use “LabelFormat” option to add suffix for axis labels.

In order to add additional Axes to the Chart other than PrimaryXAxis and PrimaryYAxis, you need to initialize axes option with collection of axis and set Name for axis in the Axes collection.

The following code example illustrates how to add Chart axis.

{% highlight html %}

@(Html.EJ().Chart("chartcontainer")

          .PrimaryXAxis(xAxis => xAxis.ValueType(AxisValueType.Category))



          .PrimaryYAxis(yAxis => yAxis.ValueType(AxisValueType.Double)

                                .LabelFormat("{value}°F")

                                .Range(range => range.Min(0).Max(120).Interval(20)))



          .Axes(additionalAxis => additionalAxis.Orientation(Orientation.Vertical)

                                 .OpposedPosition(true)

                                 . Name("Precipitation")

                                 .Range(range => range.Min(0).Max(6).Interval(1))

                                 .LabelFormat("{value} inch").Add())    

         // ...             

       )
{% endhighlight  %}

### Assign the axis to the respective series

To assign the axis to the respective series you can set YAxisName property of the series. In the following code example, YAxisName of Column series is set to “Precipitation”. This is the name set to the axis in the above code example.




{% highlight html %}


@(Html.EJ().Chart("chartcontainer")

         // ...             

        .Series(sr =>

                    {

                        sr.Name("Precipitation")

                          .Type(SeriesType.Column)

                         .DataSource((System.Collections.IEnumerable)ViewBag.datasource)

                         .XName("Xmonth")

                         .YName("Precipitation")



.YAxisName("Precipitation").Add();

                        sr.Name("Low")

                          .Type(SeriesType.Line)

                         .DataSource((System.Collections.IEnumerable)ViewBag.datasource)

                         .XName("Xmonth")

                         .YName("Low")

                          .Add();

                        sr.Name("High")

                          .Type(SeriesType.Line)

                         .DataSource((System.Collections.IEnumerable)ViewBag.datasource)

                         .XName("Xmonth")

                         .YName("High")

                          .Add();



                    })

        )

{% endhighlight  %}

The following screenshot displays a Chart with desired output.



![](Getting-Started_images/Getting-Started_img5.png)



### Add Data Labels

Data Labels display the series points in Chart. To display the data labels, you need to enable the “Visible” property of DataLabel in the Marker of specific series. By default, it displays the Y value with label format provided in axis (For example: 4.88 inch). The following code example shows how to add DataLabels.




{% highlight html %}


@(Html.EJ().Chart("chartcontainer")

        .Series(sr =>

                    {

                     // ...

                        sr.Name("Precipitation")

                       .Marker(marker => marker.DataLabel(datalabel => datalabel

                                              .Visible(true)

                                              .TextPosition(TextPosition.Top)

                                              .Fill("#FF7777")

                                              .Offset(20)

                                              .Shape(ChartShape.Rectangle)

                                              .Font(ft => ft.Color("white"))

                                     )).Add();

                       // ...             

                    })

        )

{% endhighlight  %}

The following screenshot displays the Chart when data Labels are enabled.



![C:/Users/labuser/Desktop/label.png](Getting-Started_images/Getting-Started_img6.png)



### Enable Tooltip

To display the tooltip of Chart series, you can enable the “Visible” property of “Tooltip” in the specific series. By default, it displays XandY value of points on mouse over the points. The following code example shows how to enable Tooltip.



{% highlight html %}

@(Html.EJ().Chart("chartcontainer")

        .Series(sr =>

                    {

                        sr.Name("Precipitation")

                        // ...             

                          .Tooltip(tt=>tt.Visible(true)).Add();    

                       // ...             

                    })

        )

{% endhighlight  %}

The following screen shot displays the Chart when tooltip is enabled.



![C:/Users/labuser/Desktop/tool.png](Getting-Started_images/Getting-Started_img7.png)



