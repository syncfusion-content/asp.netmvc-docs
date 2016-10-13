---
layout: post
title: XHTML Validation in RichTextEditor widget for Syncfusion Essential ASP.NET MVC
description: Import a word document into the RichTextEditor and Export the widget's content into a word or pdf file
platform: ASP.NET MVC
control: RTE
documentation: ug
keywords: RichTextEditor,server side XHTML Validation, RTE import, RTE export, export to PDF, export to Word

---

# Import 

Import feature provides support to import a word document into the editor textarea. To enable import option in the RTE tool bar,  `import` toolbar items needs to be added in RTE toolbar toolsList using `importExport` which adds the tool in the toolbar. In `ImportSettings` Url option, the server page for import is needed to be mapped. When you click the toolbar import icon, it opens a dialog to browse the select a word file. The selected word file will be imported into the editor textarea.

{% tabs %}
 
{% highlight razor %}

    @{
            List<String> toolsList = new List<string>() { "importExport" };
            List<String> ImportExport = new List<string>() { "import" };
      }
            
    @{

    Html.EJ().RTE("rteSample").Width("100%").ContentTemplate(@<div>
        &lt;p&gt;The Rich Text Editor (RTE) control is an easy to render in
        client side. Customer easy to edit the contents and get the HTML content for
        the displayed content. A rich text editor control provides users with a toolbar
        that helps them to apply rich text formats to the text entered in the text
        area. &lt;/p&gt;
    </div>).MinWidth("200px").ToolsList(toolsList).Tools(tool => tool.ImportExport(ImportExport))
                .ImportSettings(importSettings => importSettings.Url("Import")).Render();
                
    }



