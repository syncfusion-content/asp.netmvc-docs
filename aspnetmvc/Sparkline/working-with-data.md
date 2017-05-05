---
layout: post
title: Data binding
description: Learn how to bind Sparkline with local data.
platform: ejmvc
control: Sparkline
documentation: ug
---

# Working with Data

## Local Data

1. You can bind the data to the Sparkline by using `DataSource`property and then you need to map the **X** and **Y** value with **XName** and **YName** properties respectively.

{% highlight C# %}

public class HomeController : Controller
    {
         public IActionResult Index()

        {    
            //// Create dataSource to Sparkline
            List<SparklineData> data = new List<SparklineData>();
            data.Add(new SparklineData(0, 35));
            data.Add(new SparklineData(1, 28));
            data.Add(new SparklineData(2, 34));
            data.Add(new SparklineData(3, 32));
            data.Add(new SparklineData(4, 40));
            data.Add(new SparklineData(5, 32));
            data.Add(new SparklineData(6, 35));
            data.Add(new SparklineData(7, 55));
            data.Add(new SparklineData(8, 38));
            data.Add(new SparklineData(9, 30));
            data.Add(new SparklineData(10, 25));
            data.Add(new SparklineData(11, 32));
            ///...
            ViewBag.SparklineData = data;
            return View();
        }
    }

    public class SparklineData
    {
        public double Month;
        public double Sales;
        public SparklineData(double month, double sales)
        {
            this.Month = month;
            this.Sales = sales;
        }
    }

{% endhighlight %}

{% highlight cshtml %}

@(Html.EJ().Sparkline("container")

.DataSource((IEnumerable<object>)ViewBag.SparklineData)
.XName("Month").YName("Sales")
 
 )

{% endhighlight %}

![](Working-with-Data_images/Working-with-Data_img1.png); 

2. You can also bind an array of data to Sparkline by using `DataSource` property.  

{% highlight cshtml %}

public class HomeController : Controller
    {
         public IActionResult Index()

        {    
            Double[] y1 = { 2, 6, -1, 1, 12, 5, -2, 7, -3, 5, 8, 10};
            ViewBag.SparklineData = y1;
            return View();
        }
    }

{% endhighlight %}

{% highlight cshtml %}

@(Html.EJ().Sparkline("container")

.DataSource((IEnumerable<object>)ViewBag.SparklineData)
 
 )

{% endhighlight %}


![](Working-with-Data_images/Working-with-Data_img2.png); 


