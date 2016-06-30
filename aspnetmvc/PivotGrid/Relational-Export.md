---
layout: post
title: Exporting | PivotGrid | ASP.NET MVC | Syncfusion
description: exporting
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Exporting

The PivotGrid control can be exported to the following file formats.

* Excel
* Word
* PDF
* CSV

The PivotGrid control can be exported by invoking **“exportPivotGrid”** method, with an appropriate export option as parameter.

{% highlight CSHTML %}

//If you want to render PivotGrid in Client Mode.
    @Html.EJ().Pivot().PivotGrid("PivotGrid1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Add(); })) 
                  
//If you want to render PivotGrid in Server Mode.
  @Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("~/wcf/RelationalService.svc"))

  @Html.EJ().Button("Button1").ClientSideEvents(clientSideEvents => { clientSideEvents.Click("exportBtnClick"); }).Text("Export")
  <script type="text/javascript">
        function exportBtnClick(args) {
            var pGridObj = $('#PivotGrid1').data("ejPivotGrid");
            //If you render PivotGrid in Client Mode, set the export option like below.
            pGridObj.exportPivotGrid("ExcelExport","fileName");
            
            //If you render PivotGrid in Server Mode, set the export option like below.
            pGridObj.exportPivotGrid(ej.PivotGrid.ExportOptions.Excel);;
            }
   </script>
    
{% endhighlight %}

To achieve exporting in client mode, we need to add **"Syncfusion.EJ.Export"** dependency library into the application.

When PivotGrid is rendered in Client Mode, a method needs to be added in MVC controller file of the application and we need to import **"Syncfusion.EJ.Export"** namespace in the controller file. 

