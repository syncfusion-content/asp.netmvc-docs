---
layout: post
title: Customization | Tooltip | ASP.NET MVC | Syncfusion
description: Customization in Tooltip widget for Syncfusion Essential MVC
platform: ejmvc
control: Tooltip
documentation: ug
keywords : MVC Tooltip, mvc Tooltip, ASP.NET MVC Tooltip,MVC Tooltip widget,MVC Tooltip template,MVC Tooltip Animation
---

# Customization

## Template Support

By default you can add any text or image to the Tooltip. To customize the tooltip layout or to create your own visualized elements you can use this template support.

{% highlight CSHTML %}

    <div class="ctrl" id="centerImage">
        <img class="ctrImg" src="http://mvc.syncfusion.com/demos/web/content/images/tooltip/template-04.png" />
        <div class="new">Roslyn Succinctly</div>
    </div>

    @Html.EJ().Tooltip("centerImage").Content("<div class='main'> <div class='poster'> <img src='http://mvc.syncfusion.com/demos/web/content/images/tooltip/template-2.png' width='150px' height='120px'> </div> <div class='def'> <h4> Roslyn Succinctly </h4><div class='description'>Microsoft has only recently embraced the world of open source software, offering <a href='#'>More...</a> </div>").Width("350px")

{% endhighlight %}
{% highlight css %}

    <style>
        h4 {
            margin-top: 0px;
            margin-bottom: 2px;
        }
        .e-tooltip-wrap .e-tipContainer .e-tipcontent {
            padding: 5px 0px;
        }
        .poster {
            float: left;
            padding: 4px 0px;
        }
        .new {
            text-align: center;
        }
        .def {
            float: right;
        }
        .ctrl {
            border: 1px solid #ebebe0;
            width: 150px;
            padding: 5px;
            height: 180px;
            margin-top: 239px;
            margin-left: 250px;
        }
        .ctrImg {
            width: 150px;
            height: 160px;
        }
        .category {
            margin-left: 10px;
        }
        .description {
            width: 200px;
            height: 60px;
            line-height: 22px;
            margin-top: 10px;
        }
    </style>
    
{% endhighlight %}

![](Customization_images/template.png)

### Tooltip’s title customization

Tooltip title can be customized with the image or any HTML element. 

{% highlight CSHTML %}
    
    <div class="ctrl" id="centerImage">
        <img class="ctrImg" src="http://mvc.syncfusion.com/demos/web/content/images/tooltip/template-04.png" />
        <div class="new">Roslyn Succinctly</div>
    </div>

    @Html.EJ().Tooltip("centerImage").Content("<div>Microsoft has only recently embraced the world of open source software, offering <a href='#'>More...</a> </div>").Title("<div><img class='titleImg' src='http://mvc.syncfusion.com/demos/web/content/images/tooltip/template-2.png' /> <div class='description'> Roslyn Succinctly </div> </div> ")

 {% endhighlight %}   
 {% highlight css %}
    <style>
        .titleImg {
            width: 20px;
            height: 20px;
            float: left;
            margin-right: 10px;
        }
        #centerImage{
            margin-left : 300px;
            margin-top : 250px;
            position : absolute;
            border: 1px solid grey;
        }
        .description {
            height: 20px;
        }
    </style>

{% endhighlight %}

![](Customization_images/title.png)

## Animation Effects

Determines the type of effect that takes place when showing/hiding the tooltip.

We can specify the effect and the duration for the animation. 

<table>
<tr>
<td>
Effects<br/></td><td>
Description<br/></td></tr>
<tr>
<td>
Slide<br/></td><td>
Sliding animation effect takes place with a duration of 200ms.<br/></td></tr>
<tr>
<td>
Fade<br/></td><td>
Fading animation effect takes place with a duration of 800ms.<br/></td></tr>
<tr>
<td>
None (Default)<br/></td><td>
No effect takes place<br/></td></tr>
</table>

Let's create a Tooltip that slides down when shown using the [animation](http://help.syncfusion.com/js/api/ejtooltip#members:animation) property:

{% highlight CSHTML %}

    <div class="control">
        TypeScript lets you write <a id="tooltip1"><u> JavaScript</u> </a>the way you really want to.
    </div>

    @Html.EJ().Tooltip("tooltip1").Content("JavaScript is the programming language of HTML and the Web.").Animation(anim => anim.Effect(Effect.Slide).Speed(1000))
   
{% endhighlight %}

### Custom Animation

