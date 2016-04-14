---
layout: post
title: Technical Indicators| Chart  | ASP.NET MVC | Syncfusion
description: What are the different types of technical indicators supported in Essential Chart for financial analysis.
platform: ejmvc
control: Chart
documentation: ug
---

# Technical Indicators

EjChart control supports 10 types of technical indicators. 

## Bind data to render the indicator

You can bind the series **DataSource** to the indicator by setting the specific series name to the indicator by using the *Indicators.SeriesName* property.

{% highlight cshtml %}

@(Html.EJ().Chart("chartContainer")

      // ...
      //Initializing Series
      .Series(sr =>
      {
          sr
              .XName("XDate").High("High").Low("Low").Open("Open").Close("Close")
              //Set name to series
              .Name("Hilo")
              .DataSource(ViewBag.ChartData).Add();
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          //Set Hilo series dataSource to indicator using seriesName
          .SeriesName("Hilo").Add();
      })
        //...
 )

{% endhighlight %}

{% highlight csharp %}

           //// Create dataSource to chart
            List<ChartData> data = new List<ChartData>();
            data.Add(new ChartData("2010/7/1", 38, 10, 58, 27));
            data.Add(new ChartData("2010/7/8", 28, 15, 48, 58));
            data.Add(new ChartData("2010/7/9", 54, 35, 85, 98));
            data.Add(new ChartData("2010/7/10", 52, 21, 38, 85));
            ///...
            ViewBag.ChartData = data;

{% endhighlight %}
Also, you can add data to the indicator directly by using the DataSource option of the indicator.  

{% highlight cshtml %}


  @(Html.EJ().Chart("chartContainer")

      // ...
     
      //Initializing Indicators  
      .Indicators(ind => { ind
              //Add dataSource to indicator directly
              .XName("XDate").High("High").Low("Low").Open("Open").Close("Close")
              .DataSource(ViewBag.ChartData).Add();
      })
        //...
  )

{% endhighlight %}

	
## Indicator Types

### Accumulation Distribution

To create an Accumulation Distribution indicator, set the *Indicators.Type* as **AccumulationDistribution**. Accumulation Distribution require **Volume** field additionally with the DataSource to calculate the signal line.

{% highlight cshtml %}


@(Html.EJ().Chart("chartContainer")

      // ...
        //Initializing Series
      .Series(sr =>
      {
          sr
              .XName("XDate").High("High").Low("Low").Open("Open").Close("Close").Volume("Volume")
              //Set name to series
              .Name("Hilo")
              .DataSource(ViewBag.ChartData).Add();
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          //Set indicator type
          .Type(ChartIndicatorType.AccumulationDistribution)
          .SeriesName("Hilo").Add();
      })
        //...
 )


{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img1.png)

