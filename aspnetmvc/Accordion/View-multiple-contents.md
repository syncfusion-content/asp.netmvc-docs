---
layout: post
title: View-multiple-contents
description: view multiple contents
platform: ejmvc
control: Accordion 
documentation: ug
---

## View multiple contents

By default Accordion allows only one panel to be in expanded state. You can enable multiple panels in expand state by setting EnableMultipleOpen to true.

Enabling multiple panel open

The following code explains you to enable multiple panel for Accordion.



[CSHTML]

// In the View page, render Accordion with corresponding data and set EnableMultipleOpen property as true.



<div style="width: 400px">

@{Html.EJ().Accordion("accordion").Items(data =>

            {

                data.Add().Text("Essential Chart").ContentTemplate(@<div>

                    Essential Chart for ASP.NET MVC is a visually stunning, high-performance charting component that is easy to use. It includes 35 chart types ranging from simple column charts to specialized financial charts. The charts are highly customizable and have a powerful data model that makes data binding simple.

                </div>);

                data.Add().Text("Essential Schedule").ContentTemplate(@<div>

                    Essential Schedule for ASP.NET MVC is an Outlook Calendar-like scheduler control that lets you add rich scheduling capabilities to your web applications. It includes an advanced set of features including data binding, multiple resource views, rich interactivity, support for AJAX, client-side events, and much more.

                </div>);

                data.Add().Text("Essential Grid").ContentTemplate(@<div>

                    Essential Grid for ASP.NET MVC is a feature-rich control that provides extensive appearance customization options with support for grouped records. With Essential Grid for ASP.NET MVC, you can create a grid with a highly customizable look and feel. This grid is very useful for generating complex grid-based reports with rich formatting. It supports paging, sorting, grouping, filtering, and editing features. It also supports a JSON mode in which you can handle all the operations like paging and sorting. The performance of these operations in the JSON mode will be much faster than if the grid were to handle them. Essential Grid generates clean HTML in compliance with XHTML 1.0. It supports any kind of IEnumerable data source. It uses LINQ data retrieval techniques for handling data sources, and offers high performance.</div>);

            }).EnableMultipleOpen(true).Render();}

</div>



Following screenshot is the output for Accordion control on EnableMultipleOpen set to true.


{{ '![](View-multiple-contents_images/View-multiple-contents_img1.png)' | markdownify }}
{:.image }




