---
layout: post
title: Chart-Types
description: chart types
platform: ejmvc
control: Chart
documentation: ug
---

# Chart Types

Essential Chart control supports more than 20 types of Chart for your business requirements. Each one is highly and easily configurable with built-in support for creating stunning visual effects.

Chart types are specified on each series through the Type property. All the Chart types are required to have at least one x and one y value. Certain Chart types require more than one y value.

You can combine several Chart types in one Chart using the Type property on series to set different Chart types for each series.

{% highlight html %}

[MVC]



@(Html.EJ().Chart("chartcontainer")   



.Series(ser=>

            {

              ser.Name("columnSeries").Type(SeriesType.Column).Add();

              ser.Name("lineSeries").Type(SeriesType.Line).Add();

            })



              //.......

)


{% endhighlight  %}
In multiple series case, you can use CommonSeriesOptions property to specify the properties that are common for all series in Chart. 

{% highlight html %}
[MVC]



 @(Html.EJ().Chart("chartcontainer")   

              .CommonSeriesOptions(cr=>cr.Type(SeriesType.Line).EnableAnimation(false).Marker(mr=>mr.Shape(ChartShape.Circle).Size(sz=>sz.Height(10).Width(10)).Visible(true)))                



//.......



)
{% endhighlight  %}

## Line Chart

Line Charts join points on a plot using straight lines showing trends in data at equal intervals. Line Charts treats the input as non-numeric, categorical information, equally spaced along the x-axis.

You can configure the appearance of the lines and the points with options Fill used and Width of line.



![](Chart-Types_images/Chart-Types_img1.png)


{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer") 



  .Series(ser=>

            {     

              ser.Name("India").Type(SeriesType.Line).Points(po =>

                    {

                        po.X(2005).Y(28).Add();

                        po.X(2006).Y(35).Add();

                        po.X(2007).Y(42).Add();

                        po.X(2008).Y(37).Add();

                        po.X(2009).Y(41).Add();

                        po.X(2010).Y(35).Add();

                        po.X(2011).Y(37).Add();

                    }).Add();                

            })

              //.......

)
{% endhighlight  %}

## StepLine Chart

Step Line Charts use horizontal and vertical lines to connect data points resulting in a step like progression. You can configure the appearance of line using Fill and Width property in series.



![](Chart-Types_images/Chart-Types_img2.png)

{% highlight html %}

[MVC]



@(Html.EJ().Chart("chartcontainer") 



  .Series(ser=>

            {         

              ser.Name("India").Type(SeriesType.StepLine).Points(po =>

                    {

                        po.X(2006).Y(430).Add();

                        po.X(2007).Y(416).Add();

                        po.X(2008).Y(404).Add();

                        po.X(2009).Y(390).Add();

                        po.X(2010).Y(376).Add();

                        po.X(2011).Y(362).Add();

                        po.X(2012).Y(351).Add();                    

                     }).Add();                

            })

              //.......

)
{% endhighlight  %}

## Area Chart

Area Chart is rendered using a collection of line segments connected to form a closed-loop area filled with a specified color.You can plot multiple series on the same Chart. You can use Fill in series to customize the series color and the Border to customize the series border color and width.



![](Chart-Types_images/Chart-Types_img3.png)

{% highlight html %}

[MVC]



@(Html.EJ().Chart("chartcontainer") 



  .Series(ser=>

            {                        

             ser.Name("Product B").Type(SeriesType.Area).Points(po =>

                    {

                        po.X(1900).Y(2.6).Add();

                        po.X(1920).Y(2.8).Add();

                        po.X(1940).Y(2.6).Add();

                        po.X(1960).Y(3).Add();

                        po.X(1980).Y(3.6).Add();

                        po.X(2000).Y(3).Add();

                    }).Add();



            ser.Name("ProductC").Type(SeriesType.Area).Points(po =>

                {

                    po.X(1900).Y(2.8).Add();

                    po.X(1920).Y(2.5).Add();

                    po.X(1940).Y(2.8).Add();

                    po.X(1960).Y(3.2).Add();

                    po.X(1980).Y(2.9).Add();

                    po.X(2000).Y(2).Add();

                }).Add();                

            })

              //.......

)
{% endhighlight  %}

## Range Area Chart

Range Area Charts are similar to regular area Charts except that, each area is rendered over a range.  Specify the y-axis high and low values for each point for the Range Area Chart. You can customize the series color and borderusing Fill and Border properties in series.



![](Chart-Types_images/Chart-Types_img4.png)



{% highlight html %}

[MVC]



