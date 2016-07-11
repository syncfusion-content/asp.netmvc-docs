---
layout: post
title: Exporting a Report as Various Documents formats
description: How To save a report as PDF, Word, Excel, PPT and HTML documents?
platform: ejmvc
control: ReportWriter
documentation: ug
---

# Exporting Reports

Essential ReportWriter provides support for Exporting a report as a PDF, Word, Excel, PPT and HTML documents with the help of the class ReportWriter. The report elements such as Tablix, matrices, charts, gauges, shapes, and text boxes are supported in this feature. 

### Exporting Report as PDF

The report used in ReportWriter can be exported as PDF document using the following code.

~~~html

ReportWriter reportWriter = new ReportWriter(reportpath, dataSources);
reportWriter.Save("Sample.pdf", WriterFormat.PDF);

~~~

![](MVC_Images/RDLExportPdf.png) 

### Exporting Report as Word

The report used in ReportWriter can be exported as Word document using the following code.

~~~html

ReportWriter reportWriter = new ReportWriter(reportpath, dataSources);
reportWriter.Save("Sample.doc", WriterFormat.Word);

~~~

![](MVC_Images/RDLExportWord.png) 

### Exporting Report as Excel

The report used in ReportWriter can be exported as Excel document using the following code.

~~~html

ReportWriter reportWriter = new ReportWriter(reportpath, dataSources);
reportWriter.Save("Sample.xls", WriterFormat.Excel);

~~~

![](MVC_Images/RDLExportExcel.png) 

### Exporting Report as HTML

The report used in ReportWriter can be exported as HTML document using the following code.

~~~html

ReportWriter reportWriter = new ReportWriter(reportpath, dataSources);
reportWriter.Save("Sample.html", WriterFormat.HTML);

~~~

![](MVC_Images/RDLExportHtml.png) 

### Exporting Report as PPT

The report used in ReportWriter can be exported as PPT document using the following code.

~~~html

ReportWriter reportWriter = new ReportWriter(reportpath, dataSources);
reportWriter.Save("Sample.ppt", WriterFormat.PPT);

~~~

![](MVC_Images/RDLExportPPT.png)