---
layout: post
title: Markers and data labels in Essential ASP.NET MVC Chart
description: Learn how to add markers and data point labels to a Chart series.
platform: ejmvc
control: Chart
documentation: ug
---

# Data Markers

Data markers are used to provide information about the data point to the user. You can add a shape and label to adorn each data point.

## Add Shapes

You can add shapes to any chart types but they are often used with line, area and spline series to indicate each data point. It is highlighted when you hover the mouse on the shape.

Shapes can be added to the chart by enabling the Visible option of the **Marker** property. There are different shapes you can add to the chart by using the **Shape** option such as Rectangle, Circle, Diamond etc.

The following code example explains on how to enable series marker and add shapes,

{% highlight cshtml %}


    @(Html.EJ().Chart("chartContainer")
            //...

        .Series(sr =>
        {
            //Adding shapes to series1
            sr
                //...
                .Marker(mr=>mr.Visible(true).Shape(ChartShape.Diamond)).Add();
            //Adding shapes to series2
            sr
                //...
                .Marker(mr => mr.Visible(true).Shape(ChartShape.Triangle)).Add();
            //Adding shapes to series3
            sr
                //...
                .Marker(mr => mr.Visible(true).Shape(ChartShape.Hexagon)).Add();
        })
         //...
     )


{% endhighlight %}

![](Data-Markers_images/Data-Markers_img1.png)


## Add image as marker

Apart from the shapes, you can also add images to mark the data point by using the **ImageUrl** option.

The following code example illustrates this,

{% highlight cshtml %}


    @(Html.EJ().Chart("chartContainer")
            //...

        .Series(sr =>
        {
            //Adding shapes to series1
            sr
                //..
                .Marker(mr=>mr.Visible(true).Shape(ChartShape.Image)
                 .Size(size => size.Height(20).Width(20)).ImageUrl("sun_annotation.png")
                ).Add();
        })
         //...
     )


{% endhighlight %}

![](Data-Markers_images/Data-Markers_img2.png)


## Add labels

Data label can be added to a chart series by enabling the *Visible* property in the **DataLabel** option. The labels appear at the top of the data point, by default.

The following code example shows how to enable data label and set its horizontal and vertical text alignment. 

{% highlight cshtml %}


    @(Html.EJ().Chart("chartContainer")        
        //...

        .Series(sr =>
        {
            //Adding shapes to series1
            sr
                //..
                .Marker(mr=>mr
                    .DataLabel(label=>label
                        //Set text alignment to data label text	
                        .Visible(true)
                        .HorizontalTextAlignment(Syncfusion.JavaScript.DataVisualization.TextAlignment.Center)
                        .VerticalTextAlignment(Syncfusion.JavaScript.DataVisualization.TextAlignment.Far))
                ).Add();
        })
         //...
     )


{% endhighlight %}

![](Data-Markers_images/Data-Markers_img3.png)


Label content can be formatted by using the template option. Inside the template, you can add the placeholder text *"point.x"* and *"point.y"* to display corresponding data points x & y value.

You can adorn the labels with background shapes by setting *Shape* option.

The following code example shows how to add background shapes and set template to data label.

{% highlight cshtml %}


<div id="template">
     <div id="left">
	<img src="../images/chart/icon_investments.png"/>
     </div>
     <div id="right">
          <div id="point">#point.y#%</div>
     </div>
</div>

    @(Html.EJ().Chart("chartContainer")
            //...

        .Series(sr =>
        {
            //Adding shapes to series1
            sr
                //..
                .Marker(mr=>mr
                    .DataLabel(label=>label
                        .Visible(true)
                         //Set template to data label
                         .Template("template"))
                ).Add();
             //Adding shapes to series2
            sr
                //..
                .Marker(mr=>mr
                    .DataLabel(label=>label
                        .Visible(true)
                    //Add background shape to the data label
                    .Shape(ChartShape.Rectangle).Border(br=>br.Width(1).Color("red"))
                        )
                ).Add();
             //Adding shapes to series3
            sr
                //..
                .Marker(mr=>mr
                    .DataLabel(label=>label
                        .Visible(true))                         
                ).Add();
        })
         //...
     )


{% endhighlight %}

![](Data-Markers_images/Data-Markers_img4.png)


The appearance of the labels can be customized by using the *Font* and *Offset* options. The Offset option is used to move the labels vertically. Also, labels can be rotated by using the *Rotate* option.

The following code example shows how to rotate data label text and customize the font.

{% highlight cshtml %}


    @(Html.EJ().Chart("chartContainer")
            //...

        .Series(sr =>
        {
            //Adding shapes to series1
            sr
                //..
                .Marker(mr=>mr
                    .DataLabel(label=>label
                        .Visible(true)
                        //Rotate data label and customize the font
                        .Angle(300)
                        .Offset(15)
                        .Font(font=>font.Color("black").Size("13px"))
                        )
                ).Add();
        })
         //...
     )


{% endhighlight %}

![](Data-Markers_images/Data-Markers_img5.png)


You can position the label to the top, center or bottom position of the segment by using the **TextPosition** option for the chart types such as Column, Bar, Stacked bar, Stacked column, 100% Stacked bar, 100% Stacked column, Candle and OHLC.