Custom animation effect for both Tooltip show/hide can also be done by [show](http://help.syncfusion.com/js/api/ejtooltip#methods:show) and [hide](http://help.syncfusion.com/js/api/ejtooltip#methods:hide) method.

Show or Hide method may receive an optional 'callback' parameter, which represents a function you'd like to call which will animate the tooltip.

 
{% highlight CSHTML %}

    <div class="control">
        TypeScript lets you write <a id="tooltip2"><u> JavaScript</u> </a>the way you really want to.
    </div>
    @Html.EJ().Button("open").Size(ButtonSize.Large).ShowRoundedCorner(true).Text("Open").ClientSideEvents(events => events.Click("onClick"))

    @Html.EJ().Tooltip("tooltip2").Content("JavaScript is the programming language of HTML and the Web.")
   
    <script>
        var tip;
        function onClick(args){
            tip = $("#tooltip2").data("ejTooltip");
            tip.show(null,"myFunc");
        }
        function myFunc(args) {
            tip = $("#tooltip2").data("ejTooltip");
            $(tip.tooltip).slideDown(200, "easeOutElastic");
        }
        
    </script>

{% endhighlight %}

N> Show or Hide method can also receive an optional parameter “effect name”, (e.g any easing effect name) which specifies the type of effect taken place when showing/hiding of the tooltip, please refer to the following link for online demo - [link](http://mvc.syncfusion.com/demos/web/tooltip/animation).

## Modernize the tooltip’s content

It's easy to update a tooltip’s content – whether it’s open or closed.

{% highlight CSHTML %}

    <div class="control">
        TypeScript lets you write <a id="tooltip3"><u> JavaScript</u> </a>the way you really want to.
        @Html.EJ().Button("open").Size(ButtonSize.Large).ShowRoundedCorner(true).Text("Update Content").ClientSideEvents(events => events.Click("onClick"))
    </div>

    @Html.EJ().Tooltip("tooltip3").Content("JavaScript is the programming language of HTML and the Web.")

    <script type="text/javascript">
        function onClick(args){
            tip = $("#tooltip3").data("ejTooltip");
            tip.setModel({ content: "JavaScript" });
            tip.show();
        }
    </script>
    
{% endhighlight %}

## Closing Mode

By default, the Tooltip will be hidden when mouse leaves the target element. Different types of close mode as follows 

<table>
<tr>
<td>
Types<br/></td><td>
Description<br/></td></tr>
<tr>
<td>
Auto<br/></td><td>
Tooltip will be hidden after a particular period of time.<br/></td></tr>
<tr>
<td>
Sticky<br/></td><td>
Tooltip rendered with the button, it will close the tooltip.<br/></td></tr>
<tr>
<td>
None (Default)<br/></td><td>
Tooltip will be hidden when mouse leaves the target element.<br/></td></tr>
</table>

### Auto

The tooltip will be visible only for the period of time specified in the [autoCloseTimeout](http://help.syncfusion.com/js/api/ejtooltip#members:autoclosetimeout).

Let see an example, this Tooltip will only hide after hovering the target for 2000ms

{% highlight CSHTML %}

    <div class="control">
        TypeScript lets you write <a id="tooltip4"><u> JavaScript</u> </a>the way you really want to.
    </div>

    @Html.EJ().Tooltip("tooltip4").Content("JavaScript is the programming language of HTML and the Web.").CloseMode(CloseMode.Auto).AutoCloseTimeout(2000)

{% endhighlight %}

N> Time specified in the autoCloseTimeout will be in milliseconds and the default value is 4000ms

### Sticky

A close button will be shown with the Tooltip. The button element (i.e. close button) located by default at the top right of the Tooltip or title bar (if title is enabled). The tooltip gets closed when the button is clicked.

{% highlight CSHTML %}

    <div class="control">
        TypeScript lets you write <a id="tooltip5"><u> JavaScript</u> </a>the way you really want to.
    </div>

     @Html.EJ().Tooltip("tooltip5").Content("JavaScript is the programming language of HTML and the Web.").CloseMode(CloseMode.Sticky).Width("200px")

{% endhighlight %}

![](ClosingBehaviour_images/sticky.png)

You can also have Tooltip with a title, in which case the button will lye within it:

{% highlight CSHTML %}

    <div class="control">
        TypeScript lets you write <a id="tooltip6"><u> JavaScript</u> </a>the way you really want to.
    </div>

     @Html.EJ().Tooltip("tooltip6").Content("JavaScript is the programming language of HTML and the Web.").CloseMode(CloseMode.Sticky).Width("200px").Title("JavaScript")

{% endhighlight %}

![](ClosingBehaviour_images/title.png)

    
