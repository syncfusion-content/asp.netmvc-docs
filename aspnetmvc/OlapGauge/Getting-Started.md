---
layout: post
title: Getting Started | OLAPGauge | ASP.NET MVC | Syncfusion
description: getting started 
platform: ejmvc
control: OLAPGauge
documentation: ug
---

# Getting Started

## Creating a simple application with OlapGauge.

This section covers the information required to create a simple OlapGauge bound to OLAP datasource.

>**NOTE: ASP.NET MVC Web Application will contain a service that transfers data to server-side, processes and returns them back to client-side for control rendering and re-rendering. The service utilized for communicate could be either WCF or WebAPI based on users requirement.**

###Project Initialization

Create a new **ASP.NET MVC Web Application** using Visual Studio IDE and name the project as **“OlapGaugeDemo”**. 

Select the View engine as **‘Razor’** and Project template as **‘Internet Application’** and finally click **OK** button to create an application.

Now add the following dependency libraries as references into your MVC Web Application. In order to add them to your application, right-click on **References** in Solution Explorer and select Add Reference. Now in the **Reference Manager** dialog, under **Assemblies > Extension**, the following Syncfusion libraries will be found.  

* Microsoft.AnalysisServices.AdomdClient.dll
* Syncfusion.Linq.Base.dll
* Syncfusion.Olap.Base.dll
* Syncfusion.EJ.dll
* Syncfusion.EJ.Olap.dll
* Syncfusion.EJ.MVC.dll

N> If any version of SQL Server Analysis Service (SSAS) or Microsoft ADOMD.NET utility is installed, then the location of Microsoft.AnalysisServices.AdomdClient library is [system drive:\Program Files (x86)\Microsoft.NET\ADOMD.NET].

The version of Syncfusion libraries based on .NET framework and MVC version are classified below. For example, 13.3 version is illustrated as,

<table>
<tr>
<th>
MVC Version</th><th>
MVC Version of Syncfusion dlls</th><th>
Base Version of Syncfusion dlls</th><th>
System.Web.Mvc</th><th>
System.Web.WebPages</th>
</tr>
<tr><td>
MVC3</td><td>
12.1300.0.43</td><td>    
12.1350.0.43</td><td>
3.0</td><td>
1.0</td>
</tr>
<tr><td>
MVC4</td><td>
12.1400.0.43</td><td>    
12.1400.0.43</td><td>
4.0</td><td>
2.0</td>
</tr>
<tr><td>
MVC5</td><td>
12.1500.0.43</td><td>    
12.1450.0.43</td><td>
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
        <add assembly="Syncfusion.EJ, Version= 13.3400.0.7, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.EJ.Olap, Version= 13.3400.0.7, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.EJ.Mvc, Version= 13.3400.0.7, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.Linq.Base, Version= 13.3400.0.7, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.Olap.Base, Version= 13.3400.0.7, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" /> 
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

Set the “UnobtrusiveJavaScriptEnabled” property to false under <appSettings> tag in Web.config file at the root folder.
    
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


###Scripts and CSS Initialization

he scripts and style sheets that are mandatorily required to render OlapChart widget in a MVC Web Application are mentioned in an appropriate order below:

1.  ej.widgets.all.min.css
2.	jquery-1.10.2.min.js
3.	jquery.easing.1.3.min.js
4.	ej.web.all.min.js 