@(Html.EJ().Chart("chartcontainer") 



  .Series(ser=>

            {                        

             ser.Name("Product B").Type(SeriesType.RangeArea.Points(po =>

                    {

                        po.X(1900).High(4).Low(2).Add();

                        po.X(1920). High (4.5). Low(2.5).Add();

                        po.X(1940). High (5). Low(3).Add();

                        po.X(1960). High (5.3). Low(3.3).Add();

                        po.X(1980). High (5). Low(3).Add();

                        po.X(2000). High (4.5). Low(2.5).Add();

                        po.X(2020). High (4). Low(2).Add();

                    }).Add();



            ser.Name("ProductC").Type(SeriesType.RangeArea).Points(po =>

                {

                    po.X(1900).High(2).Low(0).Add();

                    po.X(1920). High (2.5). Low(0.5).Add();

                    po.X(1940). High (3). Low(1).Add();

                    po.X(1960). High (3.3). Low(1.3).Add();

                    po.X(1980). High (3). Low(1).Add();

                    po.X(2000). High (2.5). Low(0.5).Add();

                    po.X(2020). High (2). Low(0).Add();

                }).Add();                

            })

              //.......

)

{% endhighlight  %}

## StepArea Chart

Step Area Charts are similar to regular area Charts except that, instead of a straight line tracing the shortest path between points, the values are connected by continuous vertical and horizontal lines forming a step like progression. You can use the Fill and Border properties in series to customize the series color and border.



![](Chart-Types_images/Chart-Types_img5.png)


{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer") 



  .Series(ser=>

            {                        

              ser.Name("Brazil").Type(SeriesType.StepArea).Points(po =>

                    {

                        po.X(2000).Y(416).Add();

                        po.X(2001).Y(490).Add();

                        po.X(2002).Y(470).Add();

                        po.X(2003).Y(500).Add();

                        po.X(2004).Y(449).Add();

                        po.X(2005).Y(470).Add();

                        po.X(2006).Y(437).Add();

                        po.X(2007).Y(458).Add();

                        po.X(2008).Y(500).Add();

                        po.X(2009).Y(473).Add();

                        po.X(2010).Y(520).Add();

                        po.X(2011).Y(509).Add();

                    }).Add(); 

              })   

        //.......

   )
{% endhighlight  %}

## SplineArea Chart

Spline Area Chart is similar to an Area Chart except the difference in the way the points of a series are connected. It connects each series of points by a smooth spline curve. You can plot multiple series on the same Chart. To customize the series color and border, use the Fill and Border properties in series.



![](Chart-Types_images/Chart-Types_img6.png)

{% highlight html %}

[MVC]



@(Html.EJ().Chart("chartcontainer") 



  .Series(ser=>

            {                                        

              ser.Name("US").Type(SeriesType.SplineArea).Points(po =>

                    {

                        po.X(2002).Y(2.2).Add();

                        po.X(2003).Y(3.4).Add();

                        po.X(2004).Y(2.8).Add();

                        po.X(2005).Y(1.6).Add();

                        po.X(2006).Y(2.3).Add();

                        po.X(2007).Y(2.5).Add();

                        po.X(2008).Y(2.9).Add();

                        po.X(2009).Y(3.8).Add();

                        po.X(2010).Y(1.4).Add();

                        po.X(2011).Y(3.1).Add();

                    }).Add();



             ser.Name("Germany").Type(SeriesType.SplineArea).Points(po =>

                {

                    po.X(2002).Y(0.8).Add();

                    po.X(2003).Y(1.3).Add();

                    po.X(2004).Y(1.1).Add();

                    po.X(2005).Y(1.6).Add();

                    po.X(2006).Y(2).Add();

                    po.X(2007).Y(1.7).Add();

                    po.X(2008).Y(2.3).Add();

                    po.X(2009).Y(2.7).Add();

                    po.X(2010).Y(1.1).Add();

                    po.X(2011).Y(2.3).Add();

                }).Add();                 

          })   

        //.......

   )

{% endhighlight  %}

## StackingArea Chart

Stacking Area Charts are similar to regular area Charts except that the Y values stack on top of each other in the specified series order. This enables you to visualize the relationship of parts to the whole. You can customize the series color and border using Fill and Border properties in series.



![](Chart-Types_images/Chart-Types_img7.png)

{% highlight html %}

[MVC]



@(Html.EJ().Chart("chartcontainer") 



  .Series(ser=>

            {                                                      

              ser.Name("US").Type(SeriesType.StackingArea).Points(po =>

                    {

                        po.X(2002).Y(6).Add();

                        po.X(2003).Y(7.5).Add();

                        po.X(2004).Y(6).Add();

                        po.X(2005).Y(6.5).Add();

                        po.X(2006).Y(7.4).Add();

                        po.X(2007).Y(7.9).Add();

                        po.X(2008).Y(7.5).Add();

                        po.X(2009).Y(8.5).Add();

                        po.X(2010).Y(4.8).Add();

                        po.X(2011).Y(9.3).Add();

                    }).Add();



             ser.Name("Indonesia").Type(SeriesType.StackingArea).Points(po =>

                {

                    po.X(2002).Y(3.5).Add();

                    po.X(2003).Y(4.9).Add();

                    po.X(2004).Y(3.7).Add();

                    po.X(2005).Y(7.5).Add();

                    po.X(2006).Y(4.8).Add();

                    po.X(2007).Y(2.6).Add();

                    po.X(2008).Y(4.7).Add();

                    po.X(2009).Y(3.7).Add();

                    po.X(2010).Y(3.5).Add();

                    po.X(2011).Y(3.6).Add();

                }).Add();    



          })   

        //.......

   )
{% endhighlight  %}

## 100% Stacking area chart  

100% Stacking area is similar to the stacking area chart. But here, the series display multiple data series as stacked areas and the cumulative portion of each stacked element is summed to 100%.  
{% highlight html %}
[MVC]

[CSHTML]

@(Html.EJ().Chart("container")	 

   .Series(sr =>

       {

          sr.Points(pt =>

                  {

                     pt.X("2006").Y(34).Add();

                     pt.X("2007").Y(20).Add();

                     pt.X("2008").Y(40).Add();

                     pt.X("2009").Y(51).Add();

                     pt.X("2010").Y(26).Add();

                     pt.X("2011").Y(37).Add();

                     pt.X("2012").Y(54).Add();

                     pt.X("2013").Y(44).Add();

                     pt.X("2014").Y(48).Add();                       

                    }).Name("USA").Type(SeriesType.StackingArea100).Add();

         sr.Points(pt =>

                {

                    pt.X("2006").Y(51).Add();

                    pt.X("2007").Y(26).Add();

                    pt.X("2008").Y(37).Add();

                    pt.X("2009").Y(51).Add();

                    pt.X("2010").Y(26).Add();

                    pt.X("2011").Y(37).Add();

                    pt.X("2012").Y(43).Add();

                    pt.X("2013").Y(23).Add();

                    pt.X("2014").Y(55).Add();

                 }).Name("India").Type(SeriesType.StackingArea100).Add();  

)

{% endhighlight  %}

The following screenshot displays the 100% Stacking area chart.

![C:/Users/Giftline/Desktop/a.png](Chart-Types_images/Chart-Types_img8.png)



## Column Chart

Column Charts are among the most common Chart types that are used. It uses vertical bars (columns) to display different values of one or more items. It is similar to a bar Chart except that the bars are vertical and not horizontal as in bar Chart. Points from adjacent series are drawn as bars next to each other. You can customize the series color and borderusing Fill and Border properties in series and each segment of series using Fill and Border properties in point.



![](Chart-Types_images/Chart-Types_img9.png)


{% highlight html %}
[MVC]



 @(Html.EJ().Chart("chartcontainer") 



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



             ser.Name("Silver").Type(SeriesType.Column).Points(po =>

                {

                    po.X("USA").Y(70).Add();

                    po.X("China").Y(60).Add();

                    po.X("Japan").Y(60).Add();

                    po.X("Australia").Y(56).Add();

                    po.X("France").Y(45).Add();

                    po.X("Germany").Y(30).Add();

                    po.X("Italy").Y(35).Add();

                    po.X("Sweden").Y(25).Add();

                }).Add();    

          })   

        //.......

   )
{% endhighlight  %}

## RangeColumn Chart

RangeColumn Chart is similar to the Column Chart except that each column is rendered over a range. Specify the y-axis Starting and Ending values for each point for the RangeColumn Chart. You can customize the series color and borderusing Fill and Border properties in series and each segment of series using Fill and Border properties in point.



![](Chart-Types_images/Chart-Types_img10.png)


{% highlight html %}
[MVC]



 @(Html.EJ().Chart("chartcontainer") 



  .Series(ser=>

            {                                                      

              ser.Name("India).Points(po =>

                    {

                        po.X("Jan").Low(0.7).High(6.1).Add();

                        po.X("Feb").Low(1.3).High(6.3).Add();

                        po.X("Mar").Low(1.9).High(8.5).Add();

                        po.X("Apr").Low(3.1).High(10.8).Add();

                        po.X("May").Low(5.7).High(14.4).Add();

                    }).Add();



                ser.Name("Germany").Points(po =>

                {

                    po.X("Jan").Low(1.7).High(7.1).Add();

                    po.X("Feb").Low(1.9).High(7.7).Add();

                    po.X("Mar").Low(1.2).High(7.5).Add();

                    po.X("Apr").Low(2.5).High(9.8).Add();

                    po.X("May").Low(4.7).High(11.4).Add();

                }).Add();    

          })   

        //.......

   )
{% endhighlight  %}

## StackingColumn Chart

Stacking Column Charts are similar to regular column Charts except that the Y values stack on top of each other in the specified series order. This enables you to visualize the relationship of parts to the whole.You can customize the series color and borderusing Fill and Border properties in series and each segment of series using Fill and Border properties in point.



![](Chart-Types_images/Chart-Types_img11.png)


{% highlight html %}
[MVC]



 @(Html.EJ().Chart("chartcontainer") 



  .Series(sr =>

            {

             sr.Points(pt =>

              {

                 pt.X("Jan").Y(900).Add();

                 pt.X("Feb").Y(820).Add();

                 pt.X("Mar").Y(880).Add();

                 pt.X("Apr").Y(725).Add();

                 pt.X("May").Y(765).Add();                 

               }).Name("Google").Type(SeriesType.StackingColumn).Add();



              sr.Points(pt =>

               {

                  pt.X("Jan").Y(190).Add();

                  pt.X("Feb").Y(226).Add();

                  pt.X("Mar").Y(194).Add();

                  pt.X("Apr").Y(250).Add();

                  pt.X("May").Y(222).Add();

                 }).Name("Bing").Type(SeriesType.StackingColumn).Add();    

            })

  //.......

   )
{% endhighlight  %}

## 100% Stacking column chart 

100% Stacking column is similar to the stacking column charts. But here, the combined contribution of Y values is the combined total of the vertical column with 100 percent.


{% highlight html %}
[MVC]

[CSHTML]

@(Html.EJ().Chart("container")	 

   .Series(sr =>

       {

          sr.Points(pt =>

                {     

                     pt.X("2006").Y(900).Add();                 

                     pt.X("2007").Y(544).Add();

                     pt.X("2008").Y(880).Add();

                     pt.X("2009").Y(725).Add();

                     pt.X("2010").Y(765).Add();

                     pt.X("2011").Y(679).Add();

                     pt.X("2012").Y(770).Add();

                  }).Type(SeriesType.StackingColumn100).Add();

         sr.Points(pt =>

                {

                    pt.X("2006").Y(190).Add();                 

                    pt.X("2007").Y(226).Add();

                    pt.X("2008").Y(194).Add();

                    pt.X("2009").Y(545).Add();

                    pt.X("2010").Y(222).Add();

                    pt.X("2011").Y(181).Add();

                    pt.X("2012").Y(128).Add();                    

                 }).Type(SeriesType.StackingColumn100).Add();  

)


{% endhighlight %}
The following screenshot displays the 100% Stacking column chat.

![C:/Users/Giftline/Desktop/a.png](Chart-Types_images/Chart-Types_img12.png)



## Bar Chart

Bar Chart is the simplest and most versatile of statistical diagrams. It displays horizontal bars for each point in the series and points from adjacent series are drawn as bars next to each other. Bar Charts are used to compare values across categories, to display variations in the value of an item over time or to display the values of several items at a single point in time.You can customize the series color and borderusing Fill and Border properties in series and each segment of series using Fill and Border properties in point.



![](Chart-Types_images/Chart-Types_img13.png)

{% highlight html %}

[MVC]



@(Html.EJ().Chart("chartcontainer") 



   .Series(sr =>

              {

                 sr.Points(pt =>

                  {

                    pt.X(2006).Y(7.8).Add();

                    pt.X(2007).Y(7.2).Add();

                    pt.X(2008).Y(6.8).Add();

                    pt.X(2009).Y(10.7).Add();

                    pt.X(2010).Y(10.8).Add();

                    pt.X(2011).Y(9.8).Add();

                    }).Name("India").Type(SeriesType.Bar).Add();



                sr.Points(pt =>

                {

                   pt.X(2006).Y(4.8).Add();

                   pt.X(2007).Y(4.6).Add();

                   pt.X(2008).Y(7.2).Add();

                   pt.X(2009).Y(9.3).Add();

                   pt.X(2010).Y(9.7).Add();

                   pt.X(2011).Y(9).Add();

                }).Name("US").Type(SeriesType.Bar).Add();

            })

  //.......

  )

{% endhighlight  %}

## Stackingbar Chart

Stacking Bar Charts are similar to regular bar Charts except that the Y values stack on top of each other in the specified series order. This enables you to visualize the relationship of parts to the whole. You can customize the series color and borderusing Fill and Border properties in series and each segment of series using Fill and Border properties in point.



![](Chart-Types_images/Chart-Types_img14.png)

{% highlight html %}

[MVC]



@(Html.EJ().Chart("chartcontainer") 



    .Series(sr =>

      {

        sr.Points(pt =>

           {

              pt.X("Jan").Y(6).Add();

              pt.X("Feb").Y(8).Add();

              pt.X("Mar").Y(12).Add();

              pt.X("Apr").Y(15.5).Add();

              pt.X("May").Y(20).Add();

              pt.X("June").Y(24).Add();

              pt.X("July").Y(28).Add();

            }).Name("Apple").Type(SeriesType.StackingBar).Add();



           sr.Points(pt =>

             {

               pt.X("Jan").Y(-1).Add();

               pt.X("Feb").Y(-1.5).Add();

               pt.X("Mar").Y(-2).Add();

               pt.X("Apr").Y(-2.5).Add();

               pt.X("May").Y(-3).Add();

               pt.X("June").Y(-3.5).Add();

                pt.X("July").Y(-4).Add();            

              }).Name("Wastage").Type(SeriesType.StackingBar).Add();

            })

     //.......

  )
{% endhighlight  %}

## 100% Stacking bar chart 



100% Stacking bar is similar to stacking bar charts. Here, the combined contribution of Y values is the combined total of the horizontal bar with 100 percent. 
{% highlight html %}
[MVC]

[CSHTML]

@(Html.EJ().Chart("container")	 

   .Series(sr =>

       {

          sr.Points(pt =>

                {                      

                     pt.X("2007").Y(453).Add();

                     pt.X("2008").Y(354).Add();

                     pt.X("2009").Y(282).Add();

                     pt.X("2010").Y(321).Add();

                     pt.X("2011").Y(333).Add();

                     pt.X("2012").Y(351).Add();

                     pt.X("2013").Y(403).Add();

                     pt.X("2014").Y(421).Add();                       

                  }).Type(SeriesType.StackingBar100).Add();

         sr.Points(pt =>

                {

                    pt.X("2007").Y(876).Add();

                    pt.X("2008").Y(564).Add();

                    pt.X("2009").Y(242).Add();

                    pt.X("2010").Y(121).Add();

                    pt.X("2011").Y(343).Add();

                    pt.X("2012").Y(451).Add();

                    pt.X("2013").Y(203).Add();

                    pt.X("2014").Y(431).Add();

                 }).Type(SeriesType.StackingBar100).Add();  

)


{% endhighlight  %}
The following screenshot displays the 100% Stackingbar chart.

![C:/Users/Giftline/Desktop/a.png](Chart-Types_images/Chart-Types_img15.png)



## Spline Chart

Spline Chart is similar to a Line Chart except that it connects the different data points using splines instead of straight lines. You can configure the appearance of the lines and the points with options Fill used and the Width of lines.



![](Chart-Types_images/Chart-Types_img16.png)




{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer") 



  .Series(sr =>

    {

       sr.Points(pt =>

        {

          pt.X("Jan").Y(-1).Add();

          pt.X("Feb").Y(-1).Add();

          pt.X("Mar").Y(2).Add();

          pt.X("Apr").Y(8).Add();

          pt.X("May").Y(6).Add();

            pt.X("June").Y(18).Add();

            pt.X("July").Y(11).Add();                      

       }).Name("London").Type(SeriesType.Spline).Add();



         sr.Points(pt =>

          {

            pt.X("Jan").Y(3).Add();

            pt.X("Feb").Y(3.5).Add();

            pt.X("Mar").Y(7).Add();

            pt.X("Apr").Y(5.5).Add();

            pt.X("May").Y(5).Add();

            pt.X("June").Y(13.5).Add();

            pt.X("July").Y(16).Add();                

      }).Name("Germany").Type(SeriesType.Spline).Add();

   })



//.......

  )   
{% endhighlight  %}

## Pie Chart

A Pie Chart renders y values as slices in a pie. The slices are rendered in proportion to the whole that is the sum of all the y values in the series. Consequently, Pie Charts are used to visualize the proportional contribution in terms of percentage or fraction of categories of data to the whole data set. The x values in the data series are treated only as nominal in categorical, qualitative data. The Pie Chart displays only one Data Series at a time. You can customize the series color and borderusing Fill and Border properties in series and each slice of series using Fill and Border properties in point.



![](Chart-Types_images/Chart-Types_img17.png)

{% highlight html %}

[MVC]



@(Html.EJ().Chart("chartcontainer") 



    .Series(sr =>

     {

       sr.Points(pt =>

         {

            pt.X("Labour").Y(28).Text("Labour 28%").Add();

            pt.X("Legal").Y(10).Text("Legal, 10%").Add();

            pt.X("Production").Y(20).Text("Production, 20%").Add();

            pt.X("License").Y(15).Text("License, 15%").Add();

            pt.X("Facilities").Y(23).Text("Facilites, 23%").Add();

            pt.X("Taxes").Y(17).Text("Taxes, 17%").Add();

            pt.X("Insurance").Y(12).Text("Insurance, 12%").Add();

          }).Marker(mr => { mr.DataLabel(db => { db.Visible(true)

           .ConnectorLine(cl => cl.Height(15)).Font(fn => { fn.Size("20px"); }); });})     

              .Name("Newyork").Type(SeriesType.Pie).Explode(true)

                .LabelPosition(ChartLabelPosition.Outside).ExplodeIndex(2).Add();

       })



  //.......

  )  
{% endhighlight  %}

## Doughnut Chart

Doughnut Charts are pie Charts with a hole, whose value is specified as the doughnut coefficient. The Doughnut Chart is best suited for presenting data in proportions. You can customize the series color and borderusing Fill and Border properties in series and each slice of series using Fill and Border properties in point.



![](Chart-Types_images/Chart-Types_img18.png)


{% highlight html %}
[MVC]



 @(Html.EJ().Chart("chartcontainer") 



    .Series(sr =>

     {

       sr.Points(pt =>

         {

            pt.X("Labour").Y(28).Text("Labour 28%").Add();

            pt.X("Legal").Y(10).Text("Legal, 10%").Add();

            pt.X("Production").Y(20).Text("Production, 20%").Add();

            pt.X("License").Y(15).Text("License, 15%").Add();

            pt.X("Facilities").Y(23).Text("Facilites, 23%").Add();

            pt.X("Taxes").Y(17).Text("Taxes, 17%").Add();

            pt.X("Insurance").Y(12).Text("Insurance, 12%").Add();

          }).Marker(mr => { mr.DataLabel(db => { db.Visible(true)

           .ConnectorLine(cl => cl.Height(15)).Font(fn => { fn.Size("20px"); }); });})     

              .Name("Newyork").Type(SeriesType.Doughnut).Explode(true)

                .LabelPosition(ChartLabelPosition.Outside).Add();

       })



  //.......

  )  
{% endhighlight  %}

## Semi Pie and Doughnut Chart

The semi pie and doughnut chart is a semicircular chart. Data are represented in different sectors within a semi-circle.

EJ Chart allows you to create semi pie and doughnut chart using StartAngle and EndAngle property. Default values of StartAngle and EndAngle are null. The specified data are represented within start angle to end angle degree.




{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer") 

                // ......

    .Series(sr =>

     {

       sr.Points(pt =>

         {

            pt.X("Australia").Y(53.3).Text("Australia 53.3").Add();

            pt.X("China").Y(55.7).Text("China 55.7").Add();

            pt.X("India").Y(60.5).Text("India 60.5").Add();

            pt.X("Japan").Y(12.5).Text("Japan 12.5").Add();

            pt.X("South Africa").Y(79.4).Text("South Africa 79.4").Add();

            pt.X("United Kingdom").Y(70.9).Text("United Kingdom 70.9").Add();

            pt.X("United States").Y(45.0).Text("United States 45.0").Add();

          })})     

          .Name("Agricultural Land").SeriesType(SeriesType.Doughnut)

          .LabelPosition(ChartLabelPosition.Outside).StartAngle(-90).EndAngle(90).Add();

       })

        //.......

  .Render())  


{% endhighlight  %}
![C:/Users/balachandar/Desktop/semi doughnut.JPG](Chart-Types_images/Chart-Types_img19.jpeg)



![C:/Users/balachandar/Desktop/semi pie.JPG](Chart-Types_images/Chart-Types_img20.jpeg)



## Pyramid Chart

The Pyramid Chart type displays the data that when totalled renders 100%. This type of Chart is a single series Chart representing the data as portions of 100%, and this Chart does not use any axes. You can customize the series color and borderusing Fill and Border properties in series and each slice of series using Fill and Border properties in point.



![](Chart-Types_images/Chart-Types_img21.png)


{% highlight html %}
[MVC]



 @(Html.EJ().Chart("chartcontainer") 



     .Series(sr =>

     {

       sr.Points(pt =>

          {

           pt.X("India").Y(24).Text("India 24%").Add();

           pt.X("Japan").Y(25).Text("Japan 25%").Add();

           pt.X("Australia").Y(20).Text("Australia 20%").Add();

           pt.X("USA").Y(35).Text("USA 35%").Add();

           pt.X("China").Y(23).Text("China 23%").Add();

           pt.X("Germany").Y(27).Text("Germany 27%").Add();

            pt.X("France").Y(22).Text("France 22%").Add();

          }).Marker(mr => { mr.DataLabel(db => { db.Visible(true).Shape(ChartShape   

             .Rectangle).Font(fn => { fn.Color("white").Size("15px"); }); }); })

              .Name("Newyork").Type(SeriesType.Pyramid)

               .LabelPosition(ChartLabelPosition.Outside).Add();                           

       })



   //.......

  )   
{% endhighlight  %}

## Funnel Chart

The Funnel chart is a single series chart representing the data as portions of 100%, and this chart does not use any axes. Funnel charts are often used to represent stages in a sales process and expresses the amount of potential revenue for each stage. This type of chart can also be useful in identifying potential problem area in an organization’s sales process. You can customize the funnel width and height using FunnelWidth and FunnelHeight properties.

![](Chart-Types_images/Chart-Types_img22.png)


{% highlight html %}
[MVC]



 @(Html.EJ().Chart("chartcontainer") 



     .Series(sr =>

     {

       sr.Points(pt =>

          {

           pt.X("Renewed").Y(18.20).Text("Renewed : 18.20%").Add();

           pt.X("Subscribe").Y(27.3).Text("Subscribe : 27.3%").Add();

           pt.X("Support").Y(55.9).Text("Contact to Support : 55.9%").Add();

           pt.X("Downloaded").Y(76.8).Text("Downloaded a trial 76.8%").Add();

           pt.X("Visited").Y(100).Text("Visited Web Site : 100%").Add();

         }).Marker(mr => { mr.DataLabel(db => { db.Visible(true).Shape(ChartShape   

             .Rectangle).Font(fn => { fn.Color("white").Size("15px"); }); }); })

             .Name("Website").SeriesType(SeriesType.Funnel)

             .FunnelWidth("32.7%").

             .FunnelHeight("11.2%")

             .LabelPosition(ChartLabelPosition.Outside).Add();                           

       })



   //.......

  )   
{% endhighlight  %}

## Bubble Chart

Bubble Chart is an extension of the Scatter Chart (or XY-Chart) where each data marker is represented by a circle whose dimension forms a third variable. Consequently, bubble Charts allow three-variable comparisons allowing for easy visualization of complex interdependencies that are not apparent in two-variable Charts. Bubble Charts are frequently used in market and product comparison studies.



![](Chart-Types_images/Chart-Types_img23.png)


{% highlight html %}
 [MVC]



@(Html.EJ().Chart("chartcontainer")



    .Series(sr =>

      {

        sr.Points(pt =>

          {

            pt.X(92.2).Y(7.8).Size(1.347).Fill("#E94649").Add();

            pt.X(74).Y(6.5).Size(1.241).Fill("#F6B53F").Add();  

            pt.X(90.4).Y(6.0).Size(0.238).Fill("#6FAAB0").Add();

            pt.X(99.4).Y(2.2).Size(0.312).Fill("#C4C24A").Add();

            pt.X(88.6).Y(1.3).Size(0.197).Fill("#FB954F").Add();

            pt.X(54.9).Y(3.7).Size(0.177).Fill("#D9CEB2").Add();

            pt.X(99).Y(0.7).Size(0.0818).Fill("#FF8D8D").Add();

            pt.X(72).Y(2.0).Size(0.0826).Fill("#69D2E7").Add();

            pt.X(99.6).Y(3.4).Size(0.143).Fill("#E27F2D").Add();

            pt.X(99).Y(0.2).Size(0.128).Fill("#6A4B82").Add();

            pt.X(86.1).Y(4.0).Size(0.115).Fill("#F6B53F").Add();

            pt.X(92.6).Y(6.6).Size(0.096).Fill("#C4C24A").Add();

            pt.X(61.3).Y(14.5).Size(0.162).Fill("#FF8D8D").Add();

            pt.X(56.8).Y(6.1).Size(0.151).Fill("#69D2E7").Add();

           }).EnableAnimation(true).Type(SeriesType.Bubble).Name("pound").Add();

       })



   //.......

  )   


{% endhighlight  %}
{% highlight html %}
[ASP] 

<ej:Chart ID="Chart1" runat="server">

   <Series>

        <ej:Series Name="Pound" Type="Bubble" EnableAnimation="True" Opacity="0.7">

                    <Points >

                        <ej:Points Fill="#E94649" Size="1.347" Text="China" X="92.2" Y="7.8"/> 

                        <ej:Points Fill="#F6B53F" Size="1.241" Text="India" X="74" Y="6.5"/>  

                        <ej:Points Fill="#6FAAB0" Size="0.238" Text="Indonesia" X="90.4" Y="6.0"/>  

                        <ej:Points Fill="#C4C24A" Size="0.312" Text="US" X="99.4" Y="2.2"/>  

                        <ej:Points Fill="#FB954F" Size="0.197" Text="Brazil" X="88.6" Y="1.3"/>  

                        <ej:Points Fill="#D9CEB2" Size="0.177" Text="Pakistan" X="54.9" Y="3.7"/>  

                        <ej:Points Fill="#FF8D8D" Size="0.0818" Text="Germany" X="99" Y="0.7"/>  

                        <ej:Points Fill="#69D2E7" Size="0.0826" Text="Egypt" X="72" Y="2.0"/>  

                        <ej:Points Fill="#E27F2D" Size="0.143" Text="Russia" X="99.6" Y="3.4"/>  

                        <ej:Points Fill="#6A4B82" Size="0.128" Text="Japan" X="99" Y="0.2"/>  

                        <ej:Points Fill="#F6B53F" Size="0.115" Text="Mexico" X="86.1" Y="4.0"/>  

                        <ej:Points Fill="#C4C24A" Size="0.096" Text="Philippines" X="92.6" Y="6.6"/>  

                        <ej:Points Fill="#FF8D8D" Size="0.162" Text="Nigeria" X="61.3" Y="14.5"/>  

                        <ej:Points Fill="#69D2E7" Size="0.151" Text="Bangladesh" X="56.8" Y="6.1"/>     

                    </Points>

                </ej:Series>

            </Series> 

  </ej:Chart>

{% endhighlight  %}

## Scatter

In Scatter Series, each data point is represented as an ellipse, and the width and height of each ellipse is set using the Size Width and Height properties of marker. You can also change the color, stroke, and stroke thickness of the series using the Fill, Border color, and Width properties of marker respectively.

The following code example is used to create a simple scatter series. 
{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")



.Series(sr =>

 {

    sr.Points(pt =>

     {

           pt.X(10).Y(126.45).Add();

           pt.X(11).Y(150.99).Add();

           pt.X(12).Y(40.19).Add();

           pt.X(13).Y(160.23).Add();

           pt.X(15).Y(200.89).Add();                  

    }).Type(SeriesType.Scatter).Marker(mr=>mr.Size(sz=>sz.Height(10).Width(10)))    

         .Name("Scatter").Add();

   })



  //.......

  )    
{% endhighlight  %}

![](Chart-Types_images/Chart-Types_img24.png)



## HiLoOpenCloseSeries 

A HiLoOpenCloseSeries displays each data point as a group of two horizontal lines and one vertical line. The height of the vertical line depends on the difference between the high value and low value of the data point. The width of the horizontal lines depends on the time span interval. The line indicating the open value is at the left side of the vertical line, and the line indicating the closed value is at its right side. You can also change the color, and stroke thickness of the series using the FIll, BorderWidth properties respectively.

The following properties are useful in mapping the value of each data point in a HiLoOpenCloseSeries: 

_Table2: Property Table_

<table>
<tr>
<th>
API</th><th>
Description</th></tr>
<tr>
<td>
X</td><td>
Represents the x-values</td></tr>
<tr>
<td>
Open</td><td>
Represents the Open values</td></tr>
<tr>
<td>
High</td><td>
Represents the high values</td></tr>
<tr>
<td>
Low</td><td>
Represents the low values</td></tr>
<tr>
<td>
Close</td><td>
Represents the close values</td></tr>
</table>


![](Chart-Types_images/Chart-Types_img25.png)



### BullFillColor

BullFillColor is used to specify a fill color for the segments that indicates an increase in stock price in the measured time interval.

### BearFillColor

BearFillColor is used to specify a fill color for the segments that indicate a decrease in stock price in the measured time interval.

### DrawMode

DrawMode is used to specify the open and close draw mode to hiloopenclose series.

* Open - Points only the opening value of that period.
* Close - Points out the closing value of that period.
* Both - Points out both the opening and the closing values of that period.

 To create a simple HiLoOpenCloseSeries use the following code example.

{% highlight html %}

[MVC]



@(Html.EJ().Chart("chartcontainer")



.Series(sr =>

 {

   sr.Points(pt =>

     {

          pt.X(new DateTime(1950, 1, 12)).High(125.45).Low(70.23).Open(115.22)  

            .Close(90.44).Add();

          pt.X(new DateTime(1953, 1,12)).High(150.99).Low(60.23).Open(120.55) 

            .Close(70.90).Add();

          pt.X(new DateTime(1956, 1, 12)).High(200.19).Low(130.37).Open(160.13) 

            .Close(190.78).Add();

          pt.X(new DateTime(1959, 1, 12)).High(160.23).Low(90.16).Open(140.38) 

            .Close(110.24).Add();

          pt.X(new DateTime(1962, 1, 12)).High(200.89).Low(100.23).Open(180.90) 

            .Close(120.29).Add();



  }).Name("Series").Type(SeriesType.HiloOpenClose).DrawMode(SeriesDrawMode.Both)

   .Border(br=>br.Width(2)).Add();

})



  //.......

  )   
{% endhighlight  %}

## Candle

A CandleSeries displays each data point with a combination of a vertical column and a vertical line. The height of the vertical line represents the difference between high and low value of a datapoint, whereas the height of the vertical column represents the difference between the Open and Close values of a data point. You can also change the color and stroke thickness of the series using the Fill, Borderwidth properties respectively.

The following properties are useful in mapping the value of each data point in a Candle.

_Table3: Property Table_

<table>
<tr>
<th>
API</th><th>
Description</th></tr>
<tr>
<td>
X</td><td>
Represents the x-values</td></tr>
<tr>
<td>
Open</td><td>
Represents the Open values.</td></tr>
<tr>
<td>
High</td><td>
Represents the high values</td></tr>
<tr>
<td>
Low</td><td>
Represents the low values</td></tr>
<tr>
<td>
Close</td><td>
Represents the close values</td></tr>
</table>


![](Chart-Types_images/Chart-Types_img26.png)



### BullFillColor

BullFillColor is used to specify a fill color for the segment that indicates an increase in stock price in the measured time interval.

### BearFillColor

BearFillColor is used to specify a fill color for the segment that indicates a decrease in stock price in the measured time interval.

To create a simple Candle series use the following code example. 
{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")



.Series(sr =>

 {

  sr.Points(pt =>

      {

        pt.X(new DateTime(1950, 1, 12)).High(125).Low(70).Open(115).Close(90).Add();

        pt.X(new DateTime(1953, 1, 12)).High(150).Low(60).Open(120).Close(70).Add();

        pt.X(new DateTime(1956, 1, 12)).High(200).Low(140).Open(160).Close(190).Add();

        pt.X(new DateTime(1959, 1, 12)).High(160).Low(90).Open(140).Close(110).Add();

        pt.X(new DateTime(1962, 1, 12)).High(200).Low(100).Open(180).Close(120).Add();

      }).Name("Series").Type(SeriesType.Candle).Border(br=>br.Width(2)).Add();

  })



  //.......

  )  
{% endhighlight  %}

## Hilo

Ina HiLoSeries, each segment is represented by a line. The height of the line depends on the difference between the high value and low value of the data point. You can also change the color and stroke thickness of the series using the Fill, BorderWidth properties respectively.

The following properties are useful in mapping the value of each data point in a Hilo.

_Table4: Property Table_

<table>
<tr>
<th>
API</th><th>
Description</th></tr>
<tr>
<td>
X</td><td>
Represents the x-values</td></tr>
<tr>
<td>
High</td><td>
Represents the high values</td></tr>
<tr>
<td>
Low</td><td>
Represents the low values</td></tr>
</table>


![C:/Users/ApoorvahR/Desktop/3.png](Chart-Types_images/Chart-Types_img27.png)



To create a simple Hilo series use the following code example. 
{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")



 .Series(sr =>

   {

     sr.Points(pt =>

      {

         pt.X(new DateTime(1950, 1, 12)).High(126.45).Low(70.23).Add();

         pt.X(new DateTime(1953, 1, 12)).High(150.99).Low(60.23).Add();

         pt.X(new DateTime(1956, 1, 12)).High(200.19).Low(130.37).Add();

         pt.X(new DateTime(1959, 1, 12)).High(160.23).Low(90.16).Add();

         pt.X(new DateTime(1962, 1, 12)).High(200.89).Low(100.23).Add();                  

       }).Name("Series").Type(SeriesType.Hilo).Border(br=>br.Width(2)).Add();

    })



   //.......

  )  
{% endhighlight  %}

## Polar

A Polar Chart is a circular graph on which data is displayed in terms of values and angles. The x values define the angles at which the data points are plotted. The y value defines the distance of the data points from the center of the graph, with the center of the graph usually starting at 0. You can customize the series color and borderusing Fill and Border properties in series. You can use IsClosed property in series to specify whether the series drawn is in closed form. It supports three types of rendering such as Line, Area and Column.

### LineType

![](Chart-Types_images/Chart-Types_img28.png)



### Area Type

![](Chart-Types_images/Chart-Types_img29.png)



### Column Type

![](Chart-Types_images/Chart-Types_img30.png)





To create a simple Polar series use the following code example.


{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")



  .Series(sr =>

     {

       sr.Points(pt =>

        {

           pt.X("1900").Y(10).Add();

           pt.X("1991").Y(3).Add();

           pt.X("1992").Y(20).Add();

           pt.X("1993").Y(16).Add();

           pt.X("1994").Y(10).Add();

           pt.X("1995").Y(18).Add();

           pt.X("1996").Y(16).Add();

           pt.X("1997").Y(15).Add();

         }).Name("India").EnableAnimation(true).Width(3).Add();

      })

  //.......

  )  
{% endhighlight  %}

## RadarSeries 

RadarSeries is a x, y Chart of three or more quantitative variables represented on multiple axis lines originating from the same point. You can customize the series color and borderusing Fill and Border properties in series. You can use IsClosed property in series to specify whether the series drawn is in closed form. It supports three types of rendering such as Line, Area and Column.

### Area Type

![](Chart-Types_images/Chart-Types_img31.png)



### Line type

![](Chart-Types_images/Chart-Types_img32.png)



### Column type

![](Chart-Types_images/Chart-Types_img33.png)



To create simple RadarSeries use the following code example. 
{% highlight html %}
[MVC]



@(Html.EJ().Chart("chartcontainer")



  .Series(sr =>

    {

      sr.Points(pt =>

       {

          pt.X("1900").Y(10).Add();

          pt.X("1991").Y(3).Add();

          pt.X("1992").Y(20).Add();

          pt.X("1993").Y(16).Add();

          pt.X("1994").Y(10).Add();

          pt.X("1995").Y(18).Add();

          pt.X("1996").Y(16).Add();

          pt.X("1997").Y(15).Add();

       }).Name("India").EnableAnimation(true).Type(SeriesType.Radar)

          .Border(br=>br.Width(3).Color("black")).DrawType(SeriesDrawType.Area).Add();           

    })

  //.......

  )  

{% endhighlight  %}

