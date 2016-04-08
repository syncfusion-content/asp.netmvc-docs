---
layout: post
title: OLAP Getting Started | PivotGrid| ASP.NET MVC | Syncfusion
description: olap getting started
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Getting Started

## Creating a simple application with PivotGrid and OLAP datasource (Client Mode)

This section covers the information that you need to know to populate a simple PivotGrid with OLAP data completely on the client-side.

### Scripts and CSS References  

The scripts and style sheets that are mandatorily required to render PivotGrid widget in a MVC Web Application are mentioned in an appropriate order below:

1. ej.widgets.all.min.css
2. jquery-1.10.2.min.js
3. jquery.easing.1.3.min.js
4. jquery.linq.js
5. ej.web.all.min.js

Scripts and style sheets are referred under the head tag in _Layout.cshtml file which is found inside Views > Shared folder.

{% highlight html %}    

<head>
    <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" type="text/css" />
    <script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js" type="text/javascript"></script>
    <script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js" type="text/javascript"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/linq.js/2.2.0.2/jquery.linq.js" type="text/javascript"></script>
    <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js" type="text/javascript"></script>
    
</head>    

{% endhighlight %}

### Initialize PivotGrid

Before initializing, empty the contents of Index.cshtml file under Views > Home folder and add the following codes.

{% highlight html %}

@using Syncfusion.JavaScript;

<div>
    @Html.EJ().Pivot().PivotGrid("PivotGrid1")
</div>

{% endhighlight %}

### Populate PivotGrid With DataSource

Initializes the OLAP datasource for PivotGrid widget as shown below.

{% highlight html %}

 @Html.EJ().Pivot().PivotGrid("PivotGrid1").DataSource(dataSource => dataSource.Rows(rows=>{rows.FieldName("[Date].[Fiscal]").Add();}).Columns(columns=>{columns.FieldName("[Customer].[Customer Geography]").Add();}).Values(values => { values.Measures(measures => { measures.FieldName("[Measures].[Internet Sales Amount]").Add(); }).Axis(AxisName.Column).Add();}).Data("http://bi.syncfusion.com/olap/msmdpump.dll").Catalog("Adventure Works DW 2008 SE").Cube("Adventure Works"))

{% endhighlight %}

The above code will generate a simple PivotGrid with "Fiscal" field in Row, "Customer Geography" field in Column and "Internet Sales Amount" field in Value section.

![](Getting-Started_images/OlapClientside.png) 

## Creating a simple application with PivotGrid and OLAP datasource (Server Mode)
 
This section covers the information required to create a simple PivotGrid bound to OLAP datasource.

N> ASP.NET MVC Web Application will contain a service that transfers data to server-side, processes and returns back to client-side for control rendering and re-rendering. The service utilized for communication could be either WCF or WebAPI based on user requirement.

### Project Initialization

Create a new **ASP.NET MVC Web Application** using Visual Studio IDE and name the project as **"PivotGridDemo"**. 

Select the View engine as **‘Razor’** and Project template as **‘Internet Application’** and finally click **OK** button to create an application.

Now add the following dependency libraries as references into your MVC Web Application. In order to add them to your application, right-click on **References** in Solution Explorer and select **Add Reference**. Now in the **Reference Manager** dialog, under **Assemblies > Extension**, the following Syncfusion libraries will be found.

* Microsoft.AnalysisServices.AdomdClient
* Syncfusion.Compression.Base
* Syncfusion.Linq.Base
* Syncfusion.Olap.Base
* Syncfusion.PivotAnalysis.Base
* Syncfusion.XlsIO.Base
* Syncfusion.Pdf.Base
* Syncfusion.DocIO.Base
* Syncfusion.EJ
* Syncfusion.EJ.Olap
* Syncfusion.EJ.MVC

N> If any version of SQL Server Analysis Service (SSAS) or Microsoft ADOMD.NET utility is installed, then the location of Microsoft.AnalysisServices.AdomdClient library is [system drive:\Program Files (x86)\Microsoft.NET\ADOMD.NET].

The version of Syncfusion libraries based on .NET framework and MVC version are classified below. For example, 14.1 version is illustrated as,