{% highlight c# %}

public void ExcelExport()
{
     PivotGridExcelExport pGrid = new PivotGridExcelExport();
     string args = System.Web.HttpContext.Current.Request.Form.GetValues(0)[0];
     string fileName = "Sample";
     pGrid.ExportToExcel(fileName, args, System.Web.HttpContext.Current.Response);
}
        
{% endhighlight %}

When PivotGrid is rendered in Server Mode, a service method needs to be added in WCF/WebAPI for server side operations.

For WebAPI controller, the below method needs to be added.

{% highlight c# %}

[System.Web.Http.ActionName("Export")]
[System.Web.Http.HttpPost]
public void Export()
{
    string args = HttpContext.Current.Request.Form.GetValues(0)[0];
    Dictionary<string, string> gridParams = serializer.Deserialize<Dictionary<string, string>>(args);
    htmlHelper.PopulateData(gridParams["currentReport"]);
    string fileName = "Sample";
    htmlHelper.ExportPivotGrid(ProductSales.GetSalesData(), args, fileName, HttpContext.Current.Response);
}

{% endhighlight %}

For WCF service, the below method needs to be added.

{% highlight c# %}

public void Export(System.IO.Stream stream)
{
    System.IO.StreamReader sReader = new System.IO.StreamReader(stream);
    string args = System.Web.HttpContext.Current.Server.UrlDecode(sReader.ReadToEnd()).Remove(0, 5);
    Dictionary<string, string> gridParams = serializer.Deserialize<Dictionary<string, string>>(args);
    htmlHelper.PopulateData(gridParams["currentReport"]);
    string fileName = "Sample";
    htmlHelper.ExportPivotGrid(ProductSales.GetSalesData(), args, fileName, System.Web.HttpContext.Current.Response);
}

{% endhighlight %}

##Excel Export

User can export contents of the PivotGrid to Excel document for future archival, references and analysis purposes.

###Client Mode

To achieve Excel export, method name **"ExcelExport"** and file name is sent as the parameter.

{% highlight js %}

   <script type="text/javascript">
       function exportBtnClick(args)
       {
          var pGridObj = $('#PivotGrid1').data("ejPivotGrid ");
          pGridObj.exportPivotGrid("ExcelExport","fileName");
       }
   </script>
    
{% endhighlight %}  

Following method need to be added in MVC controller file of the application.

{% highlight c# %}

public void ExcelExport()
{
     PivotGridExcelExport pGrid = new PivotGridExcelExport();
     string args = System.Web.HttpContext.Current.Request.Form.GetValues(0)[0];
     string fileName = "Sample";
     pGrid.ExportToExcel(fileName, args, System.Web.HttpContext.Current.Response);
}

{% endhighlight %}

###Server Mode

To achieve Excel export, we need to add the following dependency libraries into the application.

* Syncfusion.Compression.Base
* Syncfusion.XlsIO.Base

For Excel export, **“ej.PivotGrid.ExportOptions.Excel”** enumeration value is sent as the parameter.

{% highlight js %}

function exportBtnClick(args)
{
    var pGridObj = $('#PivotGrid1').data("ejPivotGrid");
    //Setting export option as Excel in the exportPivotGrid method for ServerMode
    pGridObj.exportPivotGrid(ej.PivotGrid.ExportOptions.Excel);
}

{% endhighlight %}  

![](Exporting_images/ExportPivotExcel.png)

##Word Export
User can export contents of the PivotGrid to Word document for future archival, references and analysis purposes.

###Client Mode

To achieve Word export, method name **"WordExport"** and file name is sent as the parameter.

{% highlight js %}

   <script type="text/javascript">
       function exportBtnClick(args)
       {
          var pGridObj = $('#PivotGrid1').data("ejPivotGrid ");
          pGridObj.exportPivotGrid("WordExport","fileName");
       }
   </script>
    
{% endhighlight %}  

Following method need to be added in MVC controller file of the application.

{% highlight c# %}

public void WordExport()
{
     PivotGridWordExport pGrid = new PivotGridWordExport();
     string args = System.Web.HttpContext.Current.Request.Form.GetValues(0)[0];
     string fileName = "Sample";
     pGrid.ExportToWord(fileName, args, System.Web.HttpContext.Current.Response);
}

{% endhighlight %}

###Server Mode

 To achieve Word export, we need to add the following dependency libraries into the application.

* Syncfusion.Compression.Base
* Syncfusion.DocIO.Base

For Word export, **“ej.PivotGrid.ExportOptions.Word”** enumeration value is sent as the parameter.

{% highlight js %}

function exportBtnClick(args)
{
    var pGridObj = $('#PivotGrid1').data("ejPivotGrid");
    //Setting export option as Word in the exportPivotGrid method
    pGridObj.exportPivotGrid(ej.PivotGrid.ExportOptions.Word);
}

{% endhighlight %}

![](Exporting_images/ExportPivotWord.png)

##PDF Export

User can export contents of the PivotGrid to PDF document for future archival, references and analysis purposes.

###Client Mode

To achieve Word export, method name **"PDFExport"** and file name is sent as the parameter.

{% highlight js %}

   <script type="text/javascript">
       function exportBtnClick(args)
       {
          var pGridObj = $('#PivotGrid1').data("ejPivotGrid ");
          pGridObj.exportPivotGrid("PDFExport","fileName");
       }
   </script>
    
{% endhighlight %}  

Following method need to be added in MVC controller file of the application.

{% highlight c# %}

public void PDFExport()
{
     PivotGridPDFExport pGrid = new PivotGridPDFExport();
     string args = System.Web.HttpContext.Current.Request.Form.GetValues(0)[0];
     string fileName = "Sample";
     pGrid.ExportToPDF(fileName, args, System.Web.HttpContext.Current.Response);
}        

{% endhighlight %}

###Server Mode

To achieve PDF export, we need to add the following dependency libraries into the application.

* Syncfusion.Compression.Base
* Syncfusion.Pdf.Base

For PDF export, **“ej.PivotGrid.ExportOptions.PDF”** enumeration value is sent as the parameter.

{% highlight js %}

function exportBtnClick(args)
{
    var pGridObj = $('#PivotGrid1').data("ejPivotGrid ");
    //Setting export option as PDF in the exportPivotGrid method
    pGridObj.exportPivotGrid(ej.PivotGrid.ExportOptions.PDF);
}

{% endhighlight %} 

![](Exporting_images/ExportPivotPDF.png)

##CSV Export

User can export contents of the PivotGrid to CSV document for future archival, references and analysis purposes.

###Client Mode

To achieve CSV export, method name **"CSVExport"** and file name is sent as the parameter.

{% highlight js %}

   <script type="text/javascript">
       function exportBtnClick(args)
       {
          var pGridObj = $('#PivotGrid1').data("ejPivotGrid ");
          pGridObj.exportPivotGrid("CSVExport","fileName");
       }
   </script>
    
{% endhighlight %}  

Following method need to be added in MVC controller file of the application.

{% highlight c# %}

public void CSVExport()
{
     PivotGridCSVExport pGrid = new PivotGridCSVExport();
     string args = System.Web.HttpContext.Current.Request.Form.GetValues(0)[0];
     string fileName = "Sample";
     pGrid.ExportToCSV(fileName, args, System.Web.HttpContext.Current.Response);
}        

{% endhighlight %}

###Server Mode

For CSV export, **“ej.PivotGrid.ExportOptions.CSV”** enumeration value is sent as the parameter.

{% highlight js %}

function exportBtnClick(args)
{
    var pGridObj = $('#PivotGrid1').data("ejPivotGrid ");
    //Setting export option as CSV in the exportPivotGrid method
    pGridObj.exportPivotGrid(ej.PivotGrid.ExportOptions.CSV);
}

{% endhighlight %} 

![](Exporting_images/ExportPivotCSV.png)


##Customize the export document name

###Client Mode

For customizing file name, we need to send file name as parameter to the **“exportPivotGrid”**  method along with method name.

{% highlight js %}

function exportBtnClick(args)
{
    var pGridObj = $('#PivotGrid1').data("ejPivotGrid ");
    pGridObj.exportPivotGrid("ExcelExport","fileName");
}

{% endhighlight %}

###Server Mode

For customizing name in WebAPI controller, below code snippet is used.

{% highlight c# %}

[System.Web.Http.ActionName("Export")]
[System.Web.Http.HttpPost]
public void Export()
{
    string args = HttpContext.Current.Request.Form.GetValues(0)[0];
    Dictionary<string, string> gridParams = serializer.Deserialize<Dictionary<string, string>>(args);
    htmlHelper.PopulateData(gridParams["currentReport"]);
    string fileName = " File name is customized here ";
    htmlHelper.ExportPivotGrid(ProductSales.GetSalesData(), args, fileName, HttpContext.Current.Response);
}

{% endhighlight %}

For customizing name in WCF Service, below code snippet is used.

{% highlight c# %}

public void Export(System.IO.Stream stream)
{
    System.IO.StreamReader sReader = new System.IO.StreamReader(stream);
    string args = System.Web.HttpContext.Current.Server.UrlDecode(sReader.ReadToEnd()).Remove(0, 5);
    Dictionary<string, string> gridParams = serializer.Deserialize<Dictionary<string, string>>(args);
    htmlHelper.PopulateData(gridParams["currentReport"]);
    string fileName = " File name is customized here ";
    htmlHelper.ExportPivotGrid(ProductSales.GetSalesData(), args, fileName, System.Web.HttpContext.Current.Response);
}

{% endhighlight %}

