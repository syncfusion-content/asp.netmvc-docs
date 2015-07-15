---
layout: post
title: Scroller-Styles
description: scroller styles
platform: ejmvc
control: Scroller
documentation: ug
---

## Scroller Styles

The Essential ASP.NET MVCScroller control allows you to customize the look and function of scrollbars. You can vary it significantly by setting the scrollbar button size, scrollbar position, height and width of the Scroller control. This section describes you the custom styles to be used when creating Scroller.

Button Size

In Scroller control, it allows you to customize the scroll arrows width and height. In horizontal scroller the ButtonSize customizes the top and down arrow and in vertical scroller the ButtonSize customizes the left and right arrow.

Scroller Size

The ScrollerSize property is used to customize the scrollbar width and height. It is applicable for both horizontal and vertical scroller.

Scroll Top

The ScrollerTop property is used to move the Scroller content and scrollbars in top position with the specified value. It is used for only vertical scroller.

Scroll Left

The ScrollerLeft property is used to move the Scroller content and scrollbars in left position with the specified value. It is used for only horizontal scroller.

Height

The Height property is used to set the height for Scroller outer wrapper.

Width

The width property is used to set the Width for Scroller outer wrapper.

In the View page, add the Scroller helper to configure Scroller widget.



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



@{Html.EJ().Scroller("scrollcontent").Height(170).Width(350).ScrollTop(10).ScrollLeft(20).ButtonSize(20).Render();}





1. Configure the styles 


[CSS]



&lt;style type="text/css"&gt;



    #innercontent {

        width: 400px;

        padding: 15px;

    }



    #scrollcontent {

        border: 1px solid grey;

    }



&lt;/style&gt;



The following screenshot displays the Scroller control with basic styles

{ ![C:/Users/labuser/Desktop/scroller.png](Scroller-Styles_images/Scroller-Styles_img1.png) | markdownify }
{:.image }


_Figure_ _5__: Scroller control rendered with basic styles_

