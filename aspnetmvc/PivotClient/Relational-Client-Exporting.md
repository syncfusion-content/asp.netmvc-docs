---
layout: post
title: Exporting | PivotClient | ASP.NET MVC | Syncfusion
description: exporting
platform: ejmvc
control: PivotClient
documentation: ug
---

# Exporting

Chart and Grid in the PivotClient widget can be exported to Excel, Word and PDF documents by clicking the respective toolbar icons.

![Exporting icons in ASP NET MVC pivot client control](Exporting_images/exporticon.png)

Exporting feature provides an option that allows you to export either PivotChart or PivotGrid or both with the use of the property `ClientExportMode`.

The property `ClientExportMode` takes any one of the following value:

* **ChartAndGrid** – Exports both PivotChart and PivotGrid controls. This is the default mode.
* **ChartOnly** – Exports PivotChart control alone.
* **GridOnly** – Exports PivotGrid control alone.

## JOSN Export

I> By default, exporting is done with the use of JSON Records maintained in client-side for both client and server modes.

In order to make use of exporting with client side JSON data. The control can be exported by invoking “BeforeExport” event, with an appropriate export option as parameter.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad").BeforeExport("Export")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).ClientExportMode(ClientExportMode.ChartAndGrid)

   <script type="text/javascript">
        function Export(args) {
            args.url = "ExportPivotClient";
        }
   </script>

{% endhighlight %}

When PivotClient is exported with JSON mode, a method needs to be added in MVC controller file of the application.

