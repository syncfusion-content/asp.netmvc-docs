---
layout: post
title: Thumb-Scrolling
description: thumb scrolling
platform: ejmvc
control: Scroller
documentation: ug
---

## Thumb Scrolling

Normally the scrollbar position can be changed by dragging the scrollbar handle or clicking the arrows. The Scroller control allows you for panning or dragging the scroll content area to drag by dragging inside the scroll content. To achieve this in your Scroller control, enable the EnableTouchScroll to true_._ By default the value for__EnableTouchScroll is true. When you want to prevent the panning or dragging the scroll content area, set EnableTouchScroll as false.

The following steps explains you the configuration of EnableTouchScroll property in Scroller. 

1. In the View page, add a scroller helper to configure the EnableTouchScroll property.





[CSHTML]

// In the CSHTML page, add a &lt;div&gt; element to configure Scroller widget and initialize the control.



&lt;div id="scrollcontent"&gt;

  &lt;div&gt;                              @*Wrapper div for Scroller.*@

     &lt;div id="innercontent"&gt;         @*Content div*@

        <h3>MVC &lt;/h3&gt;

         &lt;p&gt;

           Model–view–controller (MVC) is a software architecture pattern which   

           separates the representation of information from the user's interaction

           with it. The model consists of application data, business rules, logic, and

           functions. A view can be any output representation of data, such as a chart

           or a diagram.

         &lt;/p&gt;

    &lt;/div&gt;

  &lt;/div&gt;

&lt;/div&gt;



@{Html.EJ().Scroller("scrollcontent").Height(170).Width(350).EnableTouchScroll(false).Render();}







The following screenshot displays Scroller control with disabled touch support.

{ ![](Thumb-Scrolling_images/Thumb-Scrolling_img1.png) | markdownify }
{:.image }


_Figure_ _6__: Scroller control with disabled touch support_