{% endhighlight  %}
{% highlight c# %}

    public partial class RTEController : Controller
    {
        //
        // GET: /ImportExport/

        public ActionResult ImportExport()
        {
            return View();
        }

        [HttpPost]
        public string Import()
        {
            string HtmlString = string.Empty;
            if (HttpContext.Request.Files.AllKeys.Any())
            {
                string RTEID = HttpContext.Request.QueryString["rteid"];
                var fileName = RTEID + "_importUpload";
                var httpPostedFile = HttpContext.Request.Files[fileName];
                if (httpPostedFile != null)
                {
                    using (var mStream = new MemoryStream())
                    {
                        new WordDocument(httpPostedFile.InputStream).Save(mStream, FormatType.Html);
                        mStream.Position = 0;
                        HtmlString = new StreamReader(mStream).ReadToEnd();
                    };

                    HtmlString = ExtractBodyContent(HtmlString);

                    foreach (var item in DecodeKeys())
                    {
                        HtmlString = HtmlString.Replace(item.Key, item.Value);
                    }
                }
                else HttpContext.Response.Write("Select any file to upload.");

            }
            return HtmlString;
        }

        
        public IDictionary<string, string> DecodeKeys()
        {
            IDictionary<string, string> KeyValuePair = new Dictionary<string, string>()
            {
               {"\"", "'"},{"\r", " "},{"\n", "<br/> "},{"\r\n", " "},{"( )+", " "},{"&nbsp;", " "},{"&bull;", "*"},{"&lsaquo;", "<"},
               {"&rsaquo;", ">"},{"&trade;", "(tm)"},{"&copy;", "(c)"},{"&reg;", "(r)"}
            };

            return KeyValuePair;
        }

        public string ExtractBodyContent(string html)
        {
            if (html.Contains("<html") && html.Contains("<body"))
            {
                return html.Remove(0, html.IndexOf("<body>") + 6).Replace("</body></html>", "");

            }
            return html;
        }

        
    }

{% endhighlight  %}
{% endtabs %} 

## Server Dependencies

Full list of assemblies needed for RTE Import are as follows

    1.  Syncfusion.EJ
    2.  Syncfusion.EJ.Export
    3.  Syncfusion.Linq.Base
    4.  Syncfusion.Compression.Base
    5.  Syncfusion.DocIO.Base

![](ImportAndExport_images/import_images.png)

# Export 

Export feature provides support to export editor textarea content into word and PDF files. To enable Export option in the RTE tool bar,  `wordExport` , `pdfExport` toolbar items needs to be added in RTE toolbar toolsList using `importExport` which adds the tool in the toolbar. `ExportToWordSettings` consists of Url and FileName sub properties. In Url property, the server page for export to word is needed to be mapped and In FileName property, the name for the exported word file is given. `ExportToPdfSettings` consists of Url and FileName sub properties. In Url property, the server page for export to pdf is needed to be mapped and In FileName property, the name for the exported pdf file is given. When you click the toolbar pdfExport or wordExport icon, the contents of RTE are sent to the server. It performs XHTML Validation on the editor textarea content on the server. Once the XHTML validation and formatting is sucessful, it exports the content into a Word or pdf File.

{% tabs %}
 
{% highlight razor %}

    @{
        List<String> toolsList = new List<string>() { "importExport" };
        List<String> ImportExport = new List<string>() { "wordExport","pdfExport" };
      }
    @{
      Html.EJ().RTE("rteSample").Width("100%").ContentTemplate(@<div>
          &lt;p&gt;The Rich Text Editor (RTE) control is an easy to render in
          client side. Customer easy to edit the contents and get the HTML content for
          the displayed content. A rich text editor control provides users with a toolbar
          that helps them to apply rich text formats to the text entered in the text
          area. &lt;/p&gt;
      </div>).MinWidth("200px").ToolsList(toolsList).Tools(tool => tool.ImportExport(ImportExport))
                  .ExportToWordSettings(exportToWordSettings => exportToWordSettings.Url("ExportToWord").FileName("WordExport"))
                  .ExportToPdfSettings(exportToPdfSettings => exportToPdfSettings.Url("ExportToPDF").FileName("PdfExport")).Render();
    }




{% endhighlight  %}
{% highlight c# %}

    public partial class RTEController : Controller
    {
        //
        // GET: /ImportExport/

        public ActionResult ImportExport()
        {
            return View();
        }
        
        //Export to Word Document
        [HttpPost]
        [ValidateInput(false)]
        public void ExportToWord()
        {

            string RTEID = HttpContext.Request.QueryString["rteid"];
            string FileName = HttpContext.Request.Params[RTEID + "_inputFile"];
            string htmlText = HttpContext.Request.Params[RTEID + "_inputVal"];
            WordDocument document = GetDocument(htmlText);
            document.Save(FileName + ".docx", FormatType.Docx, System.Web.HttpContext.Current.Response, HttpContentDisposition.Attachment);
        }

        //Export to PDF Document
        [HttpPost]
        [ValidateInput(false)]
        public void ExportToPDF()
        {
            string RTEID = HttpContext.Request.QueryString["rteid"];
            string FileName = HttpContext.Request.Params[RTEID + "_inputFile"];
            string htmlText = HttpContext.Request.Params[RTEID + "_inputVal"];
            WordDocument document = GetDocument(htmlText);
            DocToPDFConverter converter = new DocToPDFConverter();
            PdfDocument pdfDocument = converter.ConvertToPDF(document);
            pdfDocument.Save(FileName + ".pdf", System.Web.HttpContext.Current.Response, HttpReadType.Save);
        }

        public WordDocument GetDocument(string htmlText)
        {
            WordDocument document = null;
            MemoryStream stream = new MemoryStream();
            StreamWriter writer = new StreamWriter(stream, System.Text.Encoding.Default);
            htmlText = htmlText.Replace("\"", "'");
            XmlConversion XmlText = new XmlConversion(htmlText);
            XhtmlConversion XhtmlText = new XhtmlConversion(XmlText);
            writer.Write(XhtmlText.ToString());
            writer.Flush();
            stream.Position = 0;
            document = new WordDocument(stream, FormatType.Html, XHTMLValidationType.None);
            return document;
        }

    }

{% endhighlight  %}
{% endtabs %} 

## Server Dependencies

Export Helper functions are available in the Assembly `Syncfusion.EJ.Export`, which is available in the Essential Studio builds. Full list of assemblies needed for RTE Export as follows

    1.  Syncfusion.EJ
    2.  Syncfusion.EJ.Export
    3.  Syncfusion.Linq.Base
    4.  Syncfusion.Compression.Base
    5.  Syncfusion.DocIO.Base
    6.  Syncfusion.PDF.Base

### Word Export
![](ImportAndExport_images/export_word_images.png)

### PDF Export
![](ImportAndExport_images/export_pdf_images.png)