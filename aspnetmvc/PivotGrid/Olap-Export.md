---
layout: post
title: Exporting | PivotGrid | ASP.NET MVC | Syncfusion
description: exporting
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Exporting

The following table lists the exported file format for both Client and Server Mode of OLAP datasource.

<table>
<tr>
<th>
Mode
</th>
<th>
File Formats
</th>
</tr>
<tr>
<td>
Client Mode
</td>
<td>
Excel
</td>
</tr>
<tr>
<td>
Server Mode
</td>
<td>
Excel, Word, PDF and CSV
</td>
</tr>
</table>

The PivotGrid control can be exported by invoking **"exportPivotGrid"** method, with an appropriate export option as parameter.

## Client Mode

For client side, OLAP datasource contents can be exported only to Excel. The document can be saved from the browser to the local disk drive for later use.

To achieve Excel export, we need to add the following dependency library into the application.

* Syncfusion.EJ.Export

{% highlight js %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("[Date].[Fiscal]").Add(); }).Columns(columns => { columns.FieldName("[Customer].[Customer Geography]").Add(); }).Values(values => { values.Measures(measures => { measures.FieldName("[Measures].[Internet Sales Amount]").Add(); }).Axis(AxisName.Column).Add(); })
.Data("http://bi.syncfusion.com/olap/msmdpump.dll").Catalog("Adventure Works DW 2008 SE").Cube("Adventure Works"))

@Html.EJ().Button("Button1").ClientSideEvents(clientSideEvents => { clientSideEvents.Click("btnExportClick"); }).Text("ExcelExport")


<script type="text/javascript">
    function btnExportClick(args) {
        var gridObj = $('#PivotGrid1').data("ejPivotGrid");
        gridObj.exportPivotGrid("ExcelExport");
    }
</script>

{% endhighlight %}


Add the below code in PivotGridController.cs which is inside Controller folder to perform exporting

{% highlight c# %}

public void ExcelExport() {
    PivotGridExport pGrid = new PivotGridExport();
    string args = System.Web.HttpContext.Current.Request.Form.GetValues(0)[0];
    string fileName = "Sample";
    pGrid.ExportToExcel(fileName, args, System.Web.HttpContext.Current.Response);
}

{% endhighlight %}


![](Exporting_images/OlapClientmode.png)


## Server Mode

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Layout(PivotGridLayout.Normal).Url(Url.Content("~/OLAPService"))
@Html.EJ().Button("Button1").ClientSideEvents(clientSideEvents => { clientSideEvents.Click("exportBtnClick"); }).Text("Export")
<button id="ExportBtn">Export</button>
<script type="text/javascript">
    function exportBtnClick(args) {
        var gridObj = $('#PivotGrid1').data("ejPivotGrid");
        //Provide an appropriate export option as parameter.
        gridObj.exportPivotGrid(ej.PivotGrid.ExportOptions.Excel);
    }
</script>
                                        

{% endhighlight %}

For WebAPI controller, the below method needs to be added to perform exporting.

{% highlight c# %}

[System.Web.Http.ActionName("Export")]
[System.Web.Http.HttpPost]
public void Export() {
    string args = HttpContext.Current.Request.Form.GetValues(0)[0];
    OlapDataManager DataManager = new OlapDataManager(connectionString);
    string fileName = "Sample";
    htmlHelper.ExportPivotGrid(DataManager, args, fileName, System.Web.HttpContext.Current.Response);
}

{% endhighlight %}

For WCF service, the below service method needs to be added to perform exporting.

{% highlight c# %}

public void Export(System.IO.Stream stream) {
    System.IO.StreamReader sReader = new System.IO.StreamReader(stream);
    string args = System.Web.HttpContext.Current.Server.UrlDecode(sReader.ReadToEnd()).Remove(0, 5);;
    OlapDataManager DataManager = new OlapDataManager(connectionString);
    string fileName = "Sample";
    htmlHelper.ExportPivotGrid(DataManager, args, fileName, System.Web.HttpContext.Current.Response);
}

{% endhighlight %}

### Excel Export

User can export contents of the PivotGrid to Excel document for future archival, references and analysis purposes. To achieve Excel export, we need to add the following dependency libraries into the application.

* Syncfusion.Compression.Base
* Syncfusion.XlsIO.Base

For Excel export, **"ej.PivotGrid.ExportOptions.Excel"** enumeration value is sent as the parameter.

{% highlight js %}

function exportBtnClick(args) {
    var gridObj = $('#PivotGrid1').data("ejPivotGrid");
    gridObj.exportPivotGrid(ej.PivotGrid.ExportOptions.Excel);
}

{% endhighlight %}  

![](Exporting_images/excelexport.png)

### CSV Export
User can export contents of the PivotGrid to CSV document for future archival, references and analysis purposes.

For CSV export, **"ej.PivotGrid.ExportOptions.CSV"** enumeration value is sent as the parameter.

{% highlight js %}

function exportBtnClick(args) {
    var gridObj = $('#PivotGrid1').data("ejPivotGrid");
    gridObj.exportPivotGrid(ej.PivotGrid.ExportOptions.CSV);
}

{% endhighlight %} 

![](Exporting_images/csvexport.png)

### Word Export
User can export contents of the PivotGrid to Word document for future archival, references and analysis purposes. To achieve Word export, we need to add the following dependency libraries into the application.

* Syncfusion.Compression.Base
* Syncfusion.DocIo.Base

For Word export, “ej.PivotGrid.ExportOptions.Word” enumeration value is sent as the parameter.  

{% highlight js %}

function exportBtnClick(args) {
    var gridObj = $('#PivotGrid1').data("ejPivotGrid");
    gridObj.exportPivotGrid(ej.PivotGrid.ExportOptions.Word);
}

{% endhighlight %} 

![](Exporting_images/wordexport1.png)

### PDF Export
User can export contents of the PivotGrid to PDF document for future archival, references and analysis purposes. To achieve PDF export, we need to add the following dependency libraries into the application.

* Syncfusion.Compression.Base
* Syncfusion.Pdf.Base

For PDF export, **"ej.PivotGrid.ExportOptions.PDF"** enumeration value is sent as the parameter. 

{% highlight js %}

function exportBtnClick(args) {
    var gridObj = $('#PivotGrid1').data("ejPivotGrid");
    gridObj.exportPivotGrid(ej.PivotGrid.ExportOptions.PDF);
}

{% endhighlight %} 

![](Exporting_images/pdfexport.png)


### Customize the export document name

The document name could be customized inside the method in WebAPI Controller. Following code sample illustrates the same.

{% highlight c# %}

[System.Web.Http.ActionName("Export")]
[System.Web.Http.HttpPost]
public void Export() {
    string args = HttpContext.Current.Request.Form.GetValues(0)[0];
    OlapDataManager DataManager = new OlapDataManager(connectionString);
    string fileName = " File name is customized here ";
    htmlHelper.ExportPivotGrid(DataManager, args, fileName, System.Web.HttpContext.Current.Response);
}

{% endhighlight %}

For customizing name in WCF Service, below code snippet is used.

{% highlight c# %}

public void Export(System.IO.Stream stream) {
    System.IO.StreamReader sReader = new System.IO.StreamReader(stream);
    string args = System.Web.HttpContext.Current.Server.UrlDecode(sReader.ReadToEnd()).Remove(0, 5);;
    OlapDataManager DataManager = new OlapDataManager(connectionString);
    string fileName = " File name is customized here ";
    htmlHelper.ExportPivotGrid(DataManager, args, fileName, System.Web.HttpContext.Current.Response);
}

{% endhighlight %}


