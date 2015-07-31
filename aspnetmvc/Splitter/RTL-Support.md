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

            @<div>

                <div class="content" style="padding: 0px 15px;">

                    <h3 class="h3">

                        ASP.NET MVC

                    </h3>

                </div>

            </div>).PaneSize("60");

        p.Add().ContentTemplate(

            @<div style="height: 100%; width: 100%">

                @innerSplitter()

            </div>);

    }).Render();}



@helper innerSplitter()

{

    @Html.EJ().Splitter("innerSplitter").Width("600").PaneProperties(p1 =>

                {

                    p1.Add().ContentTemplate(@<div>

                        <div class="content">

                            <h3 class="h3">

                                Tools

                            </h3>

                            Essential Tools is an collection of user interface components used to create interactive

                            ASP.NET MVC applications.

                        </div>

                    </div>).PaneSize("200");

                    p1.Add().ContentTemplate(@<div>

            <div class="content">

                <h3 class="h3">

                    Chart

                </h3>

                Essential Chart is a business-oriented charting component.

            </div>

        </div>).PaneSize("200");

                    p1.Add().ContentTemplate(@<div>

            <div class="content">

                <h3 class="h3">

                    Grid

                </h3>

                Essential Mvc Grid offers full featured a Grid control with extensive support for

                Grouping and the display of hierarchical data.

            </div>

        </div>).PaneSize("200");

                })

}

[CSS]

<style type="text/css">

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

</style>







The output for Splitter when EnableRTL is “True”.



{{ '![](RTL-Support_images/RTL-Support_img1.png)' | markdownify }}
{:.image }








__

