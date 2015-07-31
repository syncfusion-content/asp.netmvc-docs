---
layout: post
title: Exporting
description: exporting
platform: ejmvc
control: Circular Gauge
documentation: ug
---

## Exporting

* Circular Gauge has an exporting feature that converts Gauge control into image format and then export in client side. The method API exportImage is used to export the Circular Gauge. 
* It has two arguments such as file name and file format to specify the file name and file formats. For exporting refer the following code example.



[View]

@(Html.EJ().CircularGauge("circulargauge"))

<input type="submit" value="Export Image" id="btnExportImage" />



<script type="text/javascript">

        $(function () {

            $("#btnExportImage").ejButton({ width: "100px", click: "buttonclickevent", });

        });

        function buttonclickevent() {

            var FileName = $("#txtFileName").val();

            var FileFormat = $("#ddlFileType").val();

            $("#circulargauge").ejCircularGauge("exportImage", FileName, FileFormat);

        }



    </script>


Execute the above code to render the following output.

{{ '![](Exporting_images/Exporting_img1.png)' | markdownify }}
{:.image }




