---
layout: post
title: Public Methods and Events | DigitalGauge | ASP.NET MVC | Syncfusion
description: Public methods and events
platform: ejmvc
control: DigitalGauge
documentation: ug
---

## Methods


### destroy()


To `destroy` the digital gauge


{% highlight CSHTML %}
 
@(Html.EJ().DigitalGauge("Gauge1"))

{% endhighlight %}

{% highlight js %}
 
var gauge = $("#Gauge1").data("ejDigitalGauge");
gauge.destroy();
   
{% endhighlight %}


### exportImage(fileName, fileType)


To `export` Digital Gauge as Image

{% highlight CSHTML %}
 
@(Html.EJ().DigitalGauge("Gauge1"))

{% endhighlight %}

{% highlight js %}
 
var gauge = $("#Gauge1").data("ejDigitalGauge");
gauge.exportImage();
   
{% endhighlight %}


### getPosition(itemIndex)

Gets the location of an item that is displayed on the gauge.

{% highlight CSHTML %}
 
@(Html.EJ().DigitalGauge("Gauge1"))

{% endhighlight %}

{% highlight js %}
 
var gauge = $("#Gauge1").data("ejDigitalGauge");
gauge.getPosition();
   
{% endhighlight %}


### getValue(itemIndex)


ClientSideMethod `getValue` Gets the value of an item that is displayed on the gauge

{% highlight CSHTML %}
 
@(Html.EJ().DigitalGauge("Gauge1"))

{% endhighlight %}

{% highlight js %}
 
var gauge = $("#Gauge1").data("ejDigitalGauge");
gauge.getValue();
   
{% endhighlight %}



### refresh()


`Refresh` the digital gauge widget


{% highlight CSHTML %}
 
@(Html.EJ().DigitalGauge("Gauge1"))

{% endhighlight %}

{% highlight js %}
 
var gauge = $("#Gauge1").data("ejDigitalGauge");
gauge.refresh();
   
{% endhighlight %}


### setPosition(itemIndex, value)

ClientSideMethod `Set Position` Sets the location of an item to be displayed in the gauge


{% highlight CSHTML %}
 
@(Html.EJ().DigitalGauge("Gauge1"))

{% endhighlight %}

{% highlight js %}
 
var gauge = $("#Gauge1").data("ejDigitalGauge");
gauge.setPosition();
   
{% endhighlight %}


### setValue(itemIndex, value)

ClientSideMethod `SetValue` Sets the value of an item to be displayed in the gauge.

{% highlight CSHTML %}
 
@(Html.EJ().DigitalGauge("Gauge1"))

{% endhighlight %}

{% highlight js %}
 
var gauge = $("#Gauge1").data("ejDigitalGauge");
gauge.setValue();
   
{% endhighlight %}




## Events



### Init

Triggers when the gauge is initialized.



{% highlight CSHTML %}
 
@(Html.EJ().DigitalGauge("Gauge1")

.Init("init")

)

{% endhighlight %}

{% highlight js %}
 
function init(){
    // Do Something
}

{% endhighlight %}





### ItemRendering

Triggers when the gauge `item rendering`.



{% highlight CSHTML %}
 
@(Html.EJ().DigitalGauge("Gauge1")

.ItemRendering("itemRendering")

)

{% endhighlight %}

{% highlight js %}
 
function itemRendering(){
    // Do Something
}

{% endhighlight %}



### Load


Triggers when the gauge is start to `load`.



{% highlight CSHTML %}
 
@(Html.EJ().DigitalGauge("Gauge1")

.Load("load")

)

{% endhighlight %}

{% highlight js %}
 
function load(){
    // Do Something
}

{% endhighlight %}





### RenderComplete


Triggers when the gauge render is completed.



{% highlight CSHTML %}
 
@(Html.EJ().DigitalGauge("Gauge1")

.RenderComplete("renderComplete")

)

{% endhighlight %}

{% highlight js %}
 
function renderComplete(){
    // Do Something
}

{% endhighlight %}



