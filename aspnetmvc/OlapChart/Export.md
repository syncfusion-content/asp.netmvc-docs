---
layout: post
title: Export | OLAPChart | ASP.NET MVC | Syncfusion
description: export
platform: ejmvc
control: OLAPChart
documentation: ug
---

#Exporting

The OlapChart control can be exported to the following file formats.

* Excel
* Word
* PDF
* CSV
* Image

The OlapChart control can be exported by invoking **“exportOlapChart”** method, with an appropriate export option as parameter.

{% highlight CSHTML %}

@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("100%"))
@Html.EJ().Button("Button1").ClientSideEvents(clientSideEvents => { clientSideEvents.Click("ExportBtnClick"); }).Text("Export")
<script type="text/javascript">
     function ExportBtnClick(args) {
         var chartObj = $('#OlapChart1').data("ejOlapChart");
         chartObj.exportOlapChart(ej.olap.OlapChart.ExportOptions.Excel);
     }
</script>                                       

{% endhighlight %}

In-order to perform exporting in OlapChart control, we need to add the following service method as well (either in WCF or WebAPI).In-order to perform exporting in OlapChart control, we need to add the following service method as well (either in WCF or WebAPI).

{% highlight c# %}

public void Export(System.IO.Stream stream)
{
   System.IO.StreamReader sReader = new System.IO.StreamReader(stream);
   string args =   System.Web.HttpContext.Current.Server.
   UrlDecode(sReader.ReadToEnd()).Remove(0, 5);
   OlapDataManager DataManager = new OlapDataManager(connectionString);
   string fileName = "Sample";
   htmlHelper.ExportOlapChart(DataManager, args, fileName,
   System.Web.HttpContext.Current.Response);
}

{% endhighlight %}

##Excel Export
User can export contents of the OlapChart to Excel document for future archival, references and analysis purposes. To achieve Excel export, we need to add the following dependency libraries into the application.

* Syncfusion.Compression.Base
* Syncfusion.XlsIO.Base

For Excel export, **“ej.olap.OlapChart.ExportOptions.Excel”** enumeration value is sent as the parameter.

{% highlight js %}

function exportBtnClick(args) {
   var chartObj = $('#OlapChart1').data("ejOlapChart");
   //set export option as Excel in the exportOlapChart method
   chartObj.exportOlapChart(ej.olap.OlapChart.ExportOptions.Excel);
}

{% endhighlight %}  

![](Export_images/Export_img1.png)

##Word Export
User can export contents of the OlapChart to Word document for future archival, references and analysis purposes. To achieve Word export, we need to add the following dependency libraries into the application.

* Syncfusion.Compression.Base
* Syncfusion.DocIo.Base

For Word export, **“ej.olap.OlapChart.ExportOptions.Word”** enumeration value is sent as the parameter.

{% highlight js %}

function exportBtnClick(args) {
   var chartObj = $('#OlapChart1').data("ejOlapChart");
   //set export option as Word in the exportOlapChart method
   chartObj.exportOlapChart(ej.olap.OlapChart.ExportOptions.Word);
}

{% endhighlight %}

![](Export_images/Export_img2.png)

##CSV Export
User can export contents of the OlapChart to CSV document for future archival, references and analysis purposes.

For CSV export, **“ej.olap.OlapChart.ExportOptions.CSV”** enumeration value is sent as the parameter.

{% highlight js %}

function exportBtnClick(args) {
   var chartObj = $('#OlapChart1').data("ejOlapChart");
   //set export option as CSV in the exportOlapChart method
   chartObj.exportOlapChart(ej.olap.OlapChart.ExportOptions.CSV);
}

{% endhighlight %}

##PDF Export
User can export contents of the OlapChart to PDF document for future archival, references and analysis purposes. To achieve PDF export, we need to add the following dependency libraries into the application.

Syncfusion.Compression.Base
Syncfusion.Pdf.Base

For PDF export, **“ej.olap.OlapChart.ExportOptions.PDF”** enumeration value is sent as the parameter.

{% highlight js %}

function exportBtnClick(args) {
   var chartObj = $('#OlapChart1').data("ejOlapChart");
   //set export option as PDF in the exportOlapChart method
   chartObj.exportOlapChart(ej.olap.OlapChart.ExportOptions.PDF);
}

{% endhighlight %} 

![](Export_images/Export_img3.png)

##Image Export
User can export contents of the OlapChart to image format for future archival, references and analysis purposes. We can export OlapChart to the following image formats.

PNG
EMF
JPG
GIF
BMP

For EMF export, “ej.olap.OlapChart.ExportOptions.EMF” enumeration value is sent as the parameter.

{% highlight js %}

function exportBtnClick(args) {
   var chartObj = $('#OlapChart1').data("ejOlapChart");
   //set export option as EMF in the exportOlapChart method
   chartObj.exportOlapChart(ej.olap.OlapChart.ExportOptions.EMF);
}


{% endhighlight %}  

![](Export_images/Export_img4.png)

##Customize the export document name
The document name could be customized inside the service method. Following code sample illustrates the same.

{% highlight c# %}

public void Export(System.IO.Stream stream)
{
   System.IO.StreamReader sReader = new System.IO.StreamReader(stream);
   string args =   System.Web.HttpContext.Current.Server.
   UrlDecode(sReader.ReadToEnd()).Remove(0, 5);
   OlapDataManager DataManager = new OlapDataManager(connectionString);
   string fileName = "Customize the file name here";
   htmlHelper.ExportOlapChart(DataManager, args, fileName,
   System.Web.HttpContext.Current.Response);
}

{% endhighlight %}