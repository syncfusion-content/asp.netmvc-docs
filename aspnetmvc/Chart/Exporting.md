---
layout: post
title: Exporting
description: exporting
platform: ejmvc
control: Chart
documentation: ug
---

# Exporting

Essential Chart supports client-side exporting using canvg script. canvg is a SVG parser and renderer. It takes a URL to a SVG file or the text of an SVG file, parses it to canvas, and renders the canvas image. 

Code:



{% highlight html %}

<img src="../images/chart/export.png" onclick="onExport()" title="Export Chart" style="float: right" />

<div id="container"></div> 







@(Html.EJ().Chart("container").EnableCanvasRendering(true))



[JS]



function onExport() {

            var canvas = $("#container").ejChart("exportChart");

            var image = canvas.toDataURL("image/png")

                              .replace("image/png","image/octet-stream");

            var downloadLink = document.createElement("a");

            downloadLink.href = image;

            downloadLink.download = "Chart.png";

            document.body.appendChild(downloadLink);

            downloadLink.click();

            document.body.removeChild(downloadLink);

        }


{% endhighlight  %}