The following code example shows how to set textPosition to display data label in the middle of the column rectangle.

{% highlight cshtml %}


    @(Html.EJ().Chart("chartContainer")
            //...

        .Series(sr =>
        {
            //Adding shapes to series1
            sr
                //..
                .Marker(mr=>mr
                    .DataLabel(label=>label
                        .Visible(true)
                    // Place the data label text position in the center of the rectangle
                    .TextPosition(TextPosition.Middle)
                        )
                ).Add();
        })
         //...
     )


{% endhighlight %}

![](Data-Markers_images/Data-Markers_img6.png)

The label can be positioned inside or outside the perimeter of the series by using the **LabelPosition** option for the chart types such as Pie and Doughnut, .

The following code example shows how to set the LabelPosition,

{% highlight cshtml %}


    @(Html.EJ().Chart("chartContainer")
            //...

        .Series(sr =>
        {
            //Adding shapes to series1
            sr
                .Points(pt=>{
                    pt.X("India").Y(24).Text("India 24%").Add();
                    pt.X("Japan").Y(25).Text("Japan 25%").Add();
                    pt.X("Australia").Y(20).Text("Australia 20%").Add();
                    pt.X("USA").Y(35).Text("USA 35%").Add();
                    pt.X("China").Y(23).Text("China 23%").Add();
                    pt.X("Germany").Y(27).Text("Germany 27%").Add();
                    pt.X("France").Y(22).Text("France 22%").Add();
                })
                .Marker(mr=>mr
                    .DataLabel(label=>label
                        .Visible(true)
                       .Shape(ChartShape.Rectangle)
                        .Font(font=>font.Color("white"))
                        )
                )
                //Display data label outside position 
                .LabelPosition(ChartLabelPosition.Outside)
                .Type(SeriesType.Doughnut).Add();
        })
         //...
     )


{% endhighlight %} 

![](Data-Markers_images/Data-Markers_img7.png)


The following screenshot displays the labels when the LabelPosition is set as *Inside* position.

![](/js/Chart/Data-Markers_images/Data-Markers_img8.png)


The following screenshot displays the labels when the LabelPosition is set as *OutsideExtended* position.

![](Data-Markers_images/Data-Markers_img9.png)


The label can be wrapped for pie, doughnut, funnel, and pyramid series by setting the enableWrap property. 

{% highlight javascript %} 

@(Html.EJ().Chart("chartContainer") 
                           //.... . . 
              .Series(sr => {
                  //Adding series 
                       sr.Marker(mr => mr.DataLabel(label=>
                              label.Visible("true")
                                 .EnableWrap("true")
                                 .MaximumLabelWidth(32)
                         ))
                                 //.... . . 

               }).Add(); 
                           //.... . . 
     }) 
)


{% endhighlight %} 

![](Data-Markers_images/Data-Markers_img13.png)


## Binding label from the datasource

You can bind the text value to the datalabel from the datasource and then you need to map the text value field with the **TextMappingName** property respectively.

{% highlight cshtml %}

//data source for chart with label 
var chartData = [
          { month: 'Jan', sales: 35 , text: 'January'}, 
          { month: 'Feb', sales: 28 , text: 'February'}
          //..
          ];
          
    function onChartLoad(sender) {
        var data = GetData();
        sender.model.series[0].dataSource = chartData;
        sender.model.series[0].xName = "month";
        sender.model.series[0].yName = "sales";
    }

@(Html.EJ().Chart("chartContainer") 
                           //.... . . 
              .Series(sr => {                      
                       sr.Marker(mr => mr.DataLabel(label=>
                              label.Visible("true")
                              .TextMappingName("text")                                                                  
                         ))
                       .Add();                     
                      //.... . . 
               })
               .Load("onChartLoad")
            //.... 
     }) 
)


{% endhighlight %}


## Binding fill color to the points from the datasource

You can bind the color value to the points from the datasource and then you need to map the color value field to the **PointColorMappingName** property respectively.

{% highlight cshtml %}

//data source for chart with fill color
var chartData = [
          { month: 'Jan', sales: 35 , color: 'red'}, 
          { month: 'Feb', sales: 28 , color: 'blue'}
          //..
          ];
          
    function onChartLoad(sender) {
        var data = GetData();
        sender.model.series[0].dataSource = chartData;
        sender.model.series[0].xName = "month";
        sender.model.series[0].yName = "sales";
    }

@(Html.EJ().Chart("chartContainer") 
                           //.... . . 
              .Series(sr => {
                      //Mapping the color values to the points
                      sr.PointColorMappingName("color") .Add();                     
                      //.... . . 
               })
               .Load("onChartLoad")
            //.... 
     }) 
)


{% endhighlight %}

## Customize specific points

By using the ejChart, you can also customize the individual/specific markers with different colors, shapes and also with different images.

There are two ways to achieve this based on how the data is fed to the series.

When the data is provided by using the Points option, you can add marker for each data point or specific point by using the Marker option as illustrated in the following code example.