[Click](http://mvc.syncfusion.com/demos/web/chart/accumulationdistribution) here to view the Accumulation Distribution indicator online demo sample.


### Average True Range (ATR)

You can create an ATR indicator by setting the Indicators.Type as **ATR** in the Indicators. 

{% highlight cshtml %}


@(Html.EJ().Chart("chartContainer")

      // ...
        //Initializing Series
      .Series(sr =>
      {
         //...
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          //Set indicator type
          .Type(ChartIndicatorType.ATR).Add();
      })
        //...
 )


{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img2.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/atr) here to view the ATR indicator online demo sample.


### Bollinger Band 

Bollinger Band indicator is created by setting the Indicators.Type as **BollingerBand**. It contains three lines, namely upper band, lower band and signal line. Bollinger Band default value of the *Period* is 14 and *StandardDeviations* is 2.

{% highlight cshtml %}


@(Html.EJ().Chart("chartContainer")

      // ...
        //Initializing Series
      .Series(sr =>
      {
         //...
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          //Set indicator type
          .Type(ChartIndicatorType.BollingerBand).Add();
      })
        //...
 )


{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img3.png)

[Click](http://mvc.syncfusion.com/demos/web/chart/bollingerband) here to view the Bollinger Band indicator online demo sample.


### Exponential Moving Average (EMA)

To render an EMA indicator, you have to set the Indicators.Type as **EMA**.  

{% highlight cshtml %}


@(Html.EJ().Chart("chartContainer")

      // ...
        //Initializing Series
      .Series(sr =>
      {
         //...
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          //Set indicator type
          .Type(ChartIndicatorType.EMA).Add();
      })
        //...
 )


{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img4.png)

[Click](http://mvc.syncfusion.com/demos/web/chart/ema) here to view the EMA indicator online demo sample.


### Momentum 

Momentum Technical indicator is created by setting the Indicators.Type as **Momentum**. The momentum indicator renders two lines, namely upper band and signal line. Upper band always rendered at the value 100 and the signal line is calculated based on the momentum of the data.

{% highlight cshtml %}


@(Html.EJ().Chart("chartContainer")

      // ...
        //Initializing Series
      .Series(sr =>
      {
         //...
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          //Set indicator type
          .Type(ChartIndicatorType.Momentum).Add();
      })
        //...
 )


{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img5.png)


[Click](http://mvc.syncfusion.com/demos/web/chart/momentum) here to view the Momentum indicator online demo sample.


### Moving Average Convergence Divergence (MACD)

To render an MACD indicator, you have to set the Indicators.Type as **MACD**.  MACD indicator contains MACD line, Signal line and Histogram column. Histogram is used to differentiate MACD and signal line.

{% highlight cshtml %}


@(Html.EJ().Chart("chartContainer")

      // ...
        //Initializing Series
      .Series(sr =>
      {
         //...
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          //Set indicator type
          .Type(ChartIndicatorType.MACD).Add();
      })
        //...
 )


{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img6.png)

[Click](http://mvc.syncfusion.com/demos/web/chart/macd) here to view the MACD indicator online demo sample.


#### MacdType

By using the **MacdType** enumeration property, you can change the MACD rendering as *Line*, *Histogram* or *Both*. 

{% highlight cshtml %}


@(Html.EJ().Chart("chartContainer")

      // ...
        //Initializing Series
      .Series(sr =>
      {
         //...
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          .Type(ChartIndicatorType.MACD)
          //Set macd draw type
          .MacdType(MacdType.Histogram)
          .Add();
      })
        //...
 )


{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img7.png)

### Relative Strength Index (RSI)

To render the RSI indicator, set the Indicators.Type as **RSI**. It contains three lines, namely upper band, lower band and signal line. Upper and lower band always render at value 70 and 30 respectively and signal line is calculated based on the *RSI* formula.

{% highlight cshtml %}


 @(Html.EJ().Chart("chartContainer")

      // ...
        //Initializing Series
      .Series(sr =>
      {
         //...
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          //Set indicator type
          .Type(ChartIndicatorType.RSI)
          .Add();
      })
        //...
 )


{% endhighlight %}


![](Technical-Indicators_images/Technical-Indicators_img8.png)

[Click](http://mvc.syncfusion.com/demos/web/chart/rsi) here to view the RSI indicator online demo sample.


### Simple Moving Average (SMA)

To render the SMA indicator, you should specify the Indicators.Type as **SMA**.  

{% highlight cshtml %}


 @(Html.EJ().Chart("chartContainer")

      // ...
        //Initializing Series
      .Series(sr =>
      {
         //...
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          //Set indicator type
          .Type(ChartIndicatorType.SMA)
          .Add();
      })
        //...
 )


{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img9.png)

[Click](http://mvc.syncfusion.com/demos/web/chart/sma) here to view the SMA indicator online demo sample.


### Stochastic 

For the Stochastic indicator, you need to set the Indicators.Type as **Stochastic**. The Stochastic indicator renders four lines namely, upper line, lower line, stochastic line and the signal line. Upper line always rendered at value 80 and the lower line is rendered at value 20. Stochastic and Signal Lines are calculated based on the stochastic formula.

{% highlight cshtml %}


@(Html.EJ().Chart("chartContainer")

      // ...
        //Initializing Series
      .Series(sr =>
      {
         //...
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          //Set indicator type
          .Type(ChartIndicatorType.Stochastic)
          .Add();
      })
        //...
 )


{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img10.png)

[Click](http://mvc.syncfusion.com/demos/web/chart/stochastic) here to view the stochastic indicator online demo sample.


### Triangular Moving Average (TMA)

To render the TMA indicator, you should specify the Indicators.Type as **TMA**. 

{% highlight cshtml %}


@(Html.EJ().Chart("chartContainer")

      // ...
      //Initializing Series
      .Series(sr =>
      {
         //...
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          //Set indicator type
          .Type(ChartIndicatorType.TMA)
          .Add();
      })
        //...
 )


{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img11.png)

[Click](http://mvc.syncfusion.com/demos/web/chart/tma) here to view the TMA indicator online demo sample.


## Enable Tooltip 

To display the indicator tooltip, use *Visible* option of the **Indicators.Tooltip**. Also, you can change and customize the tooltip color, border, format and font properties similar to the series tooltip.

{% highlight cshtml %}


@(Html.EJ().Chart("chartContainer")

      // ...
        //Initializing Series
      .Series(sr =>
      {
         //...
      })
        //Initializing Indicators  
      .Indicators(ind => { ind
          //...
          .Tooltip(tl=>tl.
              //Enable tooltip for indicator
              Visible(true))
          .Add();
      })
        //...
 )


{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img12.png)