{% highlight C# %}

    public void ExportPivotClient()
    {
       JavaScriptSerializer serializer = new JavaScriptSerializer() { MaxJsonLength = Int32.MaxValue };
       PivotClientExport pivotClient = new PivotClientExport();
       string args = System.Web.HttpContext.Current.Request.Form.GetValues(0)[0];
       pivotClient.ExportPivotClient(string.Empty, args, System.Web.HttpContext.Current.Response);
     }

{% endhighlight %}

### Customize the export document name

The document name to be exported could be customized. Following code sample illustrates the same.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad").BeforeExport("Export")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).ClientExportMode(ClientExportMode.ChartAndGrid)

    <script type="text/javascript">
            function Export(args) {
                args.url = "ExportPivotClient";
                args.fileName=" File name is customized here ";
            }
    </script>

{% endhighlight %}

## PivotEngine Export

I> This feature is applicable only at server mode operation.

In order to perform exporting with the use of PivotEngine available in server-side, the 'exportMode' property obtained in the “BeforeExport” event is set to "ej.PivotClient.ExportMode.PivotEngine" as shown below.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").Url(Url.Content("/RelationalClient")).ClientExportMode(ClientExportMode.ChartAndGrid).ClientSideEvents(oEve => { oEve.BeforeExport("Export"); })
   <script type="text/javascript">
        function Export(args) {
          args.exportMode = ej.PivotClient.ExportMode.PivotEngine;
        }
   </script>

{% endhighlight %}

For WebAPI controller, the below method needs to be added to perform exporting with PivotEngine.


{% highlight C# %}

        [System.Web.Http.ActionName("Export")]
        [System.Web.Http.HttpPost]
        public void Export()
        {
            string args = HttpContext.Current.Request.Form.GetValues(0)[0];
            Dictionary<string, string> gridParams = serializer.Deserialize<Dictionary<string, string>>(args);
            pivotClient.PopulateData(gridParams["currentReport"]);
            string fileName = "Sample";
            pivotClient.ExportPivotClient(ProductSales.GetSalesData(), args, fileName, System.Web.HttpContext.Current.Response);
        }

{% endhighlight %}

For WCF service, the below service method needs to be added to perform exporting with PivotEngine.

{% highlight C# %}

        public void Export(System.IO.Stream stream)
        {
            System.IO.StreamReader sReader = new System.IO.StreamReader(stream);
            string args = System.Web.HttpContext.Current.Server.UrlDecode(sReader.ReadToEnd()).Remove(0, 5);
            Dictionary<string, string> gridParams = serializer.Deserialize<Dictionary<string, string>>(args);
            pivotClient.PopulateData(gridParams["currentReport"]);
            string fileName = "Sample";
            pivotClient.ExportPivotClient(ProductSales.GetSalesData(), args, fileName, System.Web.HttpContext.Current.Response);
        }


{% endhighlight %}

### File format selection

I> This option is applicable only for PivotClient excel export.

You can set the option for exporting excel sheet as either *.xls* or *.xlsx* format before export the document by using 'fileFormat' property obtained in the “BeforeExport” event.

N> By default excel document can be exported as ".xls" format using PivotEngine export.

{% highlight cshtml %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(oEve => { oEve.BeforeExport("Exporting"); })
   <script type="text/javascript">
        function Exporting(args) {
            args.exportMode = ej.PivotClient.ExportMode.PivotEngine;
            args.fileFormat = ".xlsx"; //you can set the excel sheet format here
        }
   </script>

{% endhighlight %}

### Customize the export document name

The document name could be customized inside the method in WebAPI Controller. Following code sample illustrates the same.

{% highlight c# %}

        [System.Web.Http.ActionName("Export")]
        [System.Web.Http.HttpPost]
        public void Export()
        {
            string args = HttpContext.Current.Request.Form.GetValues(0)[0];
            Dictionary<string, string> gridParams = serializer.Deserialize<Dictionary<string, string>>(args);
            pivotClient.PopulateData(gridParams["currentReport"]);
            string fileName = " File name is customized here ";
            pivotClient.ExportPivotClient(ProductSales.GetSalesData(), args, fileName, System.Web.HttpContext.Current.Response);
        }

{% endhighlight %}

For customizing name in WCF Service, below code snippet is used.

{% highlight c# %}

        public void Export(System.IO.Stream stream)
        {
            System.IO.StreamReader sReader = new System.IO.StreamReader(stream);
            string args = System.Web.HttpContext.Current.Server.UrlDecode(sReader.ReadToEnd()).Remove(0, 5);
            Dictionary<string, string> gridParams = serializer.Deserialize<Dictionary<string, string>>(args);
            pivotClient.PopulateData(gridParams["currentReport"]);
            string fileName = " File name is customized here ";
            pivotClient.ExportPivotClient(ProductSales.GetSalesData(), args, fileName, System.Web.HttpContext.Current.Response);
        }


{% endhighlight %}

## PivotChart - Exporting Format

I> This option is applicable only for PivotChart in PivotClient specifically when exported to Excel document.

You can set an option to export PivotChart to an Excel document, either as image or PivotChart format itself by setting the boolean property `exportChartAsImage`, inside the `BeforeExport` event.

N> By default PivotChart will be exported as image format to Excel document.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotClient("PivotClient1").Url(Url.Content("/RelationalClient")).ClientExportMode(ClientExportMode.ChartOnly).ClientSideEvents(oEve => { oEve.BeforeExport("Export"); })
<script type="text/javascript">
        function Export(args) {
           args.exportChartAsImage = false; //you can set the chart format here
        }
</script>

{% endhighlight %}

The below screenshot shows the control exported to Excel document showing its own format (Pivoting Chart).

![Exporting format of ASP NET MVC pivot client control](Exporting_images/Export_ExcelChartClient.png)

## Exporting Customization

You can add title and description to the exporting document by using the title and description properties respectively obtained in the `BeforeExport` event. Similarly, you can enable or disable styling on the exported document by using the `exportWithStyle` property.

{% highlight cshtml %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(oEve => { oEve.BeforeExport("Exporting"); })
   <script type="text/javascript">
        function Exporting(args) {
            //ClientMode export
            args.url = "ExportPivotClient";
            //PivotEngine Export
            args.exportMode = ej.PivotClient.ExportMode.PivotEngine;

            args.title = "PivotClient";
            args.description = "Visualizes both OLAP and Relational datasource in tabular and graphical formats";
			args.exportWithStyle = true;   // by default it sets as true. It improves performance on exporting huge data when it sets as false.
        }
   </script>

{% endhighlight %}

You can also edit the exporting document with the use of a server side event for required exporting option.

{% highlight c# %}

//...
using Syncfusion.EJ.Export;
using Syncfusion.Compression.Base;
using Syncfusion.XlsIO;
using Syncfusion.DocIO.Base;
using Syncfusion.Pdf.Base;

//Following methods needs to be added in MVC controller file of the application for JSON Export.
public void ExportPivotClient()
{
    JavaScriptSerializer serializer = new JavaScriptSerializer() { MaxJsonLength = Int32.MaxValue };
    PivotClientExport pivotClient = new PivotClientExport();
    string args = System.Web.HttpContext.Current.Request.Form.GetValues(0)[0];
    pivotClient.ExcelExport += pivotClient_ExcelExport;
    pivotClient.WordExport += pivotClient_WordExport;
    pivotClient.AddPDFHeaderFooter += pivotClient_AddPDFHeaderFooter;
    pivotClient.PDFExport += pivotClient_PDFExport;
    pivotClient.ExportPivotClient(string.Empty, args, System.Web.HttpContext.Current.Response);

}

void pivotClient_PDFExport(object sender, Syncfusion.Pdf.PdfDocument pdfDoc)
{
    //You can customize exporting document here.
}

void pivotClient_AddPDFHeaderFooter(object sender, Syncfusion.Pdf.PdfDocument pdfDoc)
{
    //You can add header/footer information to the PDF document.
}

void pivotClient_WordExport(object sender, Syncfusion.DocIO.DLS.WordDocument document)
{
    //You can customize exporting document here.
}

void pivotClient_ExcelExport(object sender, Syncfusion.XlsIO.IWorkbook workBook)
{
    //You can customize exporting document here.
}

//Following service method needs to be added in WebAPI controller for PivotEngine Export.

[System.Web.Http.ActionName("Export")]
[System.Web.Http.HttpPost]
public void Export()
{
    string args = HttpContext.Current.Request.Form.GetValues(0)[0];
    Dictionary<string, string> gridParams = serializer.Deserialize<Dictionary<string, string>>(args);
    pivotClient.PopulateData(gridParams["currentReport"]);
    pivotClient.ExcelExport += pivotClient_ExcelExport;
    pivotClient.WordExport += pivotClient_WordExport;
    pivotClient.AddPDFHeaderFooter += pivotClient_AddPDFHeaderFooter;
    pivotClient.PDFExport += pivotClient_PDFExport;
    string fileName = "Sample";
    pivotClient.ExportPivotClient(ProductSales.GetSalesData(), args, fileName, System.Web.HttpContext.Current.Response);
}

void pivotClient_PDFExport(object sender, Syncfusion.Pdf.PdfDocument pdfDoc)
{
    //You can customize exporting document here.
}

void pivotClient_AddPDFHeaderFooter(object sender, Syncfusion.Pdf.PdfDocument pdfDoc)
{
    //You can add header/footer information to the PDF document.
}

void pivotClient_WordExport(object sender, Syncfusion.DocIO.DLS.WordDocument document)
{
    //You can customize exporting document here.
}

void pivotClient_ExcelExport(object sender, Syncfusion.XlsIO.IWorkbook workBook)
{
    //You can customize exporting document here.
}

{% endhighlight %}

The below screenshot shows the PivotGrid and PivotChart controls exported to Excel document.

![Excel exporting in ASP NET MVC pivot client control](Exporting_images/relational-excel-export.png)

The below screenshot shows the PivotGrid and PivotChart controls exported to Word document.

![Word exporting in ASP NET MVC pivot client control](Exporting_images/relational-word-export.png)

The below screenshot shows the PivotGrid and PivotChart controls exported to PDF document.

![PDF exporting in ASP NET MVC pivot client control](Exporting_images/relational-pdf-export.png)