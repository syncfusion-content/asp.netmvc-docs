---
layout: post
title: Public Methods and Events| BulletGraph	 | ASP.NET MVC | Syncfusion
description: bullet graph methods and events
platform: ejmvc
control: BulletGraph	
documentation: ug
---


## Methods


### destroy ()

To destroy the bullet graph


{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1"))

{% endhighlight %}

{% highlight js %}
 
var bullet = $("#bullet1").data("ejBulletGraph");
bullet.destroy();
   
{% endhighlight %}


### redraw()

To redraw the bullet graph


{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1"))

{% endhighlight %}

{% highlight js %}
 
var bullet = $("#bullet1").data("ejBulletGraph");
bullet.redraw();
   
{% endhighlight %}




### setComparativeMeasureSymbol()


To set the value for comparative measure in bullet graph.



{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1"))

{% endhighlight %}

{% highlight js %}
 
var bullet = $("#bullet1").data("ejBulletGraph");
bullet.setComparativeMeasureSymbol();
   
{% endhighlight %}


### setFeatureMeasureBarValue()


To set the value for feature measure bar.



{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1"))

{% endhighlight %}

{% highlight js %}
 
var bullet = $("#bullet1").data("ejBulletGraph");
bullet.setFeatureMeasureBarValue();
   
{% endhighlight %}


## Events


### DrawCaption

Fires on rendering the caption of bullet graph.


{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1")

.DrawCaption("drawCaption")

)

{% endhighlight %}

{% highlight js %}
 
function drawCaption(){
    // Do Something
}

{% endhighlight %}







### DrawCategory

Fires on rendering the category.



{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1")

.DrawCategory("drawCategory")

)

{% endhighlight %}

{% highlight js %}
 
function drawCategory(){
    // Do Something
}

{% endhighlight %}


### DrawComparativeMeasureSymbol


Fires on rendering the comparative measure symbol.



{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1")

.DrawComparativeMeasureSymbol("drawComparativeMeasureSymbol")

)

{% endhighlight %}

{% highlight js %}
 
function drawComparativeMeasureSymbol(){
    // Do Something
}

{% endhighlight %}





### DrawFeatureMeasureBar

Fires on rendering the feature measure bar.


{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1")

.DrawFeatureMeasureBar("drawFeatureMeasureBar")

)

{% endhighlight %}

{% highlight js %}
 
function drawFeatureMeasureBar(){
    // Do Something
}

{% endhighlight %}






### DrawIndicator


Fires on rendering the indicator of bullet graph.



{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1")

.DrawIndicator("drawIndicator")

)

{% endhighlight %}

{% highlight js %}
 
function drawIndicator(){
    // Do Something
}

{% endhighlight %}






### DrawLabels


Fires on rendering the labels.



{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1")

.DrawLabels("drawLabels")

)

{% endhighlight %}

{% highlight js %}
 
function drawLabels(){
    // Do Something
}

{% endhighlight %}


### DrawTicks

Fires on rendering the ticks.



{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1")

.DrawTicks("drawTicks")

)

{% endhighlight %}

{% highlight js %}
 
function drawTicks(){
    // Do Something
}

{% endhighlight %}


### DrawQualitativeRanges






{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1")

.DrawQualitativeRanges("drawQualitativeRanges")

)

{% endhighlight %}

{% highlight js %}
 
function drawQualitativeRanges(){
    // Do Something
}

{% endhighlight %}






### Load

Fires on loading bullet graph.



{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1")

.Load("load")

)

{% endhighlight %}

{% highlight js %}
 
function load(){
    // Do Something
}

{% endhighlight %}


### Click

Click event fires on clicking the bullet graph.



{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1")

.Click("click")

)

{% endhighlight %}

{% highlight js %}
 
function click(){
    // Do Something
}

{% endhighlight %}

### DoubleClick

DoubleClick event fires on double clicking the bullet graph.



{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1")

.DoubleClick("doubleClick")

)

{% endhighlight %}

{% highlight js %}
 
function doubleClick(){
    // Do Something
}

{% endhighlight %}

### RightClick

RightClick event fires on right clicking the bullet graph.



{% highlight CSHTML %}
 
@(Html.EJ().BulletGraph("bullet1")

.RightClick("rightClick")

)

{% endhighlight %}

{% highlight js %}
 
function rightClick(){
    // Do Something
}

{% endhighlight %}


