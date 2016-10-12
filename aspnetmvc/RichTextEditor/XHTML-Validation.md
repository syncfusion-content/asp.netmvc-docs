---
layout: post
title: XHTML Validation in RichTextEditor widget for Syncfusion Essential ASP.NET MVC
description: XHTML Validation to format the RichTextEditor widget's content
platform: ASP.NET MVC
control: RTE
documentation: ug
keywords: RichTextEditor, XHTML Validation, RTE import, RTE export

---
# XHTML Validation

The editor provides option to validate its content through the EnableXHTML property. When you set or modify the content into the editor, it continuously checks whether the HTML source of the content that you are creating is valid. The editor examines the HTML markup and then removes the elements or attributes that are not valid. 

{% highlight razor %}

  @{
    Html.EJ().RTE("rteSample").Width("820px").ContentTemplate(@<div>
          The RichTextEditor (RTE) control enables you to edit the contents with insert table and images
          It also provides a toolbar that helps to apply rich text formats to the content entered in the TextArea
          </div>)
        .EnableXHTML(true)
        .Render();
    }

{% endhighlight %}

The editor checks the following settings on validation:

* **Attributes** 
  * Must be specified in lowercase 
  * Proper use of quotation marks around the attributes
  * Must be valid attributes for corresponding HTML element
  * All the required attributes must be included in the HTML element
  * Accepts the allowed values alone such as true or false.
* **HTML** **Elements** 
  * Must be in lowercase 
  * All opening tags must be closed
  * Allows only the valid HTML elements

# Import 

Import feature provides support to import a word document into the editor textarea. To enable import option in the RTE tool bar,  `import` toolbar items needs to be added in RTE toolbar toolsList using `importExport` which adds the tool in the toolbar. When you click the toolbar import icon, it opens a dialog to browse the select a word file. The selected word file will be imported into the editor textarea.

{% tabs %}
 
{% highlight razor %}

    @{
            List<String> toolsList = new List<string>() { "importExport" };
            List<String> ImportExport = new List<string>() { "import" };
      }
            
    @{

    Html.EJ().RTE("rteSample").Width("100%").ContentTemplate(@<div>
        &lt;p&gt;&lt;b&gt;Description:&lt;/b&gt;&lt;/p&gt;
        &lt;p&gt;The Rich Text Editor (RTE) control is an easy to render in
        client side. Customer easy to edit the contents and get the HTML content for
        the displayed content. A rich text editor control provides users with a toolbar
        that helps them to apply rich text formats to the text entered in the text
        area. &lt;/p&gt;
        &lt;p&gt;&lt;b&gt;Functional
        Specifications/Requirements:&lt;/b&gt;&lt;/p&gt;
        &lt;ol&gt;&lt;li&gt;&lt;p&gt;Provide
        the tool bar support, it’s also customizable.&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Options
        to get the HTML elements with styles.&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Support
        to insert image from a defined path.&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Footer
        elements and styles(tag / Element information , Action button (Upload, Cancel))&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Re-size
        the editor support. &lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Provide
        efficient public methods and client side events.&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Keyboard
        navigation support.&lt;/p&gt;&lt;/li&gt;&lt;/ol&gt;
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

![](XHTML-Validation_images/import_images.png)

# Export 

Export feature provides support to export editor textarea content into word and PDF files. To enable Export option in the RTE tool bar,  `wordExport` , `pdfExport` toolbar items needs to be added in RTE toolbar toolsList using `importExport` which adds the tool in the toolbar. When you click the toolbar pdfExport or wordExport icon, it performs server side XHTML Validation on the editor textarea content and exports it into a Word or pdf File.

{% tabs %}
 
{% highlight razor %}

    @{
        List<String> toolsList = new List<string>() { "importExport" };
        List<String> ImportExport = new List<string>() { "wordExport","pdfExport" };
      }
    @{
      Html.EJ().RTE("rteSample").Width("100%").ContentTemplate(@<div>
          &lt;p&gt;&lt;b&gt;Description:&lt;/b&gt;&lt;/p&gt;
          &lt;p&gt;The Rich Text Editor (RTE) control is an easy to render in
          client side. Customer easy to edit the contents and get the HTML content for
          the displayed content. A rich text editor control provides users with a toolbar
          that helps them to apply rich text formats to the text entered in the text
          area. &lt;/p&gt;
          &lt;p&gt;&lt;b&gt;Functional
          Specifications/Requirements:&lt;/b&gt;&lt;/p&gt;
          &lt;ol&gt;&lt;li&gt;&lt;p&gt;Provide
          the tool bar support, it’s also customizable.&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Options
          to get the HTML elements with styles.&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Support
          to insert image from a defined path.&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Footer
          elements and styles(tag / Element information , Action button (Upload, Cancel))&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Re-size
          the editor support. &lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Provide
          efficient public methods and client side events.&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Keyboard
          navigation support.&lt;/p&gt;&lt;/li&gt;&lt;/ol&gt;
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


![](XHTML-Validation_images/export_images.png)
