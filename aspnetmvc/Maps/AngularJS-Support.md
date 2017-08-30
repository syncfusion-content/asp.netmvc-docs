---
layout: post
title: AngularJS Support
description: Learn how to customize map control using angularjs support
platform: ejmvc
control: Maps
documentation: ug
---

# AngularJS Support

`AngularJS` is a JavaScript framework added to a HTML page with a &lt;script&gt; tag. It extends HTML attributes with directives and binds data to HTML with expressions. AngularJS directives allow you to specify custom and reusable HTML tags that moderate the behavior of certain elements. 

`Angular binding` uses directives to plug its action into the page. Directives, all prefaced with ng-, are placed in HTML attributes. To know more about Angular binding refer to: <http://help.syncfusion.com/aspnetmvc/maps/angularjs-support>

Apply the plugin and property assigning the Map element through the directive that starts with the letter “e-“.  The following code illustrates how to bind data to the Map component through Angular support.



{% highlight CSHTML %}


      //References to be added for AngularJS support.

            <script src="@Url.Content("~/Scripts/angular.min.js")"></script>

            <script src="@Url.Content("~/Scripts/ej/ej.widget.angular.min.js")"></script>    

            <script src="@Url.Content("~/Scripts/MapsData/USA.js")"></script>

      //Initializes Map

            <div ng-app="SyncApp">

                  <div ng-controller="MapController">           

	                 <div id="map" style="height: inherit; min-height: 356px;" ej-map e-zoomsettings- enablezoom="enableZoom">

		                <div e-layers>

			               <div e-layer e-shapedata="shapeData" e-shapesettings-fill="fill" e-shapesettings-strokethickness="strokeThickness" e-shapesettings-stroke="stroke">

			               </div>

		                </div>

	                 </div> 
                       
                       Shape Color:  <input type="text" id="Text11" ng-model="nfill" style="width: 110px">      

	            <div>			

	      </div> 	      


            angular.module('SyncApp', ['ejangular'])

            .controller('MapController', function ($scope) 
            
            {          

                  $scope.enableZoom = true,          

                  $scope.shapeData = usMap;

                  $scope.fill = "#9CBF4E";

                  $scope.strokeThickness = "0.5";

                  $scope.stroke = "white";      

            });

{% endhighlight %}



![](AngularJS-Support_images/AngularJS-Support_img1.png)




