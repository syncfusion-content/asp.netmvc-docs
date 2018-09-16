---
layout: post
title: Getting Started | ReportDesigner | ASP.NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: ReportDesigner
documentation: ug
---

# Getting Started

This section explains briefly about how to create a **ReportDesigner** in your ASP.NET MVC application.

## Project Creation

The following screenshots displays the Project Creation Wizard in Visual Studio 2013

Create a new ASP.NET MVC4 Web Application project by selecting the **WEB** category from the listed project template in Microsoft Visual Studio IDE.

![](Getting-Started_images/Getting-Started_img1.png)

Project Creation Wizard
{:.caption}

The following screenshot displays how to select the project template with razor view engine:

![](Getting-Started_images/Getting-Started_img3.png)

Select an empty template and click OK.

### Add References

1. In the Solution Explorer, right-click the `References` folder and then click `Add Reference`.

    ![](Getting-Started_images/Getting-Started_img2.png) 

2. Add the following references to the project that are necessary for using the report designer control and  set the Copy Local property to **True**.

   * Syncfusion.Chart.Wpf
   * Syncfusion.Compression.Base
   * Syncfusion.DocIO.Base
   * Syncfusion.EJ.ReportDesigner
   * Syncfusion.EJ.ReportViewer
   * Syncfusion.Gauge.Wpf
   * Syncfusion.Pdf.Base
   * Syncfusion.Presentation.Base
   * Syncfusion.Shared.Wpf
   * Syncfusion.SfMaps.Wpf
   * Syncfusion.XlsIO.Base
   * Syncfusion.EJ
   * Syncfusion.EJ.MVC

    > Refer the Syncfusion.EJ.MVC assembly from the installed location, [Installed Location]:\Program Files (x86)\Syncfusion\Essential Studio\ASP.NET MVC\{{ site.releaseversion }}\Assemblies\MVC\MVC4

    > Refer the other assemblies from the installed location, [Installed Location]:\Program Files (x86)\Syncfusion\Essential Studio\ASP.NET MVC\{{ site.releaseversion }}\Assemblies