[Click here](http://help.syncfusion.com/js/cdn) here to know more about scripts and style sheets available online (CDN Link).

Scripts and style sheets are referred under the <head> tag in **_Layout.cshtml** file which is found inside **Views > Shared folder.**
    
{% highlight html %}

<head>
    <link href="http://cdn.syncfusion.com/13.3.0.7/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
    <script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js" type="text/javascript"> </script>
    <script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js" type="text/javascript"> </script>
    <script src="http://cdn.syncfusion.com/13.3.0.7/js/web/ej.web.all.min.js"> </script>
</head>

{% endhighlight %}

The script manager is initialized immediately after the `RenderBody()` function call in **_Layout.cshtml** file in-order to generate widget related scripts.

{% highlight html %}

<body> 
  	…… 
    …… 
    @RenderBody() @(Html.EJ().ScriptManager()) 
</body>

{% endhighlight %}

### Control Initialization

Before initializing, empty the contents of **Index.cshtml** file under **Views > Home** folder and add the following codes. Register the namespaces at the top of the page and then add the control.

{% highlight html %}
    
@using Syncfusion.JavaScript.Olap;

<div> 
      @Html.EJ().Olap().OlapGauge("OlapGauge1").Url(Url.Content("~/api/OlapGauge")).IsResponsive(true).BackgroundColor("transparent").EnableTooltip(true).Scales(scale =>
 {
     scale.ShowRanges(true).Radius(150).ShowScaleBar(true).Size(1).Border(bor => bor.Width(0.5)).ShowIndicators(true).ShowLabels(true).
     Pointers(pointer =>
     {
         pointer.ShowBackNeedle(true).BackNeedleLength(20).Length(120).Width(7).Add();
         pointer.Type(PointerType.Marker).DistanceFromScale(5).Placement(PointerPlacement.Center).BackgroundColor("#29A4D9").Length(25).Width(15).MarkerType(MarkerType.Diamond).Add();
     }).
     Ticks(ticks =>
     {
         ticks.Type(CircularTickTypes.Major).DistanceFromScale(2).Height(16).Width(1).Color("#8c8c8c").Add();
         ticks.Type(CircularTickTypes.Minor).Height(6).Width(1).DistanceFromScale(2).Color("#8c8c8c").Add();
     }).Labels(labels =>
     {
         labels.Color("#8c8c8c").Add();
     }).Ranges(ranges =>
     {
         ranges.DistanceFromScale(-5).BackgroundColor("#fc0606").Border(bor => bor.Color("#fc0606")).Add();
         ranges.DistanceFromScale(-5).Add();
     }).CustomLabels(customLabel =>
     {
         customLabel.Position(location => location.X(180).Y(290)).Font(font => font.Size("10px").FontFamily("Segoe UI").FontStyle("Normal")).Color("#666666").Add();
         customLabel.Position(location => location.X(180).Y(320)).Font(font => font.Size("10px").FontFamily("Segoe UI").FontStyle("Normal")).Color("#666666").Add();
         customLabel.Position(location => location.X(180).Y(150)).Font(font => font.Size("12px").FontFamily("Segoe UI").FontStyle("Normal")).Color("#666666").Add();
     }).Add();
 }).ClientSideEvents(oCli =>{oCli.RenderSuccess("loadOLAPGaugeTheme");})
</div>

{% endhighlight %}

The **“Url”** property in OlapGauge widget points the service endpoint, where data are processed and fetched in the form of JSON. The services used in OlapGauge widget as endpoint are WCF and WebAPI.

N> The above "Index.cshtml" contains WebAPI Url, which is, "~/OlapGauge". If WCF service is used as endpoint, the Url would look like "~/OlapGaugeService.svc".


###WebAPI

**Adding a WebAPI Controller**

To add a WebAPI controller in an existing Web Application, right-click on the project in Solution Explorer and select **Add > New Item**. In the **Add New Item** window, select **WebAPI Controller Class** and name it as `OlapGaugeController.cs`, click Add.

Now, WebAPI controller is added to the application successfully containing the file **“OlapGaugeController.cs”**.

N> While adding WebAPI Controller Class, name it with the suffix ‘Controller’ that is mandatory. For example, in this demo the controller is named as “OlapGaugeController”.

Next, remove all the existing methods such as “Get”, “Post”, “Put” and “Delete” present inside `OlapGaugeController.cs` file.

{% highlight c# %}

namespace OlapGaugeDemo
{
    public class OlapGaugeController: ApiController
    {
    
    }
}

{% endhighlight %}

**Adding the List of Namespaces**

The following are the list of namespaces to be added on top of the main class inside `OlapGaugeController.cs` file.

{% highlight c# %}

using Syncfusion.JavaScript.Olap;
using Syncfusion.Olap.Manager;
using Syncfusion.Olap.Reports;
using System;
using System.Collections.Generic;
using System.Configuration;
using System.Linq;
using System.Net;
using System.Net.Http;
using System.Web.Http;
using System.Web.Script.Serialization;

namespace OlapGaugeDemo
{
    public class OlapGaugeController: ApiController
    {
    
    }
}

{% endhighlight %}

**Datasource Initialization**

Now, the connection string to connect OLAP Cube, OlapGauge and JavaScriptSerializer instances are created immediately inside the main class in OlapGaugeController.cs file.

{% highlight c# %}

namespace OlapGaugeDemo
{
    public class OlapGaugeController: ApiController
    {
        OlapGauge htmlHelper = new OlapGauge();
        string connectionString = "Data Source=http://bi.syncfusion.com/olap/msmdpump.dll; Initial Catalog=Adventure Works DW 2008 SE;";
        JavaScriptSerializer serializer = new JavaScriptSerializer();
        ……
        ……
    }
}

{% endhighlight %}

**Service methods in WebAPI Controller**

Define the service methods inside OlapGaugeController class, found inside `OlapGaugeController.cs` file, created while adding WebAPI Controller Class to the Application.

{% highlight c# %}

namespace OlapGaugeDemo
{
    public class OlapGaugeController: ApiController
    {
        OlapGauge htmlHelper = new OlapGauge();
        string connectionString = "Data Source=http://bi.syncfusion.com/olap/msmdpump.dll; Initial Catalog=Adventure Works DW 2008 SE;";
        JavaScriptSerializer serializer = new JavaScriptSerializer();
        [System.Web.Http.ActionName("InitializeGauge")]
        [System.Web.Http.HttpPost]
        public Dictionary < string, object > InitializeGauge(Dictionary < string, object > jsonResult)
        {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(CreateOlapReport());
            return htmlHelper.GetJsonData(jsonResult["action"].ToString(), DataManager);
        }
        private OlapReport CreateOlapReport()
        {
            OlapReport report = new OlapReport();
            report.CurrentCubeName = "Adventure Works";
            KpiElements kpiElement = new KpiElements();
            kpiElement.Elements.Add(new KpiElement
            {
                Name = "Internet Revenue", ShowKPIGoal = true, ShowKPIStatus = true, ShowKPIValue = true, ShowKPITrend = true
            });
            DimensionElement dimensionElementColumn = new DimensionElement();
            dimensionElementColumn.Name = "Customer";
            dimensionElementColumn.AddLevel("Customer Geography", "Country");
            MeasureElements measureElementColumn = new MeasureElements();
            measureElementColumn.Elements.Add(new MeasureElement
            {
                Name = "Internet Sales Amount"
            });
            DimensionElement dimensionElementRow = new DimensionElement();
            dimensionElementRow.Name = "Date";
            dimensionElementRow.AddLevel("Fiscal", "Fiscal Year");
            dimensionElementRow.Hierarchy.LevelElements["Fiscal Year"].Add("FY 2004");
            dimensionElementRow.Hierarchy.LevelElements["Fiscal Year"].IncludeAvailableMembers = true;
            report.CategoricalElements.Add(dimensionElementColumn);
            report.CategoricalElements.Add(kpiElement);
            report.CategoricalElements.Add(measureElementColumn);
            report.SeriesElements.Add(dimensionElementRow);
            return report;
        }
    }
}

{% endhighlight %}

**Configure routing in Global Application Class**

If Global.asax file is not found in your MVC Web Application then add a new one. To add a **Global.asax** in your existing MVC Web Application, right-click on the project in Solution Explorer and select **Add > New Item**. In the **Add New Item** window, select **Global Application Class** and name it as “Global.asax”, click **Add.**
 
Once the Global.asax file is created, remove all the existing code inside the “Application_Start” function. Then routing could be configured as shown in the following code example.

{% highlight c# %}

public class Global: System.Web.HttpApplication
{
    protected void Application_Start(object sender, EventArgs e)
    {
        GlobalConfiguration.Configuration.Routes.MapHttpRoute(name: "DefaultApi", routeTemplate: "{controller}/{action}/{id}", defaults: new
        {
            id = RouteParameter.Optional
        });
        AppDomain.CurrentDomain.SetData("SQLServerCompactEditionUnderWebHosting", true);
        RouteConfig.RegisterRoutes(RouteTable.Routes);
    }
}

{% endhighlight %}

Now, **OlapGauge** is rendered with Internet Revenue for Internet Sales Amount over a Fiscal Year 2004 across different customer geographic locations.

![](Getting-Started_images/OlapGauge.png) 

###WCF

This section demonstrates the utilization of WCF service as endpoint binding OLAP datasource to a simple OlapGauge. For more details on this topic, [click here](http://help.syncfusion.com/aspnetmvc/olapgauge/data-binding#wcf).

