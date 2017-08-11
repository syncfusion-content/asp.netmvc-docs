---
layout: post
title: MVVM | CircularGauge | ASP.NET MVC | Syncfusion
description: mvvm
platform: ejmvc
control: CircularGauge
documentation: ug
---

# MVVM

## AngularJS

Circular Gauge contains AngularJS support. You can add object as well as array object in the Circular Gauge. The two way binding support is given to the pointer value, minimum scale value and maximum scale value. 

## Rendering the Circular Gauge


ej-CircularGauge is the control tag in which ej is tag prefix and CircularGauge is the control name.The following code example helps you to render Circular Gauge.

{% highlight html %}
<div ng-app="syncApp">

<div ng-controller="CircularGauge">

<ej-CircularGauge id="CircularGauge1" e-backgroundColor="transparent" e-value="50"

e-width="500" e-readOnly="false" e-load= "loadGaugeTheme"

e-enableAnimation="false">

</ej-CircularGauge>



</div>

</div>
{% endhighlight  %}

{% highlight js %}
<script type="text/javascript">



<!—binding the value to the scope variables in application controller-->



angular.module('syncApp', ['ejangular'])

.controller('CircularGauge', function ($scope) {

$scope.value = 50;

$scope.minimum = 0;

$scope.maximum = 120;


});

</script>


{% endhighlight  %}


Execute the above code to render the output as follows.

![](MVVM_images/MVVM_img1.png)

Default Circular gauge in AngularJS
{:.caption}



## Adding Scale Collection

Scale is an array object and you can use the inner tag for it. Object in the array collection (i.e. border) is extended with hyphen in the same tag.

Example: e-border-width and e-border-color. 

{% highlight html %}
<!--To Render the Circular gauge-->

<ej-CircularGauge id="CircularGauge1">

<!--Adding Scale collection to the Circular gauge-->

<e-scales>

<e-scale e-showRanges="true" e-startAngle="122" e-sweepAngle="296"

e-radius="130" e-showScaleBar="true" e-size="1" e-maximum="120"

e-majorIntervalValue="20" e-minorIntervalValue="10"

e-border-width="0.5">

</e-scale>

</e-scales>

</ej-CircularGauge>


{% endhighlight  %}


Execute the above code to render the following output.

![](MVVM_images/MVVM_img2.png)

Circular gauge with scale customization in AngularJS
{:.caption}


## Adding Pointer Collection

Pointer is an array object and you can use the inner tag for it. Object in the array collection (i.e. pointer cap) is extended with hyphen in the same tag.

Example: e-pointerCap-radius. 
{% highlight html %}
<!--To Render the Circular gauge-->

<ej-CircularGauge id="CircularGauge1">

<!--Adding Scale collection to the Circular gauge-->

<e-scales>

<e-scale>

<!--Adding pointer collection to the scale collection-->

<e-pointers>

<e-pointer e-showBackNeedle="true" e-backNeedleLength="20"

e-length="95" e-width="7" e-value="80"

e-pointerCap-radius="12">

</e-pointer>

</e-pointers>

</e-scale>

</e-scales>

</ej-CircularGauge>


{% endhighlight %}
Execute the above code to render the output as follows.

![](MVVM_images/MVVM_img3.png)

Circular gauge with pointer customization in AngularJS
{:.caption}


## Adding Label Collection

Label is also an array object. You can use the inner tag for it. 
{% highlight html %}
<!--To Render the Circular gauge-->

<ej-CircularGauge id="CircularGauge1">

<!--Adding Scale collection to the Circular gauge-->

<e-scales>

<e-scale>

<!--Adding pointer collection to the scale collection-->

<e-pointers>…</e-pointers>

<!--Adding labels collection to the scale collection-->

<e-labels>

<e-label e-color="#8c8c8c">

</e-label>

</e-labels>

</e-scale>

</e-scales>

</ej-CircularGauge>

{% endhighlight %}

Execute the above code to render the following output.

![](MVVM_images/MVVM_img4.png)

Circular gauge with label customization in AngularJS
{:.caption}



## Adding Tick Collection

Tick is an array object. You can use the inner tag for it. 
{% highlight html %}
<!--To Render the Circular gauge-->

<ej-CircularGauge id="CircularGauge1">

<!--Adding Scale collection to the Circular gauge-->

<e-scales>

<e-scale>

<!--Adding pointer collection to the scale collection-->

<e-pointers>…</e-pointers>

<!--Adding labels collection to the scale collection-->

<e-labels>…</e-labels>

<!--Adding ticks collection to the scale collection-->

<e-ticks>

<e-tick e-type="major" e-distanceFromScale="2" e-height="16"

e-width="1" e-color="#8c8c8c">

</e-tick>

<e-tick e-type="minor" e-distanceFromScale="2" e-height="8"

e-width="1" e-color="#8c8c8c">

</e-tick>

</e-ticks>

</e-scale>

</e-scales>

</ej-CircularGauge>

{% endhighlight %}

Execute the above code to render the following output.

![](MVVM_images/MVVM_img5.png)

Circular gauge with ticks customization in AngularJS
{:.caption}


## Adding Range Collection

Range is an array object. You can use the inner tag for it. Object in the array collection (i.e. border) is extended with hyphen in the same tag.

Example: e-border-color. 
{% highlight html %}
<!--To Render the Circular gauge-->