3.  Add reference to the following assemblies from [NuGet package](https://help.syncfusion.com/extension/syncfusion-nuget-packages/web-nuget-packages-details "Web NuGet Package Details").

    * System.Web.Http
    * System.Web.Http.WebHost
    * System.Net.Http.WebRequest
    * System.Net.Http.Formatting

    > The System.Web.Routing and System.Net.Http assemblies are also required, which are referred by default when creating the project.

### Add Controller 

1. Right-Click on the **Controllers** folder in the project and select `Add` then select `Controller`.

    ![](Getting-Started_images/Getting-Started_img8.png)

2. Name the controller as **ReportDesignerController**.

    ![](Getting-Started_images/Getting-Started_img9.png)

3. Click Add.

    ![](Getting-Started_images/Getting-Started_img10.png)

### Modify RouteConfig.cs

1. Open the RouteConfig.cs file from `App_Start` folder of your application.

    ![](Getting-Started_images/Getting-Started_img15.png)

2. Modify the controller name to map to the **ReportDesigner** controller as follows.

    {% highlight C# %}

    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Web;
    using System.Web.Mvc;
    using System.Web.Routing;

    namespace ReportDesignerSample
    {
        public class RouteConfig
        {
            public static void RegisterRoutes(RouteCollection routes)
            {
                routes.IgnoreRoute("{resource}.axd/{*pathInfo}");
                routes.MapRoute(
                    name: "Default",
                    url: "{controller}/{action}/{id}",
                    defaults: new { controller = "ReportDesigner", action = "Index", id = UrlParameter.Optional }
                );
            }
        }
    }

    {% endhighlight %}

### Add View page

1. Create a new folder **ReportDesigner** in `Views` folder.

    ![](Getting-Started_images/Getting-Started_img11.png)

2. Right-Click on the **ReportDesigner** folder in the `Views` folder and select `Add` then select `View`.

    ![](Getting-Started_images/Getting-Started_img12.png)

3. Name the view page as **Index**.

    ![](Getting-Started_images/Getting-Started_img13.png)

4. Click `Add`.

    ![](Getting-Started_images/Getting-Started_img14.png)


### Add Scripts and Styles

For complete dependencies list of report designer control [Click here](/aspnetmvc/ReportDesigner/Dependencies).

* Add the below code snippet in the Index.cshtml page.

    {% highlight CSHTML %}

    @using Syncfusion.JavaScript
    @using Syncfusion.MVC.EJ

    <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="utf-8" />
            <title>@ViewBag.Title</title>
    </head>
    <body>
    </body>
    </html>
    {% endhighlight %} 

* Add the script files and theme files in the &lt;head&gt; tag of the Index.cshtml page.

**Themes**

{% highlight CSHTML %}

<link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
<link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.reportdesigner.min.css" rel="stylesheet" />

{% endhighlight %} 

**Scripts**

**External dependencies**

{% highlight CSHTML %}

<script src="http://code.jquery.com/jquery-1.10.2.min.js" type="text/javascript"></script>
<script src="http://cdnjs.cloudflare.com/ajax/libs/jquery-easing/1.3/jquery.easing.min.js" type="text/javascript"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jsrender/0.9.90/jsrender.min.js" type="text/javascript"></script>

{% endhighlight %} 

**Internal dependencies**

Refer the below scripts to render report designer control.

{% highlight CSHTML %}

<script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js" type="text/javascript"></script>
<script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.reportdesigner.min.js" type="text/javascript"></script>
 
{% endhighlight %} 

**Code Mirror**

To edit the SQL queries with syntax highlighter need to refer the below code mirror scripts and themes.

{% highlight CSHTML %}

<link href="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.37.0/codemirror.min.css" rel="stylesheet" />
<link href="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.37.0/addon/hint/show-hint.min.css" rel="stylesheet" />

<script src="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.37.0/codemirror.min.js" type="text/javascript"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.37.0/addon/hint/show-hint.min.js" type="text/javascript"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.37.0/addon/hint/sql-hint.min.js" type="text/javascript"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.37.0/mode/sql/sql.min.js" type="text/javascript"></script>

{% endhighlight %} 

Use the above code example while adding scripts and styles.

> Also the scripts and styles can be referred from the installed location, [Installed Location]:\Program Files (x86)\Syncfusion\Essential Studio\ASP.NET MVC\{{ site.releaseversion }}\JavaScript\assets

### Unobtrusive Mode

**Enable unobtrusive mode**

1. To render the Report Designer in unobtrusive mode, refer to the **ej.unobtrusive.js** script file in &lt;head&gt; of Index.cshtml page.

{% highlight CSHTML %}

<script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/common/ej.unobtrusive.min.js"></script>

{% endhighlight %}

2. Set **UnobtrusiveJavaScriptEnabled** to true in Web.config file of your application.

    ![](Getting-Started_images/Getting-Started_img18.png)

    ![](Getting-Started_images/Getting-Started_img16.png)

**Disable unobtrusive mode**

Set **UnobtrusiveJavaScriptEnabled** to false in Web.config file of your application.

![](Getting-Started_images/Getting-Started_img17.png)

### Registering namespaces within Web.config

Register the following namespaces in the web.config file present within the Views folder as well as the root directory of your application.

{% highlight XML %}

<namespaces>
    <add namespace="Syncfusion.EJ.ReportViewer"/>
    <add namespace="Syncfusion.EJ.ReportDesigner"/>
    <add namespace="Syncfusion.EJ"/>
    <add namespace="Syncfusion.MVC.EJ"/>
</namespaces>

{% endhighlight %}

### Add Control in View page

Add the following code example in the &lt;body&gt; tag of the `Index.cshtml` page that is already created. Set the desired `ServiceUrl` to ReportDesigner.

{% highlight CSHTML %}

<div>
    @{Html.EJ().ReportDesigner("designer").ServiceUrl("/api/DesignerAPI").Render();}
</div>

{% endhighlight %}

### Add WebAPI controller for ReportDesigner

The MVC ReportDesigner uses WebApi services to process the report file and process the request from control.

**Add Controller**

1. Right-Click on the project and select `Add` then click `New Item`. 

    ![](Getting-Started_images/Getting-Started_img4.png)

2. Select `Web API Controller Class` from the listed templates and name the controller as **DesignerAPIController.cs**. 

    ![](Getting-Started_images/Getting-Started_img19.png)

3. Click Add.

    ![](Getting-Started_images/Getting-Started_img20.png)

#### Inherit IReportDesignerController
 
The ApiController should inherit the `IReportDesignerController` and to process the report file. The interface `IReportDesignerController` contains the required actions and helper methods declaration to process the report. The `ReportDesignerHelper` and `ReportHelper` class contains helper methods that helps to process Post/Get request from control and return the response to control.

Please add the following code example in `DesignerAPIController.cs`.

{% highlight c# %}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Net;
using System.Net.Http;
using System.Web.Http;
using System.IO;
using System.Web;
using Syncfusion.EJ.ReportViewer;
using Syncfusion.Reports.EJ;
using Syncfusion.EJ.ReportDesigner;

namespace ReportDesignerSample
{
    public class DesignerAPIController : ApiController, Syncfusion.EJ.ReportDesigner.IReportDesignerController
    {
        public string GetFilePath(string fileName)
        {
            string targetFolder = HttpContext.Current.Server.MapPath("~/");
            targetFolder += "Cache";

            if (!Directory.Exists(targetFolder))
            {
                Directory.CreateDirectory(targetFolder);
            }

            if (!Directory.Exists(targetFolder + "\\" + ReportDesignerHelper.EJReportDesignerToken))
            {
                Directory.CreateDirectory(targetFolder + "\\" + ReportDesignerHelper.EJReportDesignerToken);
            }

            var folderPath = HttpContext.Current.Server.MapPath("~/") + "Cache\\" + ReportDesignerHelper.EJReportDesignerToken + "\\";
            return folderPath + fileName;
        }

        [HttpGet]
        public object GetImage(string key, string image)
        {
            return ReportDesignerHelper.GetImage(key, image, this);
        }

        [HttpPost]
        public object PostDesignerAction(Dictionary<string, object> jsonResult)
        {
            return ReportDesignerHelper.ProcessDesigner(jsonResult, this, null);
        }

        public bool UploadFile(System.Web.HttpPostedFile httpPostedFile)
        {
            string targetFolder = HttpContext.Current.Server.MapPath("~/");
            string fileName = !string.IsNullOrEmpty(ReportDesignerHelper.SaveFileName) ? ReportDesignerHelper.SaveFileName : Path.GetFileName(httpPostedFile.FileName);
            targetFolder += "Cache";

            if (!Directory.Exists(targetFolder))
            {
                Directory.CreateDirectory(targetFolder);
            }

            if (!Directory.Exists(targetFolder + "\\" + ReportDesignerHelper.EJReportDesignerToken))
            {
                Directory.CreateDirectory(targetFolder + "\\" + ReportDesignerHelper.EJReportDesignerToken);
            }

            httpPostedFile.SaveAs(targetFolder + "\\" + ReportDesignerHelper.EJReportDesignerToken + "\\" + fileName);
            return true;
        }

        public void UploadReportAction()
        {
            ReportDesignerHelper.ProcessDesigner(null, this, HttpContext.Current.Request.Files[0]);
        }

        public object GetResource(string key, string resourcetype, bool isPrint)
        {
            return ReportHelper.GetResource(key, resourcetype, isPrint);
        }

        public void OnInitReportOptions(ReportViewerOptions reportOption)
        {
            //You can update report options here
        }

        public void OnReportLoaded(ReportViewerOptions reportOption)
        {
            //You can update report options here
        }

        public object PostReportAction(Dictionary<string, object> jsonResult)
        {
            return ReportHelper.ProcessReport(jsonResult, this as IReportController);
        }

        public FileModel GetFile(string filename, bool isOverride)
        {
            throw new NotImplementedException();
        }

        public List<FileModel> GetFiles(FileType fileType)
        {
            throw new NotImplementedException();
        }
    }
}

{% endhighlight %}

### WebAPI Routing

If `Global Application Class` file already exists in your application skip the below **Add Global Application Class** section.

#### Add Global Application Class

1. Right-Click on the project and select `Add` then click `New Item`. 

    ![](Getting-Started_images/Getting-Started_img4.png)

2. Select `Global Application Class` from the listed templates and name it as `Global.asax`.

    ![](Getting-Started_images/Getting-Started_img5.png)

3. Click Add.

    ![](Getting-Started_images/Getting-Started_img5.png)
 
#### Route WebAPI

Open the `Global Application Class` file in the application and modify the WebAPI routing in Application_Start event as follows.

{% highlight c# %}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.Security;
using System.Web.SessionState;
using System.Web.Http;

namespace ReportDesignerSample
{
    public class Global : System.Web.HttpApplication
    {
        protected void Application_Start(object sender, EventArgs e)
        {
            System.Web.Http.GlobalConfiguration.Configuration.Routes.MapHttpRoute(
            name: "DefaultApi",
            routeTemplate: "api/{controller}/{action}/{id}",
            defaults: new { id = RouteParameter.Optional });
            AppDomain.CurrentDomain.SetData("SQLServerCompactEditionUnderWebHosting", true);
        }
    }
}

{% endhighlight %}

### Run the Application

On running the application, Report Designer will be rendered like below.

![](Getting-Started_images/Getting-Started_img7.png)
