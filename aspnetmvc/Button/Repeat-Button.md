---
layout: post
title: Repeat-Button
description: repeat button
platform: ejmvc
control: Button
documentation: ug
---

# Repeat Button

When you press button continuously, click event is raised at each specific time interval. This type of button is called Repeat Button. This functionality repeatedly raises the click event of button in both button click and from button in pressed state to the released state. TimeInterval property is used to specify the time Interval for triggering click event, when the button is in pressed state. RepeatButton property is used to set the button in repeat mode.

The following steps explains you the details about rendering the Repeat Button.

1. In the CSHTML page, configure the Button widget as follows.

{% highlight html %}

<table>
<tr>
<td>
[CSHTML]@*Add the code in CSHTML page to configure and initialize the control*@  @* Enable the button in repeat action mode and specifies time interval.*@    <div class="control">        <div class="align">            @Html.EJ().Button("repeatButton").Text("click").ShowRoundedCorner(true).Size(ButtonSize.Mini).RepeatButton(true).TimeInterval("200").ClientSideEvents(e => e.Click("btnClick"))        </div>        <div class="align">            <div><b>Event Trace</b></div>            <div class="eventTrace"></div>        </div>    </div></td></tr>
<tr>
<td>
[JavaScript]//Add this script section that is used to handle the click event    <script type="text/javascript">        function btnClick(e) {            $(".eventTrace").html("click event has been triggered..</br>" + $(".eventTrace").html());        }    </script></td></tr>
</table>


{% endhighlight  %}

2. Configure the CSS styles to apply on button

{% highlight css %}

[CSS]

<style>

        .align {

            display: table-cell;

            padding-left: 50px;

        }

    </style>

{% endhighlight  %}

Execute the above code to render the following output.

![](Repeat-Button_images/Repeat-Button_img1.png)



_Figure 10: Output for repeat button_

