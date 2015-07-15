---
layout: post
title: RTL-Support
description: rtl support
platform: ejmvc
control: Splitter
documentation: ug
---

## RTL Support

The Splitter provides you with RTL (Right-To-Left) support. The alignment of Splitter can be changed from Left-To-Right to Right-To-Left.

Enable RTL

The following steps explain enabling the right-to-left property for Splitter widget.

In the View page add the Splitter helper to enable the RTL functionality. 



[CSHTML]



@{Html.EJ().Splitter("outterSplitter").Height("300").Width("600").Orientation(Orientation.Vertical).EnableRTL(true)

      .PaneProperties(

    p =>

    {

        p.Add().ContentTemplate(

            @&lt;div&gt;

                &lt;div class="content" style="padding: 0px 15px;"&gt;

                    &lt;h3 class="h3"&gt;

                        ASP.NET MVC

                    &lt;/h3&gt;

                &lt;/div&gt;

            &lt;/div&gt;).PaneSize("60");

        p.Add().ContentTemplate(

            @&lt;div style="height: 100%; width: 100%"&gt;

                @innerSplitter()

            &lt;/div&gt;);

    }).Render();}



@helper innerSplitter()

{

    @Html.EJ().Splitter("innerSplitter").Width("600").PaneProperties(p1 =>

                {

                    p1.Add().ContentTemplate(@&lt;div&gt;

                        &lt;div class="content"&gt;

                            &lt;h3 class="h3"&gt;

                                Tools

                            &lt;/h3&gt;

                            Essential Tools is an collection of user interface components used to create interactive

                            ASP.NET MVC applications.

                        &lt;/div&gt;

                    &lt;/div&gt;).PaneSize("200");

                    p1.Add().ContentTemplate(@&lt;div&gt;

            &lt;div class="content"&gt;

                &lt;h3 class="h3"&gt;

                    Chart

                &lt;/h3&gt;

                Essential Chart is a business-oriented charting component.

            &lt;/div&gt;

        &lt;/div&gt;).PaneSize("200");

                    p1.Add().ContentTemplate(@&lt;div&gt;

            &lt;div class="content"&gt;

                &lt;h3 class="h3"&gt;

                    Grid

                &lt;/h3&gt;

                Essential Mvc Grid offers full featured a Grid control with extensive support for

                Grouping and the display of hierarchical data.

            &lt;/div&gt;

        &lt;/div&gt;).PaneSize("200");

                })

}

[CSS]

&lt;style type="text/css"&gt;

    #outterSplitter {

        margin: 0 auto;

    }

    .h3 {

        font-size: 14px;

    }

    #innerSplitter {

        border: 0 none;

    }

    .content {

        padding: 15px;

    }

&lt;/style&gt;







The output for Splitter when EnableRTL is “True”.



{ ![](RTL-Support_images/RTL-Support_img1.png) | markdownify }
{:.image }








__

