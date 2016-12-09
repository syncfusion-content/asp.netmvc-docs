---
layout: post
title: Open and Save with Spreadsheet widget for Syncfusion Essential ASP.NET MVC
description: How to perform Open and Save and configure its functionalities like server mapper, import URL etc.
platform: ejmvc
control: Spreadsheet
documentation: ug
--- 

# Open and Save
The native data format for Spreadsheet is JSON. You can load and store JSON data with Spreadsheet. In Spreadsheet we have [`saveAsJSON`](http://help.syncfusion.com/api/js/ejspreadsheet#methods:saveasjson "saveAsJSON") and [`loadFromJSON`](https://help.syncfusion.com/api/js/ejspreadsheet#methods:loadfromjson "loadFromJSON") method which is used to save Spreadsheet as JSON and same JSON used to render Spreadsheet.

{% highlight javascript %}

function saveAsJSON() {
    var xlObj = $("#Spreadsheet").data("ejSpreadsheet");
    window.xlData = xlObj.saveAsJSON();
}

function loadFromJSON() {
    var xlObj = $("#Spreadsheet").data("ejSpreadsheet");
    xlObj.loadFromJSON(window.xlData);
}   
    
{% endhighlight %}

When you open excel file, it need to be read and converted to client side Spreadsheet model. The converted client side Spreadsheet model is sent as JSON which is used to render Spreadsheet. Similarly, when you save the Spreadsheet, the client Spreadsheet model is sent to the server as JSON for processing and saved. `Server configuration` is used for this process. 

## Open 
The Spreadsheet can open excel documents as like excel application with its data, style, format. To enable open option in Spreadsheet set `AllowImport` option to `true`. Since Spreadsheet uses a server side helper to open document, set `ImportMapper` in `ImportSettings` to map server action.

{% tabs %}
{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .AllowImport(true)
    .ImportSettings(import =>
    {
        import.ImportMapper("Import");
    })
)
    
{% endhighlight %}
{% highlight c# %}

namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            return View();
        }

        [AcceptVerbs(HttpVerbs.Post)]
        public ActionResult Import(ImportRequest importRequest)
        {
            return importRequest.SpreadsheetActions();
        }
    }
}
    
{% endhighlight %}
{% endtabs %}

Following file types can be opened in Spreadsheet

* XLS
* XLSX
* CSV

[`Click`](http://mvc.syncfusion.com/demos/web/spreadsheet/importexport "Click") here to view online demo sample. You can open excel documents in following ways

1. Initial settings
2. Methods
3. User Interface

### Initial settings
The Spreadsheet can load excel documents initially. The document can be specified either from client side or in server side. To load excel documents initially from client side, set `ImportUrl` in `ImportSettings`. The code snippets for document initial load on client side are as follows,

{% tabs %}
{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .ImportSettings(import =>
    {
        import.ImportMapper("Import");
        import.ImportUrl("http://mvc.syncfusion.com/Spreadsheet/LargeData.xlsx");
    })
)
    
{% endhighlight %}
{% highlight c# %}

namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            return View();
        }

        [AcceptVerbs(HttpVerbs.Post)]
        public ActionResult Import(ImportRequest importRequest)
        {
            return importRequest.SpreadsheetActions();
        }
    }
}
    
{% endhighlight %}
{% endtabs %}

To load excel documents initially from server side, set `ImportOnLoad`as `true` and assign document stream or URL in the server. The code snippets for document initial load from server side are as follows,

{% tabs %}{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .ImportSettings(import =>
    {
        import.ImportOnLoad(true);
        import.ImportMapper("Import");
    })
)

{% endhighlight %}
{% highlight c# %}

namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            return View();
        }

        [AcceptVerbs(HttpVerbs.Post)]
        public ActionResult Import(ImportRequest importRequest)
        {
            importRequest.Url = "http://mvc.syncfusion.com/Spreadsheet/LargeData.xlsx";
            return importRequest.SpreadsheetActions();
        }
    }
}
    
{% endhighlight %}
{% endtabs %}

![](Open-and-Save_images/Open-and-Save_img1.png)

### Methods
To open an excel document, [`import`](http://help.syncfusion.com/api/js/ejspreadsheet#methods:import "import") method should be called with import options as a parameter. The Spreadsheet can open excel document as a stream or file URL.
 
#### Stream
Spreadsheet can open excel document as a stream and the document stream was either from the client side or it can be specified in server side. The code snippets to open excel document as a stream from client side are as follows,

{% highlight javascript %}

function fileOpen(args) {
    var xlObj = $("#Spreadsheet").data("ejSpreadsheet"),
    stream = args.files[0]; // file stream from ejUploadbox
    xlObj["import"]({ file: stream });
}
    
{% endhighlight %}

The Code snippets to specify excel document as stream in server side are as follows,

{% highlight c# %}

namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            var DataSource = new OrderItemsDataContext().GetAllItemDetails.ToList();
            ViewBag.Datasource = DataSource;
            return View();
        }
 
        [AcceptVerbs(HttpVerbs.Post)]
        public ActionResult Import(ImportRequest importRequest)
        {
            importRequest.FileStream = getFileStream(); // assign file stream
            return importRequest.SpreadsheetActions();
        }
 
    }
}

{% endhighlight %}

#### File URL
Spreadsheet can open excel document from specified URL. The URL can be specified either from client side or in server side. The code snippets to open excel document as URL from client side are as follows,

{% highlight javascript %}

function fileOpen() {
    var xlObj = $("#Spreadsheet").data("ejSpreadsheet");
    xlObj["import"]({Url: "http://mvc.syncfusion.com/Spreadsheet/LargeData.xlsx"});
}
    
{% endhighlight %}

The Code snippets to specify excel document as URL in server side are as follows,