<ej-CircularGauge id="CircularGauge1">

<!--Adding Scale collection to the Circular gauge-->

<e-scales>

<e-scale>

<!--Adding pointer collection to the scale collection-->

<e-pointers>…</e-pointers>

<!--Adding labels collection to the scale collection-->

<e-labels>…</e-labels>

<!--Adding ticks collection to the scale collection-->

<e-ticks>…</e-ticks>

<!--Adding ranges collection to the scale collection-->

<e-ranges>

<e-range e-distanceFromScale="-30" e-startValue="0" e-endValue="70">

</e-range>

<e-range e-distanceFromScale="-30" e-startValue="70"

e-endValue="110" e-backgroundColor="#fc0606"

e-border-color="#fc0606">

</e-range>

<e-range e-distanceFromScale="-30" e-startValue="110"

e-endValue="120" e-backgroundColor="#f5b43f"

e-border-color="#f5b43f">

</e-range>

</e-ranges>

</e-scale>

</e-scales>

</ej-CircularGauge>

{% endhighlight %}

Execute the above code to render the following output.

![](MVVM_images/MVVM_img6.png)

Circular gauge Rendered in AngularJS
{:.caption}




## Two Way Binding 

Circular Gauge support the two way binding for the property value, minimum and maximum as mentioned earlier. The following code example explains how to achieve the two way binding in Circular Gauge.
{% highlight html %}

<div ng-app="syncApp">

<div ng-controller="CircularGauge">

<div>

<ej-CircularGauge id="CircularGauge1" e-backgroundColor="transparent" e-value="nvalue" e-width="500" e-readOnly="false" e-load= "loadGaugeTheme" e-enableAnimation="false">

<e-scales>

<e-scale e-showRanges="true" e-startAngle="122" e-sweepAngle="296"

e-radius="130" e-showScaleBar="true" e-size="1"

<!—binding maximum value using angular JS -->

e-maximum="maximum"

<!—binding minimum value using angular JS -->

e-minimum="minimum"

e-majorIntervalValue="20"

e-minorIntervalValue="10" e-border-width="0.5">

<e-pointers>

<e-pointer e-showBackNeedle="true" e-backNeedleLength="20"

e-length="95" e-width="7"

<!—binding pointer value using angular JS -->

e-value="value"

e-pointerCap-radius="12">

</e-pointer>

</e-pointers>

<e-labels>

<e-label e-color="#8c8c8c"></e-label>

</e-labels>

<e-ticks>

<e-tick e-type="major" e-distanceFromScale="2" e-height="16"

e-width="1" e-color="#8c8c8c">

</e-tick>

<e-tick e-type="minor" e-distanceFromScale="2" e-height="8"

e-width="1" e-color="#8c8c8c">

</e-tick>

</e-ticks>

<e-ranges>

<e-range e-distanceFromScale="-30" e-startValue="0" e-endValue="70">

</e-range>

<e-range e-distanceFromScale="-30" e-startValue="70"

e-endValue="110" e-backgroundColor="#fc0606"

e-border-color="#fc0606">

</e-range>

<e-range e-distanceFromScale="-30" e-startValue="110"

e-endValue="120" e-backgroundColor="#f5b43f"

e-border-color="#f5b43f">

</e-range>

</e-ranges>

</e-scale>

</e-scales>

</ej-CircularGauge>

</div>

<input type="text" id="txtMax" e-value="nvalue" ej-numerictextbox ng-model="nvalue"  e-decimalplaces="2" e-showspinbutton="false" Style="width:110px"/>

</div>

</div>

<script type="text/javascript">



<!—binding the value to the scope variables in application controller-->



angular.module('syncApp', ['ejangular'])

.controller('CircularGauge', function ($scope) {

$scope.value = 50;

$scope.minimum = 0;

$scope.maximum = 120;



});

</script>

{% endhighlight  %}

Execute the above code to render the following output.

![](MVVM_images/MVVM_img7.png)

Circular gauge with two way binding in AngularJS
{:.caption}

## KnockoutJS

* KnockoutJS support allows you to bind the HTML elements against any of the available data models.Two types of KnockoutJS binding is supported as of AngularJS,
1. one-way binding
2. two-way binding
* One way binding refers to the process of applying observable values to all the available properties of the Circular Gauge control, but the changes made in gauge control does not reflect and trigger in turn to the observable collection. This kind of binding applies to all the properties of the circular gauge control.
* Two-way binding supports both the processes – it applies the observable values to the Circular Gauge properties as well as the changes made in the Circular Gauge control also reflects back and triggers within the observable collections. Only few of the schedule properties support two-way binding and they are as follows
1. value
2. maximum 
3. minimum


{% highlight CSHTML %}


<div id="CircularGauge1"

data-bind="ejCircularGauge: {

value:sampleValue,

minimum:minimumValue,

maximum:maximumValue

}">

</div>
{% endhighlight  %}
{% highlight js %}
<script type="text/javascript">

$(function () {

window.viewModel = {

sampleValue: ko.observable(50),

minimumValue: ko.observable(10),

maximumValue: ko.observable(150)

};

$(function () {

ko.applyBindings(viewModel);

});

});

</script>
{% endhighlight  %}


Execute the above code to render the following output. The following screenshot is the output of ASP.



![](MVVM_images/MVVM_img8.png)

Circular Gauge with KnockoutJS binding
{:.caption}


