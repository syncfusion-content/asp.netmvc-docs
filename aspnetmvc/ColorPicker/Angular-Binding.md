---
layout: post
title: Angular-Binding
description: angular binding
platform: ejmvc
control: ColorPicker
documentation: ug
---

## Angular Binding

The ColorPicker widget is availed with two types of angularJS support namely, 

* One-way binding
* Two-way binding 

One-way binding refers to the process of applying scope values to all the available properties of the ColorPicker widget. The changes made in ColorPicker widget are not reflected or triggered in turn to the scope collection. This kind of binding is applied to all the properties of the ColorPicker widget.

Two-way binding supports both the processes. It applies the scope values to the ColorPicker properties, as well as the changes made in the ColorPicker widget are reflected back and triggered within the angular scope change function.

Apply the plugin and property assigning to the ColorPicker widget element through the directive that starts with “e-“.

To know more about the Angular binding, you can refer to the online documentation in the following link location,

[http://help.syncfusion.com/ug/js/documents/angularjs.htm](http://help.syncfusion.com/ug/js/documents/angularjs.htm)

1. The following code example depicts the way to bind data to the ColorPicker widget through angular support.



[CSHTML]

@*Add the following scripts in your view page for angular support*@

<script src="http://cdn.syncfusion.com/js/assets/external/angular.min.js"></script>

<script src="http://cdn.syncfusion.com/13.1.0.21/js/web/ej.unobtrusive.min.js"> </script>

<script src="http://cdn.syncfusion.com/13.1.0.21/js/ej.widget.angular.min.js"> </script>



<div class="content-container-fluid" ng-app="PickerCtrl">

    <div class="row" style="width: 100%" ng-controller="ColorPickerCtrl">

        <div class="cols-sample-area" style="width: 100%">

            <div class="frame">

                <div id="control">

                    <div class="element" style="margin-left: 45px;">

                        <input id="picker" ej-colorpicker e-value="colorValue" e-modeltype="palette" />

                    </div>

                    <div class="element" style="margin-left: 234px">

                        <input id="custom" ej-colorpicker e-value="colorValue" e-modeltype="picker" />

                    </div>

                    <h6><span style="font-style: italic; font-weight: normal; position: absolute; margin-top: 5px; margin-left: 45px;">Note:Two Way Angular Support</span></h6>

                </div>

            </div>

        </div>



        <script>

            angular.module('PickerCtrl', ['ejangular'])

              .controller('ColorPickerCtrl', function ($scope) {

                  $scope.colorValue = "#278787";

              });

        </script>

    </div>

</div>



<style>

    .element {

        display: inline-block;

    }



    .frame {

        width: 457px;

        border: 0px;

    }



    #control {

        width: 600px;

    }

</style>





The following screenshot displays the output of the above code example.

{{ '![](Angular-Binding_images/Angular-Binding_img1.png)' | markdownify }}
{:.image }