{% highlight cshtml %}


    @(Html.EJ().Chart("chartContainer")
            //...

        .Series(sr =>
        {
            //Adding shapes to series1
            sr
                .Points(pt=>{
                    pt.X("Jan").Y(35).Add();
                    pt.X("Feb").Y(28).Add();
                    pt.X("Mar").Y(34).Add();
                    pt.X("Apr").Y(32).Add();
                    pt.X("May").Y(40).Add();
                    pt.X("Jun").Y(32).Add();
                    pt.X("Jul").Y(35).Add();
                    pt.X("Aug").Y(55).Marker(mr=>mr
                        //Enable and customize the data label for a point
                        .DataLabel(label=>label.Visible(true).Offset(-10).Shape(ChartShape.UpArrow)
                        .Font(font=>font.Color("white").Size("11px"))
                        .Margin(margin=>margin.Right(15).Left(15).Top(10).Bottom(10))
                        .Fill("green"))
                        ).Add();
                    pt.X("Sep").Y(38).Add();
                    pt.X("Oct").Y(30).Add();
                    pt.X("Nov").Y(25).Marker(mr => mr
                        //Enable and customize the data label for a point
                       .DataLabel(label => label.Visible(true).Offset(-22).Shape(ChartShape.DownArrow)
                           .VerticalTextAlignment(Syncfusion.JavaScript.DataVisualization.TextAlignment.Near)
                       .Font(font => font.Color("white").Size("11px"))
                       .Margin(margin => margin.Right(15).Left(15).Top(10).Bottom(10))
                       .Fill("red"))
                       ).Add();
                    pt.X("Dec").Y(32).Add();
                }).Add();
        })
         //...
     )


{% endhighlight %}

![](Data-Markers_images/Data-Markers_img10.png)


When the data is bound to the series by using the DataSource option, you can customize the points in the **SeriesRendering** event as illustrated in the following code example,

{% highlight cshtml %}


    @(Html.EJ().Chart("chartContainer")
            //...

        .Series(sr =>
        {
            //Adding shapes to series1
            sr
               //Add datasource and set xName and yName 
               .XName("Month").YName("Sales")
               .DataSource(ViewBag.ChartData)
               .Add();
           })
           //Fires on rendering the series
           .SeriesRendering("onSeriesRender")
         //...
     )
     
{% endhighlight %}


{% highlight js %}
    //Define the seriesRendering client side event
  
     function onSeriesRender(sender) {
 
        
        //Enable and customize the dataLabel for a point using event

            sender.data.series.points[7].marker = {
               dataLabel: {
                    visible: true,
                    offset: -10,
                    shape: "upArrow", font: { color: "white", size: '11px' },
                    margin: { left: 15, right: 15, top: 10, bottom: 10 },                    
                    fill: "green"
                }};

            sender.data.series.points[10].marker = {
                 //Enable and customize the dataLabel for a point using event
                dataLabel: {
                        visible: true,
                        offset: -22,
                        verticalTextAlignment: 'near',
                        shape: "downArrow", font: { color: "white", size: '11px' },
                        margin: { left: 15, right: 15, top: 10, bottom: 10 },                    
                        fill: "red"
                }};
        }

{% endhighlight %}

![](Data-Markers_images/Data-Markers_img10.png)


## Connect Line

This feature is used to connect label and data point by using a line. It can be enabled only for Pie, Doughnut, Pyramid and Funnel chart types. **ConnectorLine** types can be set as *Bezier* or *Line* by using the **Type** option.

 The following code example illustrates this,

{% highlight cshtml %}


    @(Html.EJ().Chart("chartContainer")
            //...

        .Series(sr =>
        {
            //Adding shapes to series1
            sr
               .Marker(mr=>mr.DataLabel(label=>label
                   // Set connector line type and customize the color
                   .ConnectorLine(cl=>cl.Color("black").Type(ConnectorType.Bezier))
                   ))
                   .LabelPosition(ChartLabelPosition.OutsideExtended)
                   .Type(SeriesType.Doughnut)
               .Add();
           })
           //Fires on rendering the series
           .SeriesRendering("onSeriesRender")
         //...
     )


{% endhighlight %}

![](Data-Markers_images/Data-Markers_img11.png)


## Smart labels

Overlapping of the labels can be avoided by enabling the **EnableSmartLabels** property. The default value is *True* for *Accumulation type series* and *False* for *other series types*.

The following code example shows how to enable smart labels,

{% highlight cshtml %}


   @(Html.EJ().Chart("chartContainer")
          .Series(sr =>
                    {
                        sr
                           //...
                           .EnableSmartLabels(true).StartAngle(145)
                                          .Marker(mr =>
                                          {
                                              mr.DataLabel(label =>
                                              {
                                                  label.Visible(true).ConnectorLine(cl => cl.Color("black")
                                                      .Height(60).Type(ConnectorType.Bezier)).Shape(ChartShape.None)
                                                      .Font(font => { font.Size("14px"); });
                                              });
                                          }).Name("Expenses").Type(SeriesType.Pie).Add();
                    })
                    //...
         )


{% endhighlight %}

![](Data-Markers_images/Data-Markers_img12.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/pie) here to view the SmartLabel online demo sample.