<table>
<tr>
<th>
MVC Version</th><th>
MVC Version of Syncfusion dll</th><th>
Base Version of Syncfusion dll</th><th>
System.Web.Mvc</th><th>
System.Web.WebPages</th>
</tr>
<tr><td>
MVC3</td><td>
{{ site.mvc3releaseversion }}</td><td>    
{{ site.35esreleaseversion }}</td><td>
3.0</td><td>
1.0</td>
</tr>
<tr><td>
MVC4</td><td>
{{ site.mvc4releaseversion }}</td><td>    
{{ site.40esreleaseversion }}</td><td>
4.0</td><td>
2.0</td>
</tr>
<tr><td>
MVC5</td><td>
{{ site.mvc5releaseversion }}</td><td>    
{{ site.45esreleaseversion }}</td><td>
5.0</td><td>
3.0</td>
</tr>
</table>

Register the referenced assemblies in Web.config files available inside Views folder and also at the root of the application.

{% highlight xml %}

<compilation debug="true" targetFramework="4.5">
    <assemblies> 
        …… 
        ……
        <add assembly="Syncfusion.EJ, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.EJ.Olap, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.EJ.Mvc, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.Linq.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.Olap.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.Compression.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" /> 
        <add assembly="Syncfusion.PivotAnalysis.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" /> 
        <add assembly="Syncfusion.Pdf.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.XlsIO.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.DocIO.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" /> 
    </assemblies>
</compilation>

{% endhighlight %}

Register the required namespaces in Web.config files available inside Views folder and also at the root of the application

{% highlight xml %}

<namespaces> 
    ……
    ……
    <add namespace="Syncfusion.MVC.EJ" />
    <add namespace="Syncfusion.JavaScript" /> 
</namespaces>

{% endhighlight %}

N> Registering assemblies and namespaces earlier helps to include the control in view page with the help of intellisense.

Set the **UnobtrusiveJavaScriptEnabled** property to false under **appSettings** tag in Web.config file at the root folder.
    
{% highlight xml %}

<configuration> 
  	…… 
  	……
    <appSettings> 
      	…… 
      	……
        <add key="UnobtrusiveJavaScriptEnabled" value="false" /> 
   </appSettings>
        
</configuration>

{% endhighlight %}


### Scripts and CSS Initialization

The scripts and style sheets that are mandatorily required to render PivotGrid widget in a MVC Web Application are mentioned in an appropriate order below:

1.  ej.widgets.all.min.css
2.	jquery-1.10.2.min.js
3.	jquery.easing.1.3.min.js
4.	ej.web.all.min.js 

