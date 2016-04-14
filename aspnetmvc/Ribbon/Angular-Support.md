---
layout: post
title: Angular-Support | Ribbon | ASP.NET MVC | Syncfusion
description: angular-support
platform: ejmvc
control: Ribbon
documentation: ug
keywords: angular support,ribbon angular support
---

# AngularJS-Support 

It is possible to add object, array collection in the Ribbon control with AngularJS. The one way binding support is provided for Ribbon control.

`ej-ribbon` is the control tag where, `ej` is tag prefix and `Ribbon` is the control name.

## Tabs and Contextual Tabs

Ribbon Tabs and Contextual Tabs are Array Collections and the inner tag is used for them.

Objects with in these Array Collections can be extended by using hyphen. E.g. `e-applicationTab-menuItemId="menu"`

{% highlight CSHTML %}

     @section ControlsSection{
        <div ng-app="ribbonApp">
    <div ng-controller="RibbonCtrl">
        <div id="defaultRibbon" ej-ribbon e-width="100%" e-applicationtab-menuitemid="menu" e-expandpinsettings-tooltip="Collapse the Ribbon" e-collapsepinsettings-tooltip="Pin the Ribbon" e-applicationtab-type="menu" e-create="createControl">
            <div e-tabs>
                <div e-tab e-id="home" e-text="HOME">
                    <div e-groups>
                        <div e-group e-text="New" e-aligntype="rows">
                            <div e-content>
                                <div e-content e-defaults-type="button" e-defaults-width="60" e-defaults-height="70">
                                    <div e-groups>
                                        <div e-group e-id="new" e-text="New" e-customtooltip-title="New" e-customtooltip-content="
                                            <h6>New.<&#47;h6>" e-buttonsettings-contenttype="imageonly" e-buttonsettings-imageposition="imagetop" e-buttonsettings-prefixicon="e-ribbon e-new" e-buttonsettings-click="executeAction">
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div e-contextualtabs>
                    <div e-contextualtab e-backgroundcolor="#FCFBEB" e-bordercolor="#F2CC1C">
                        <div e-tabs>
                            <div e-tab e-id="Design" e-text="DESIGN">
                                <div e-groups>
                                    <div e-group e-text="New" e-aligntype="rows">
                                        <div e-content>
                                            <div e-content e-defaults-type="button" e-defaults-width="60" e-defaults-height="70">
                                                <div e-groups>
                                                    <div e-group e-id="Design" e-text="Design" e-buttonsettings-prefixicon="e-shape" e-buttonsettings-contenttype="textandimage" e-buttonsettings-imageposition="imagetop"></div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <ul id="menu">
                <li>
                    <a>FILE</a>
                    <ul>
                        <li>
                            <a>Save</a>
                        </li>
                    </ul>
                </li>
            </ul>
        </div>
    </div>
    }   
    @section ScriptSection{
    <script type="text/javascript">
        angular.module('ribbonApp', ['ejangular'])
            .controller('RibbonCtrl', function ($scope) {
            });
    </script>
    }

{% endhighlight %}

![](Angular-Support_images/Angular-Support_img1.png)

## Gallery and Custom Tooltip
                
GalleryItems is an Array Collection and the inner tag is used for it inside the Ribbon Groups. Object of this Array Collection can be extended by using hyphen.
 
Custom Tooltip is an Object of Ribbon Groups and can extend it by using hyphen. E.g. `e-customToolTip-title`.

{% highlight CSHTML %}

    @section ControlsSection{
    <div ng-app="ribbonApp">
    <div ng-controller="RibbonCtrl">
        <div id="defaultRibbon" ej-ribbon e-width="400" e-applicationtab-menuitemid="menu" e-expandpinsettings-tooltip="Collapse the Ribbon" e-collapsepinsettings-tooltip="Pin the Ribbon" e-applicationtab-type="menu" e-create="createControl">
            <div e-tabs>
                <div e-tab e-id="home" e-text="HOME">
                    <div e-groups>
                        <div e-group e-text="New" e-aligntype="columns">
                            <div e-content>
                                <div e-content e-defaults-type="button" e-defaults-width="60" e-defaults-height="70">
                                    <div e-groups>
                                        <div e-group e-id="paste" e-text="Paste" e-customtooltip-title="Paste" e-customtooltip-content="
                                            <h6>Paste the content.
                                                <br &#47;>
                                                    <br &#47;>Add content on the Clipboard to your document.<&#47;h6>" e-customtooltip-prefixicon="e-pastetip">
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                    <div e-group e-text="Gallery" e-aligntype="rows">
                                        <div e-content>
                                            <div e-content>
                                                <div e-groups>
                                                    <div e-group e-id="Gallery" e-columns="3" e-itemheight="54" e-itemwidth="68" e-expandedcolumns="4" e-type="gallery">
                                                        <div e-galleryitems>
                                                            <div e-galleryitem e-text="Content1" e-tooltip="GalleryContent1" e-buttonsettings-contenttype="textonly"></div>
                                                            <div e-galleryitem e-text="Content2" e-tooltip="GalleryContent2" e-buttonsettings-contenttype="textonly"></div>
                                                            <div e-galleryitem e-text="Content3" e-tooltip="GalleryContent3" e-buttonsettings-contenttype="textonly"></div>
                                                            <div e-galleryitem e-text="Content4" e-tooltip="GalleryContent4" e-buttonsettings-contenttype="textonly"></div>
                                                            <div e-galleryitem e-text="Content5" e-tooltip="GalleryContent5" e-buttonsettings-contenttype="textonly"></div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <ul id="menu">
                        <li>
                            <a>FILE</a>
                            <ul>
                                <li>
                                    <a>Save</a>
                                </li>
                            </ul>
                        </li>
                    </ul>
                </div>
            </div>
    } 
       @section ScriptSection{
    <script type="text/javascript">
        angular.module('ribbonApp', ['ejangular'])
            .controller('RibbonCtrl', function ($scope) {
            });
    </script>
}

{% endhighlight %}

![](Angular-Support_images/Angular-Support_img2.png)
