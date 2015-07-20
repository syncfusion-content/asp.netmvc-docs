---
layout: post
title: AngularJS-Support
description: angularjs support
platform: ejmvc
control: Maps
documentation: ug
---

## AngularJS Support

AngularJS is a JavaScript framework added to a HTML page with a <script> tag. It extends HTML attributes with directives and binds data to HTML with expressions. AngularJS directives allow you to specify custom and reusable HTML tags that moderate the behavior of certain elements. Angularbinding uses directives to plug its action into the page. Directives, all prefaced with ng-, are placed in HTML attributes. To know more about Angular binding refer to: [http://help.syncfusion.com/ug/js/#!documents/angularjs.htm](http://help.syncfusion.com/ug/js/)

Apply the plugin and property assigning the Map element through the directive that starts with the letter “e-“.  The following code illustrates how to bind data to the Map component through Angular support.



{% highlight html %}

[MVC]

[CSHTML]



//References to be added for angular support.



   <script src="@Url.Content("~/Scripts/angular.min.js")"></script>

   <script src="@Url.Content("~/Scripts/ej/ej.widget.angular.min.js")"></script>    

   <script src="@Url.Content("~/Scripts/MapsData/USA.js")"></script>

//Initializes Map

   <div ng-app="SyncApp">

       <div ng-controller="MapController">           

           <div id="map" style="height: inherit; min-height: 356px;" ej-map e-zoomsettings- enablezoom="nenablezoom">

               <div e-layers>

                   <div e-layer e-shapedata="nshapedata" e-shapesettings-fill="nfill" e-shapesettings-strokethickness="nstrokeThickness" e-shapesettings-stroke="nstroke">

                   </div>

               </div>

           </div>       

           <div>

                Shape Color:  <input type="text" id="Text11" ng-model="nfill" style="width: 110px">

           </div> 



       </div>

   </div>

angular.module('SyncApp', ['ejangular'])

       .controller('MapController', function ($scope) {          

           $scope.nenablezoom = true,          

           $scope.nshapedata = usMap;

           $scope.nfill = "#9CBF4E";

           $scope.nstrokethickness = "0.5";

           $scope.nstroke = "white";      

       });



{% endhighlight %}



{{ '![1](AngularJS-Support_images/AngularJS-Support_img1.png)' | markdownify }}
{:.image }






