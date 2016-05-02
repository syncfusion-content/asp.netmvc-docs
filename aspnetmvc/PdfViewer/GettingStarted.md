---
layout: post
title: Getting Started | PDF viewer | ASP .NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: PDF viewer
documentation: ug
---


# Getting Started

This section explains briefly about how to add and use a PDF viewer control in your web application with ASP.NET MVC.

##Create your first PDF viewer application in ASP.NET MVC

Create a new project in the visual studio by selecting the ASP.NET MVC Empty Web Application template. The following screenshot displays the Project Creation Wizard in Visual Studio 2012.

![](GettingStarted_images/GettingStarted_img1.jpeg)

In the Project template select Empty template

![](GettingStarted_images/GettingStarted_img2.jpeg)

### Add Controller

Add new controller and name it as **PdfSampleController.cs**

![](GettingStarted_images/GettingStarted_img3.jpeg)

Add below references and set the Copy Local property to **True**

* Syncfusion.Compression.Base
* Syncfusion.Pdf.Base
* Syncfusion.EJ
* Syncfusion.EJ.PdfViewer
* Sycnfusion.EJ.MVC

### Modify RouteConfig.cs

Modify the routing to map to the **PdfSample** controller as below

{% highlight C# %}
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.Mvc;
using System.Web.Routing;
namespace PdfViewerSample
{
    public class RouteConfig
    {
        public static void RegisterRoutes(RouteCollection routes)
        {
            routes.IgnoreRoute("{resource}.axd/{*pathInfo}");
            routes.MapRoute(
                name: "Default",
                url: "{controller}/{action}/{id}",
                defaults: new { controller = "PdfSample", action = "Index", id = UrlParameter.Optional }
            );
        }
    }
}
{% endhighlight %}

###Modify Web.config

Set the value of **UnobtrusiveJavaScriptEnabled** to **false** in Web.config of Project (To enable the Unobstrusive option, please look at this [link](http://help.syncfusion.com/aspnetmvc/getting-started#to-enable-unobtrusive-option-in-your-application)).
Add below namespace in Web.config of Views.

<table>
<tr>
<td>
<add namespace="Syncfusion.EJ"/>
<add namespace="Syncfusion.MVC.EJ"/>
</td>
</tr>
</table>

### Add View

Create a new folder PdfSample in Views and add new view **Index.cshtml** in it.

![](GettingStarted_images/GettingStarted_img4.jpeg)

### i) Displaying PDF document using Remote service

Add below code snippet to Index.cshtml. Here, PDF viewer uses the hosted service in the remote machine to process the PDF.

{% highlight HTML %}
@using Syncfusion.JavaScript
@using Syncfusion.MVC.EJ.Extension
<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width" />
    <title>PDF viewer</title>
    <link href="~/assets/css/web/default-theme/ej.web.all.min.css" rel="stylesheet" />
    <script src="~/assets/external/jquery-2.1.4.min.js"></script>
    <script src="~/assets/external/jquery.validate.min.js"></script>
    <script src="~/assets/scripts/web/ej.web.all.min.js"></script>
</head>
<body>
    <div>
        <div style="width:100%;height:780px;">
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("http://mvc.syncfusion.com/PDFViewer/pdfviewer.asmx/PostViewerAction")
            .PdfService(Syncfusion.JavaScript.PdfViewerEnums.PdfService.Remote))
        </div>
    </div>
    @(Html.EJ().ScriptManager())
</body>
</html>
{% endhighlight %}

N> For adding scripts and styles, please refer **Add Scripts and Styles** section of [ejpdfviewer](http://help.syncfusion.com/js/pdfviewer/getting-started)

### ii) Displaying PDF document using Web API

Add new folder **webapi** in the solution and add new Web API Controller Class. Name it as **PdfViewerController** and click OK

![](GettingStarted_images/GettingStarted_img5.jpeg)

![](GettingStarted_images/GettingStarted_img6.jpeg)

Replace the below code in the PdfViewerController.cs

{% highlight C# %}
using Newtonsoft.Json;
using Syncfusion.EJ.PdfViewer;
using System.Collections.Generic;
using System.IO;
using System.Web;
using System.Web.Http;
namespace PdfViewerSample.WebApi
{
    public class PdfViewerController : ApiController
    {
        PdfViewerHelper helper = new PdfViewerHelper();
        public object PostViewerAction(Dictionary<string, string> jsonResult)
        {
            if (jsonResult.ContainsKey("isInitialLoading"))
                helper.Load(Helper.GetFilePath("HTTP Succinctly.pdf"));
            string output = JsonConvert.SerializeObject(helper.ProcessPdf(jsonResult));
            return output;
        }
    }
    public class Helper
    {
        public static string GetFilePath(string path)
        {
            string _dataPath = GetCommonFolder(new DirectoryInfo(HttpContext.Current.Request.PhysicalApplicationPath));
            _dataPath += @"\" + path;
            return _dataPath;
        }
        static string GetCommonFolder(DirectoryInfo dtInfo)
        {
            var _folderNames = dtInfo.GetDirectories("App_Data");
            if (_folderNames.Length > 0)
            {
                return _folderNames[0].FullName;
            }
            return dtInfo.Parent != null ? GetCommonFolder(dtInfo.Parent) : string.Empty;
        }
    }
}
{% endhighlight %}

N> Please, add the PDF document to be viewed in PDF viewer in App_Data folder of the project

Add below code snippet to Index.cshtml. Here, PDF viewer uses the Web API to process the PDF.

{% highlight HTML %}
@using Syncfusion.JavaScript
@using Syncfusion.MVC.EJ.Extension
<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width" />
    <title>PDF viewer</title>
    <link href="~/assets/css/web/default-theme/ej.web.all.min.css" rel="stylesheet" />
    <script src="~/assets/external/jquery-2.1.4.min.js"></script>
    <script src="~/assets/external/jquery.validate.min.js"></script>
    <script src="~/assets/scripts/web/ej.web.all.min.js"></script>
</head>
<body>
    <div>
        <div style="width:100%;height:780px;">
            @(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("../../api/PdfViewer")
            .PdfService(Syncfusion.JavaScript.PdfViewerEnums.PdfService.Local))
        </div>
    </div>
    @(Html.EJ().ScriptManager())
</body>
</html>
{% endhighlight %}

N> For adding scripts and styles, please refer **Add Scripts and Styles** section of [ejpdfviewer](http://help.syncfusion.com/js/pdfviewer/getting-started)

### Output

Run the sample and you will see the PDF viewer control as in the below screenshot.

![](GettingStarted_images/GettingStarted_img7.jpeg)

