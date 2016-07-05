## Export Types

The ReportWriter provides support for exporting report as PDF, Word, Excel and HTML documents with the help of the ReportWriter class.

### Exporting Report as PDF

The report used in ReportWriter can be exported as a PDF document using the following code.

~~~html

ReportWriter reportWriter = new ReportWriter(reportpath, dataSources);
reportWriter.Save("Sample.pdf", WriterFormat.PDF);

~~~

![](MVC_Images/RDLExportPdf.png) 

### Exporting Report as Word

The report used in ReportWriter can be exported as a Word document using the following code.

~~~html

ReportWriter reportWriter = new ReportWriter(reportpath, dataSources);
reportWriter.Save("Sample.doc", WriterFormat.Word);

~~~

![](MVC_Images/RDLExportWord.png) 

### Exporting Report as Excel

The report used in ReportWriter can be exported as an Excel document using the following code.

~~~html

ReportWriter reportWriter = new ReportWriter(reportpath, dataSources);
reportWriter.Save("Sample.xls", WriterFormat.Excel);

~~~

![](MVC_Images/RDLExportExcel.png) 

### Exporting Report as HTML

The report used in ReportWriter can be exported as an HTML document using the following code.

~~~html

ReportWriter reportWriter = new ReportWriter(reportpath, dataSources);
reportWriter.Save("Sample.html", WriterFormat.HTML);

~~~

![](MVC_Images/RDLExportHtml.png) 

### Exporting Report as PPT

The report used in ReportWriter can be exported as an HTML document using the following code.

~~~html

ReportWriter reportWriter = new ReportWriter(reportpath, dataSources);
reportWriter.Save("Sample.ppt", WriterFormat.PPT);

~~~

![](MVC_Images/RDLExportPPT.png) 