---
layout: post
title: Printing  |Chart  | ASP.NET MVC | Syncfusion 
description: Learn how to print Chart
platform: ejmvc
control: Chart
documentation: ug
---

# Printing Chart
The rendered chart can be printed directly from the browser by calling the public method **print**. ID of the chart div element must be passed as argument to that method.

{% highlight cshtml %}

<button type="button" onclick="print()" ></button> 
@(Html.EJ().Chart("container"))
<script>
function print() {
var chartObj = $("#container").ejChart("instance");
chartObj.print("container");
        }

</script>


{% endhighlight %}


This print method can be called by performing any action on the web page. For example, by clicking a button. While calling the print method in chart, print preview will be displayed in the browser.

![](Printing_images/Printing_img1.png)

[Click](http://mvc.syncfusion.com/demos/web/chart/exports) here to view the Printing chart online demo sample

## Printing Multiple chart

Multiple charts in a web page can be printed together. For printing multiple charts, ID of the chart div elements have to be passed as shown in the below code 


{% highlight cshtml  %}
   
<button type="button" onclick="print()" ></button> 
@(Html.EJ().Chart("container1"))
@(Html.EJ().Chart("container2"))
<script>
function print() {
var chartObj = $("#container1").ejChart("instance");
chartObj.print("container1","container2");
        }

</script>

{% endhighlight %}

The Print preview of multiple Charts is shown below 

![](Printing_images/Printing_img2.png)

## Page Setup

Some of print options are not configurable through JavaScript code. You need to customize layout, paper size, margins options through browser's page setup dialog. Please find the following guidelines link to browser page setup.

* [Chrome](https://support.google.com/chrome/answer/1379552?hl=en)
* [Firefox](https://support.mozilla.org/en-US/kb/how-print-web-pages-firefox)
* [Safari](http://www.mintprintables.com/print-tips/adjust-margins-osx/)
* [IE](http://www.helpteaching.com/help/print/index.htm) 
