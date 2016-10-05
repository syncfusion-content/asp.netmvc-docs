---
layout: post
title: Getting started | Tooltip | ASP.NET MVC | Syncfusion
description: How to create the Tooltip
platform: ejmvc
control: Tooltip
documentation: ug
keywords : MVC Tooltip, mvc Tooltip, ASP.NET MVC Tooltip,MVC Tooltip widget,MVC Tooltip Appearance, MVC Tooltip Dimensions
---
# Getting started

## Create a Tooltip

Using the following steps, you can create a Tooltip control. The basic rendering of ASP.NET MVC Tooltip is achieved with default functionality.



1. You can create an MVC Project and add necessary assembly and script with the help of the given [MVC-Getting Started](http://help.syncfusion.com/aspnetmvc/getting-started) Documentation.



2. Add the mentioned code to the corresponding view page for Tooltip rendering.

{% highlight CSHTML %}

    <div class="frame">    
        <div class="img" id="sample1">
            <a target="_blank" href="image/taj.png">
            <img src="http://mvc.syncfusion.com/demos/web/content/images/tooltip/template-05.png" alt="Delphi">
            </a>
            <div class="desc">Delphi Succinctly</div>
        </div>
    </div>

    @Html.EJ().Tooltip("sample1").Content("Learn the fundamentals of Delphi to build a variety of solutions for many devices and platforms.")



{% endhighlight %}

Apply the following style sheet

{% highlight css %}

    <style>
        div.img {
            border: 1px solid #ccc;
            width: 159px;
            height: 213px;
            left: 35%;
            position: relative;
            top: 20%;
        }
        div.img img {
            width: 159px;
            height: 179px;
        }
        div.desc {
            padding: 8px;
            text-align: center;
        }
    </style>
    
{% endhighlight %}

![](Getteing-Started_images/Getteing-Started_img1.jpeg)

## Setting Dimensions

Tooltip dimensions can be set using [width](http://help.syncfusion.com/js/api/ejtooltip#members:width) and [height](http://help.syncfusion.com/js/api/ejtooltip#members:height) API.

{% highlight CSHTML %}
 
    <div class="control">
        TypeScript lets you write <a id="tooltip1"><u> JavaScript</u> </a>the way you really want to.
    </div>

    @Html.EJ().Tooltip("tooltip1").Content("JavaScript is the programming language of HTML and the Web.").Width("100px").Height("100px")
        
{% endhighlight %}

## Tooltip Appearance 

You can configure the appearance of the Tooltip with the title, close button and call out as your application requires.

{% highlight CSHTML %}
 
    <div class="img" id="sample">
        <a target="_blank" href="image/taj.png">
        <img src="http://mvc.syncfusion.com/demos/web/content/images/tooltip/template-05.png" alt="Delphi">
        </a>
        <div class="desc">Delphi Succinctly</div>
    </div>

    @Html.EJ().Tooltip("sample").Content("Learn the fundamentals of Delphi to build a variety of solutions for many devices and platforms.").Width("180px").Title("Delphi Succinctly").CloseMode(CloseMode.Sticky).IsBalloon(false)
    
{% endhighlight %}

Apply the following styles to show the Tooltip.

{% highlight css %}

    <style>
        div.img {
            border: 1px solid #ccc;
            float: left;
            box-sizing: border-box;
            height: 200px;
            width: 146px;
        }
        div.img img{
            width: 100%;
            height: 166px;
        }
        div.desc {
            padding: 6px;
            text-align: center;
        }
    </style>
    
{% endhighlight %}

![](Getteing-Started_images/Getteing-Started_img2.jpeg)