{% highlight c# %}

namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            return View();
        }

        [AcceptVerbs(HttpVerbs.Post)]
        public ActionResult Import(ImportRequest importRequest)
        {
            importRequest.Url = "http://mvc.syncfusion.com/Spreadsheet/LargeData.xlsx";
            return importRequest.SpreadsheetActions();
        }

    }
}
    
{% endhighlight %}

### User Interface
You can dynamically open excel document by clicking the file menu in ribbon and choose Open to upload excel file. 

## Save
The Spreadsheet can save its data, style, format into an excel file. To enable save option in Spreadsheet set `AllowExporting` option in `ExportSettings` as `true`. Since Spreadsheet uses server side helper to save documents set `ExcelUrl` in `ExportSettings` option.

{% tabs %}
{% highlight cshtml %}

@(Html.EJ().Spreadsheet<ItemDetail>("Spreadsheet")
    .ExportSettings(export =>
    {
        export.AllowExporting(true);
        export.ExcelUrl("ExportToExcel");
        export.CsvUrl("ExportToCSV");
        export.PdfUrl("ExportToPDF");
    })
)
    
{% endhighlight %}
{% highlight c# %}

namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            List<ItemDetail> lItems = new List<ItemDetail>();
            lItems.Add(new ItemDetail() { ItemName = "Casual Shoes", Date = new DateTime(2014, 02, 14), Time = new DateTime(2014, 02, 14, 11, 34, 32), Quantity = 10, Price = 20, Amount = 200, Discount = 1, Profit = 10 });
            lItems.Add(new ItemDetail() { ItemName = "Sports Shoes", Date = new DateTime(2014, 06, 11), Time = new DateTime(2014, 06, 11, 05, 56, 32), Quantity = 20, Price = 30, Amount = 600, Discount = 5, Profit = 50 });
            lItems.Add(new ItemDetail() { ItemName = "Formal Shoes", Date = new DateTime(2014, 07, 27), Time = new DateTime(2014, 07, 27, 03, 32, 44), Quantity = 20, Price = 15, Amount = 300, Discount = 7, Profit = 27 });
            lItems.Add(new ItemDetail() { ItemName = "Sandals & Floaters", Date = new DateTime(2014, 11, 21), Time = new DateTime(2014, 11, 21, 06, 23, 54), Quantity = 15, Price = 20, Amount = 300, Discount = 11, Profit = 67 });
            lItems.Add(new ItemDetail() { ItemName = "Flip- Flops & Slippers", Date = new DateTime(2014, 06, 23), Time = new DateTime(2014, 06, 23, 12, 43, 59), Quantity = 30, Price = 10, Amount = 300, Discount = 10, Profit = 70 });
            ViewBag.Datasource = lItems;
            return View();
        }
        
        [AcceptVerbs(HttpVerbs.Post)]
        public void ExportToExcel(string sheetModel, string sheetData, string password)
        {
            if (String.IsNullOrEmpty(password))
                Spreadsheet.Save(sheetModel, sheetData, "sample", ExportFormat.XLSX, ExcelVersion.Excel2013);
            else
                Spreadsheet.Save(sheetModel, sheetData, "sample", ExportFormat.XLSX, ExcelVersion.Excel2013, password);
        }

        [AcceptVerbs(HttpVerbs.Post)]
        public void ExportToCsv(string sheetModel, string sheetData)
        {
            Spreadsheet.Save(sheetModel, sheetData, "sample", ExportFormat.CSV);
        }

        [AcceptVerbs(HttpVerbs.Post)]
        public void ExportToPdf(string sheetModel, string sheetData)
        {
            Spreadsheet.Save(sheetModel, sheetData, "sample", ExportFormat.PDF);
        }

    }
}
    
{% endhighlight %}
{% endtabs %}


N> To export as Stream skip file name parameter in Save method. For more details refer below code snippets,
N> Stream stream = Spreadsheet.Save(sheetModel, sheetData, ExportFormat.XLSX, ExcelVersion.Excel2013);

You can save Spreadsheet contents with following file types,

* XLS
* XLSX
* CSV
* PDF

[`Click`](http://mvc.syncfusion.com/demos/web/spreadsheet/importexport "Click") here to view online demo sample. You can save excel documents in following ways

1. Methods
2. User Interface

### Methods
To save Spreadsheet document as excel file, [`export`](http://help.syncfusion.com/api/js/ejspreadsheet#methods:xlexport-export "export") method should be called with file type as parameter. The code snippets to save Spreadsheet document are as follows,

{% highlight javascript %}

function saveAsFile() {
    var xlObj = $("#spreadsheet").data("ejSpreadsheet");
    xlObj.XLExport["export"](ej.Spreadsheet.exportType.Excel);
}
    
{% endhighlight %}

### User Interface
You can dynamically save Spreadsheet by clicking file menu in ribbon and choose `SaveAs` option.

## Server dependencies
Import and Export Helper functions are available in the assembly `Syncfusion.EJ.Export`, which is available in Essential Studio and Essential JavaScript builds. The full list of assemblies needed for Spreadsheet import and export are as follows.

1. Syncfusion.EJ
2. Syncfusion.EJ.Export
3. Syncfusion.Linq.Base
4. Syncfusion.Compression.Base
5. Syncfusion.DocIO.Base
6. Syncfusion.XlsIO.Base
7. Syncfusion.PDF.Base
    
N> 1.  The above mentioned assemblies will be available in below location after Essential Studio build installation.
N> 2.  C:\Program Files (x86)\Syncfusion\Essential Studio\x.x.x.x\precompiledassemblies\x.x.x.x\y.y.
N> 3.  x.x.x.x defines build version of Essential Studio and y.y defines .NET Framework version.
