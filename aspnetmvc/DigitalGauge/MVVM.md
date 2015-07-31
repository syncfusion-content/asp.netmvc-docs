---
layout: post
title: MVVM
description: mvvm
platform: ejmvc
control: Digital Gauge
documentation: ug
---

## MVVM

Angular JS

Digital Gauge contains angular support. It is possible to add object as well as array object in the Digital Gauge. The two way binding support is given to the value for displaying the text.



### Rendering the Digital Gauge

ej-DigitalGauge is the control tag, where ej is tag prefix and DigitalGauge is the control name.Digital Gauge is rendered with the following code example.

<div ng-app="syncApp">

<div ng-controller="DigitalGauge">

<ej-DigitalGauge id="digitalCore" e-height="500" e-load="loadGaugeTheme">

</ej-DigitalGauge>

</div>

</div>

<script type="text/javascript">

<!—binding the value to the scope variables in application controller-->

angular.module('syncApp', ['ejangular'])

.controller('DigitalGauge', function ($scope) {

$scope.nvalue = “text”;

});

</script>





Execute the above code to render the following output.

{{ '![](MVVM_images/MVVM_img1.png)' | markdownify }}
{:.image }




### Adding the Digital Gauge Items

Digital Gauge is rendered with the following code example. You can extend the Object in the array collection such as, position, characterSetting, segmentSetting, etc. with hyphen in the same tag.

Example: e-position-x. 



<!--To Render the Digital gauge-->

<ej-DigitalGauge id="digitalCore">

<!--Adding Item collection to the digital gauge-->

<e-items>

<e-item e-segmentSettings-width="1" e-segmentSettings-spacing="0"

e-value="Syncfusion" e-characterSetting-opacity="0.8"

e-position-x="52" e-position-y="52">

</e-item>

</e-items>

</ej-DigitalGauge>



Finally while running the above codes, the following output will be rendered.

{{ '![](MVVM_images/MVVM_img2.png)' | markdownify }}
{:.image }




### Two Way Binding

Digital Gauge supports the two way biding for the property value as mentioned earlier. Following code example explains how to achieve the two way binding to the Digital Gauge.

<div ng-app="syncApp">

<div ng-controller="DigitalGauge">

<ej-DigitalGauge id="digitalCore" e-height="200" e-load="loadGaugeTheme">

<e-items>

<e-item e-segmentSettings-width="1" e-segmentSettings-spacing="0"

e-characterSetting-opacity="0.8" e-position-x="52"

e-value="nvalue" e-position-y="52">

</e-item>

</e-items>

</ej-DigitalGauge>

Type here <input type="text" id="txtValue" ng-model="nvalue" Style="width:110px"/>

</div>

</div>



<script type="text/javascript">



<!—binding the value to the scope variables in application controller-->



angular.module('syncApp', ['ejangular'])

.controller('DigitalGauge', function ($scope) {

$scope.nvalue = "Syncfusion";

});

</script>





Execute the above code to render the following output.

{{ '![](MVVM_images/MVVM_img3.png)' | markdownify }}
{:.image }




### Knockout Binding



* Knockout support allows you to bind the html elements against any of the available data models.Two types of knockout binding is supported as of angular,
1. one-way binding
2. two-way binding
* One way binding refers to the process of applying observable values to all the available properties of the Digital Gauge control, but the changes made in it does not reflect and trigger in turn to the observable collection. This kind of binding applies to all the properties of the Digital Gauge control.
* Two-way binding supports both the processes – it applies the observable values to the Digital Gauge properties as well as the changes made in it is also reflected back and triggered within the observable collections. Only Value of the schedule properties support two-way binding.



[MVC]

 [CSHTML]

    <div id="digitalCore" 

         data-bind="ejDigitalGauge: { 

value: samplevalue,

                    }">

    </div>

    <script type="text/javascript">

        $(function () {

            window.viewModel = {

             samplevalue: ko.observable(“syncfusion”),

            };

            $(function () {

                ko.applyBindings(viewModel);

            });

        });

    </script>


Execute the above code to render the following output.





{{ '![C:/Users/karthigeyan/Desktop/q.png](MVVM_images/MVVM_img4.png)' | markdownify }}
{:.image }




















_Figure_ _4__1: Digital Gauge with Knockout binding_



