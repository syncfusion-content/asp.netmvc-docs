---
layout: post
title: Exporting
description: exporting
platform: ejmvc
control: OLAP Client
documentation: ug
---

## Exporting

The content in the OLAP Client control can be exported to Excel, Word and PDF documents.

{ ![](Exporting_images/Exporting_img1.png) | markdownify }
{:.image }


Exporting feature provides you a mode option that allows you to export either OlapChart or PivotGrid or both. The following code example explains the same. 

@Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/wcf/OlapClientService.svc")).ClientExportMode(ClientExportMode.ChartAndGrid)



The ClientExportMode propertytakes any one of the following value:

1. ChartAndGrid – Exports both the OlapChart and the PivotGrid controls. This is the default mode.
2. ChartOnly – Exports the OlapChart control alone.
3. GridOnly – Exports the PivotGrid control alone.

The following code example of the service method needs to be added in-order to perform exporting in the OlapClient.

public void Export(Stream stream)

{

    System.IO.StreamReader sReader = new System.IO.StreamReader(stream);

    string args = System.Web.HttpContext.Current.Server.UrlDecode(sReader.ReadToEnd());

    OlapDataManager DataManager = new OlapDataManager(connectionString);

    string fileName = "OlapClient";

    olapClientHelper.ExportOlapClient(DataManager, args, fileName,

    System.Web.HttpContext.Current.Response);

}



{ ![C:/Users/Narendhran Muthuvel/Desktop/Exported Screenshots/OlapClientExcelMVC.png](Exporting_images/Exporting_img2.png) | markdownify }
{:.image }


{ ![C:/Users/Narendhran Muthuvel/Desktop/Exported Screenshots/OlapClientWordMVC.png](Exporting_images/Exporting_img3.png) | markdownify }
{:.image }


{ ![C:/Users/Narendhran Muthuvel/Desktop/Exported Screenshots/OlapClientPdfMVC.png](Exporting_images/Exporting_img4.png) | markdownify }
{:.image }