[Click here](http://help.syncfusion.com/js/cdn) here to know more about scripts and style sheets available online (CDN Link).

Scripts and style sheets are referred under the **head** tag in **_Layout.cshtml** file which is found inside **Views > Shared folder.**
    
{% highlight html %}

<head>
    <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
    <script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js" type="text/javascript"> </script>
    <script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js" type="text/javascript"> </script>
    <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js"> </script>
</head>

{% endhighlight %}

The script manager is initialized immediately after the `RenderBody()` function call in **_Layout.cshtml** file in-order to generate widget related scripts.

{% highlight html %}

<body> 
  …… 
  …… 
  @RenderBody() 
  @(Html.EJ().ScriptManager()) 
  
</body>

{% endhighlight %}

### Control Initialization

Before initializing, empty the contents of **Index.cshtml** file under **Views > Home** folder and add the following codes. Register the namespaces at the top of the page and then add the control.

{% highlight html %}
    
@using Syncfusion.JavaScript.Olap;

<div> 
@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url(Url.Content("~/OLAPService")) 
</div>

{% endhighlight %}

The **“Url”** property in PivotGrid widget points the service endpoint, where data are processed and fetched in the form of JSON. The services used in PivotGrid widget as endpoint are WCF and WebAPI.

N> The above "Index.cshtml" contains WebAPI Url, which is "~/OLAPService". If WCF service is used as endpoint, the Url would look like "~/OLAPService.svc".


### WebAPI

**Adding a WebAPI Controller**

To add a WebAPI controller in an existing Web Application, right-click on the project in Solution Explorer and select **Add > New Item**. In the **Add New Item** window, select **WebAPI Controller Class** and name it as `OLAPServiceController.cs`, click Add.

Now, WebAPI controller is added to the application successfully with the file **"OLAPServiceController.cs"**.

N> While adding WebAPI Controller Class, name it with the suffix 'Controller' that is mandatory. For example, in this demo the controller is named as **"OLAPServiceController"**.

Next, remove all the existing methods such as "Get", "Post", "Put" and "Delete" present inside `OLAPServiceController.cs` file.

{% highlight c# %}

namespace PivotGridDemo
{
    public class OLAPServiceController: ApiController
    {
    
    }
}

{% endhighlight %}

**Adding the List of Namespaces**

The following are the list of namespaces to be added on top of the main class inside `OLAPServiceController.cs` file.

{% highlight c# %}

using System.Web.Script.Serialization;
using Syncfusion.Olap.Manager;
using Syncfusion.Olap.Reports;
using Syncfusion.JavaScript;
using Syncfusion.JavaScript.Olap;

namespace PivotGridDemo
{
    public class OLAPServiceController: ApiController
    {
    
    }
}

{% endhighlight %}

**Datasource Initialization**

Now, the connection string to connect OLAP Cube, PivotGrid and JavaScriptSerializer instances are created immediately inside the main class in `OLAPServiceController.cs` file.

{% highlight c# %}

namespace PivotGridDemo
{
    public class OLAPServiceController: ApiController
    {
        PivotGridhtmlHelper = new PivotGrid();
        string connectionString = "Data Source=http://bi.syncfusion.com/olap/msmdpump.dll; Initial Catalog=Adventure Works DW 2008 SE;";
        JavaScriptSerializer serializer = new JavaScriptSerializer();
        //Other codes
     }
}

{% endhighlight %}

**Service methods in WebAPI Controller**

Define the service methods inside OLAPServiceController class, found inside `OLAPServiceController.cs` file, created while adding WebAPI Controller Class to the Application.

{% highlight c# %}

namespace PivotGridDemo {
    public class OLAPServiceController: ApiController {
        PivotGridhtmlHelper = new PivotGrid();
        string connectionString = "Data Source=http://bi.syncfusion.com/olap/msmdpump.dll; Initial Catalog=Adventure Works DW 2008 SE;";
        JavaScriptSerializer serializer = new JavaScriptSerializer();

        [System.Web.Http.ActionName("InitializeGrid")]
        [System.Web.Http.HttpPost]
        public Dictionary < string, object > InitializeGrid(Dictionary < string, object > jsonResult) {
            Dictionary < string, object > customDict = new Dictionary < string, object > ();
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(CreateOlapReport());
            customDict = htmlHelper.GetJsonData(jsonResult["action"].ToString(), DataManager, jsonResult.ContainsKey("gridLayout") ? jsonResult["gridLayout"].ToString() : null, Convert.ToBoolean(jsonResult["enablePivotFieldList"].ToString()));
            return customDict;
        }

        [System.Web.Http.ActionName("DrillGrid")]
        [System.Web.Http.HttpPost]
        public Dictionary < string, object > DrillGrid(Dictionary < string, object > jsonResult) {
            dynamic customData = serializer.Deserialize < dynamic > (jsonResult["customObject"].ToString());
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager = new OlapDataManager(connectionString);
            if ((customData.ContainsKey("Language"))) {
                DataManager.Culture = new System.Globalization.CultureInfo((customData["Language"]));
                DataManager.OverrideDefaultFormatStrings = true;
            }
            DataManager.SetCurrentReport(Syncfusion.JavaScript.Olap.Utils.DeserializeOlapReport(jsonResult["currentReport"].ToString()));
            return htmlHelper.GetJsonData(jsonResult["action"].ToString(), connectionString, DataManager, jsonResult["cellPosition"].ToString(), jsonResult["headerInfo"].ToString(), jsonResult["layout"].ToString());
        }

        [System.Web.Http.ActionName("NodeDropped")]
        [System.Web.Http.HttpPost]
        public Dictionary < string, object > NodeDropped(Dictionary < string, object > jsonResult) {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(Syncfusion.JavaScript.Olap.Utils.DeserializeOlapReport(jsonResult["currentReport"].ToString()));
            return htmlHelper.GetJsonData(jsonResult["action"].ToString(), DataManager, jsonResult["dropType"].ToString(), jsonResult["nodeInfo"].ToString(), null,
                true);
        }

        [System.Web.Http.ActionName("Filtering")]
        [System.Web.Http.HttpPost]
        public Dictionary < string, object > Filtering(Dictionary < string, object > jsonResult) {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(Syncfusion.JavaScript.Olap.Utils.DeserializeOlapReport(jsonResult["currentReport"].ToString()));
            return htmlHelper.GetJsonData(jsonResult["action"].ToString(), DataManager, null, jsonResult["filterParams"].ToString());
        }

        [System.Web.Http.ActionName("FetchMembers")]
        [System.Web.Http.HttpPost]
        public Dictionary < string, object > FetchMembers(Dictionary < string, object > jsonResult) {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(Syncfusion.JavaScript.Olap.Utils.DeserializeOlapReport(jsonResult["currentReport"].ToString()));
            return htmlHelper.GetJsonData(jsonResult["action"].ToString(), DataManager, null, jsonResult["headerTag"].ToString());
        }

        [System.Web.Http.ActionName("Paging")]
        [System.Web.Http.HttpPost]
        public Dictionary < string, object > Paging(Dictionary < string, object > jsonResult) {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(htmlHelper.SetPaging(jsonResult["currentReport"].ToString(), jsonResult["pagingInfo"].ToString()));
            return htmlHelper.GetJsonData(jsonResult["action"].ToString(), DataManager, jsonResult["gridLayout"].ToString());
        }

        [System.Web.Http.ActionName("RemoveButton")]
        [System.Web.Http.HttpPost]
        public Dictionary < string, object > RemoveButton(Dictionary < string, object > jsonResult) {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(Syncfusion.JavaScript.Olap.Utils.DeserializeOlapReport(jsonResult["currentReport"].ToString()));
            return htmlHelper.GetJsonData(jsonResult["action"].ToString(), DataManager, null, jsonResult["headerInfo"].ToString());
        }

        [System.Web.Http.ActionName("MemberExpanded")]
        [System.Web.Http.HttpPost]
        public Dictionary < string, object > MemberExpanded(Dictionary < string, object > jsonResult) {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            if (!string.IsNullOrEmpty(jsonResult["currentReport"].ToString()))
                DataManager.SetCurrentReport(Syncfusion.JavaScript.Olap.Utils.DeserializeOlapReport(jsonResult["currentReport"].ToString()));
            return htmlHelper.GetJsonData(jsonResult["action"].ToString(), DataManager, jsonResult["checkedStatus"].ToString(), jsonResult["parentNode"].ToString(),
                jsonResult["tag"].ToString(), jsonResult["cubeName"].ToString());
        }

        [System.Web.Http.ActionName("Export")]
        [System.Web.Http.HttpPost]
        public void Export(System.IO.Stream stream) {
            System.IO.StreamReader sReader = new System.IO.StreamReader(stream);
            string args = System.Web.HttpContext.Current.Server.UrlDecode(sReader.ReadToEnd());
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            string fileName = "Sample";
            htmlHelper.ExportPivotGrid(DataManager, args, fileName, System.Web.HttpContext.Current.Response);
        }

        private OlapReport CreateOlapReport() {
            OlapReport olapReport = new OlapReport();
            olapReport.CurrentCubeName = "Adventure Works";

            MeasureElements measureElement = new MeasureElements();
            measureElement.Elements.Add(new MeasureElement {
                UniqueName = "[Measures].[Internet Sales Amount]"
            });

            DimensionElement dimensionElementRow = new DimensionElement();
            dimensionElementRow.Name = "Date";
            dimensionElementRow.AddLevel("Fiscal", "Fiscal Year");

            DimensionElement dimensionElementColumn = new DimensionElement();
            dimensionElementColumn.Name = "Customer";
            dimensionElementColumn.AddLevel("Customer Geography", "Country");

            olapReport.SeriesElements.Add(dimensionElementRow);
            olapReport.CategoricalElements.Add(dimensionElementColumn);
            olapReport.CategoricalElements.Add(measureElement);

            return olapReport;
        }

    }
}

{% endhighlight %}

**Configure routing in Global Application Class**

If Global.asax file is not found in your MVC Web Application then add a new one. To add a **Global.asax** in your existing MVC Web Application, right-click on the project in Solution Explorer and select **Add > New Item**. In the **Add New Item** window, select **Global Application Class** and name it as `Global.asax`, click **Add.**
 
Once the Global.asax file is created, remove all the existing code inside the "Application_Start" function. Then routing could be configured as shown in the following code example.

{% highlight c# %}

public class Global: System.Web.HttpApplication {
    protected void Application_Start(object sender, EventArgs e) {
        System.Web.Http.GlobalConfiguration.Configuration.Routes.MapHttpRoute(
            name: "DefaultApi",
            routeTemplate: "{controller}/{action}/{id}",
            defaults: new {
                id = RouteParameter.Optional
            });
        AppDomain.CurrentDomain.SetData("SQLServerCompactEditionUnderWebHosting", true);
    }
}

{% endhighlight %}

Now, **PivotGrid** is rendered with Customer Count over a period of fiscal years across different customer geographic locations.

![](Getting-Started_images/olapwebapi.png) 

### WCF

This section demonstrates the utilization of WCF service as endpoint binding OLAP datasource to a simple PivotGrid. For more details on this topic, [click here](http://help.syncfusion.com/aspnetmvc/PivotGrid/olap-connectivity#wcf).


