---
layout: post
title: ReportWriter | ReportWriter | ASP.NET MVC | Syncfusion
description: export rdl
platform: ejmvc
control: ReportWriter
documentation: ug
---

## To Export RDL Reports

The ReportWriter has options to save the RDL reports. The following code example helps you to generate the RDL report using ReportWriter.

Specify the `ReportPath`, `ReportProcessingMode` and `WriterFormat` properties for ReportWriter to generate report.

~~~csharp
   
string reportPath = @"..\ReportTemplate\GroupingAgg.rdl";
ReportWriter reportWriter = new ReportWriter(reportPath);
reportWriter.ReportProcessingMode = ProcessingMode.Remote;
reportWriter.Save("GroupingAgg.xls", WriterFormat.Excel);

~~~