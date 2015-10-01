---
layout: post
title: Getting-Started
description: getting started
platform: ejmvc
control: OLAPChart
documentation: ug
---

# Getting Started

This section briefly explains how you can create an OLAP Chart in your application with ASP.NET MVC.

## Create your first OLAP Chart in MVC

## Control structure

The following screenshot displays OLAP Chart for Asp.Net MVC.



![](Getting-Started_images/Getting-Started_img1.png)



## Syncfusion OLAP Controls – Architecture


![](Getting-Started_images/Getting-Started_img2.png)



The architecture gives you a clear idea on how the control rendering takes place at client-side and all other analytical operations on each action takes place at server-side.

## Service for OLAP Controls

### The primary reasons for using service in an OLAP processing are as follows:

DataSource Connectivity: You  can establish a connection between different cube data sources such as

1. Offline Cube
2. Online Cube (XML/A)
3. Cube within SQL Server, locally or through remote, you can move the connectivity related coding to service-side as it is impossible at client-side other than Online Cube (XML/A) option. Using service you can connect any type of cube data source without any limitation.

Cube Schema: As the connection is moved to service side, you obviously use Microsoft__ADOMD__assembly, to get the entire cube schema. Only with the cube schema the following details are achieved for control rendering.

1. Availability of cubes.
2. A complete end-to-end detail such as name, caption, unique name, parent information, child information, its properties etc. about the dimension, hierarchy, level, members are available in cube schema only. 
3. Localized information is also available in cube schema.  

MDX Generator:  You can frame the MDX query using a  MDX generator in Syncfusion.Olap.Base assembly. To execute the framed MDX from the cube data source, you need to sent framed MDX via Microsoft__ADOMD__assembly_._ The executed query is returned back in the form of cell set (contains values) that is converted to Pivot Engine and then to JSON data to render any OLAP controls.

OLAP Report: The OlapReport class in the Syncfusion.Olap.Base assembly holds the complete information about each axes such as column, row and slicer. Using OlapReport class you can maintain the dimension element, measure element, hierarchy name, level name as well as members information that is included and excluded.

As the OlapControl is the key for each and every operation, initially you need to serialize the OlapReport and send to client-side in a form of string.

When you perform any operation such as drill up or down, filtering, sorting etc., you need to send OlapReport from the client-side to the service in a de-serialized and updated format.Further operations are carried with updated OlapReports only and you can send the updated OlapReport back to client-side with JSON data in a serialized format again. 

This process has the OlapReport always updated. You cannot operate serialized OlapReport in client-side and hence it is carried to service having its class in Syncfusion.Olap.Base assembly to perform the update operation_._

## Create an application

This section encompasses on how to configure the OLAP Chart component in an application. You can also learn how to pass the required data to OLAP Chart and to customize its various options according to your requirements. 

In the following example, the OLAP Chart component displays the customer count over different fiscal years against various geographical locations. This helps you to analyze the summarized data over different fiscal years.

![](Getting-Started_images/Getting-Started_img3.png)



Open Visual Studio and create a new project using by clicking New Project. Select the category Web and select the ASP.NET MVC4 Web Application template, and then click OK.

The following screenshot displays the Project Creation Wizard.

![](Getting-Started_images/Getting-Started_img4.png)


The following screenshot displays how to select Internet application template with razor view engine.

![](Getting-Started_images/Getting-Started_img5.png)



## Add References, Scripts, Styles and Control

### Add References

In the Solution Explorer, right-click the References folder, then click Add Reference.

![](Getting-Started_images/Getting-Started_img6.png)



The following screenshot illustrates how to reference Syncfusion.Olap.Base.

![](Getting-Started_images/Getting-Started_img7.png)



## Select the following assemblies: 

* Microsoft.AnalysisServices.AdomdClient.dll,
* Syncfusion.Linq.Base.dll
* Syncfusion.EJ.dll
* Syncfusion.EJ.MVC.dll 
* Syncfusion.EJ.Olap.dll 
* Syncfusion.Olap.Base.dll
* Syncfusion.Pdf.Base.dll
* Syncfusion.XlsIO.Base.dll
* Syncfusion.DocIO.dll

Click OK.

### Add Scripts and Styles

1. Add the script files and CSS files in the head tag of the _Layout.cshtml page.

   N> 
   >
   > 1. Follow the given order while adding scripts and styles.
   > 2. Apart from the cdn files rest of them can be acquired from the following location
   > C:\Users\<UserName>\AppData\Local\Syncfusion\EssentialStudio\<Version>\JavaScript\assets\

   ~~~ html

		<head>

		<link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
		<script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js" type="text/javascript"> </script>
		<script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js" type="text/javascript"> </script>
		<script src="http://cdn.syncfusion.com/js/assets/external/jquery.globalize.min.js"> </script>
		<script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js"> </script>

		</head>

   ~~~
   {:.prettyprint }



2. Add the following code example in the body tag of the _Layout.cshtml page.

   ~~~ html

		<body>
		   @RenderBody()
		   @Html.EJ().ScriptManager()   
		</body>

   ~~~
   {:.prettyprint }


### Add Control in View page

Add the following code example in the Index.cshtml page that is already created.
{% highlight html %}

@using Syncfusion.JavaScript;
@using Syncfusion.JavaScript.Olap;
@using Syncfusion.JavaScript.DataVisualization;

<div>

@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")).Size(size => size.Height("460px").Width("950px")) </div> 
{% endhighlight %}

## Add WCF service for OLAP Chart

### Creating WCF Services

1. Right-click the project and select Add>New Folder.  Name the folder as wcf. Let the folder name "wcf" be in lower case.
2. Now right-click the wcf folder created and select Add > New Item.  In the Add New Item window, select WCF Service and name it OlapChartService.svc
3. Click Add. 

![](Getting-Started_images/Getting-Started_img9.png)



### Add service methods inside Interface

Add the following code example inside the IOlapChartService interface available in the IOlapChartService.cs file.
{% highlight c# %}



public interface IOlapChartService
{
    [OperationContract] 
    Dictionary<string, object> InitializeChart(string action, string customObject);
                        
    [OperationContract] 
    Dictionary<string, object> DrillChart(string action, string drilledSeries, string olapReport, string customObject);
        
    [OperationContract]
    void Export(System.IO.Stream stream);
}
{% endhighlight %}

### Add Namespaces

Add the following namespaces required to implement the service methods.
{% highlight c# %}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Runtime.Serialization;
using System.ServiceModel;
using System.Text;
using System.ServiceModel.Activation;
using Syncfusion.Olap.Manager;
using Syncfusion.Olap.Reports;
using Syncfusion.JavaScript.Olap;
using System.Web.Script.Serialization;
{% endhighlight  %}

### Create Class in Service file

Create the OlapChartService class to implement the service methods. Inherit the class from the IOlapChartService interface that is created automatically when any new service is added.
{% highlight c# %}

namespace MvcApplication1.wcf
{
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class OlapChartService : IOlapChartService
    {

    }
}

{% endhighlight %}

### Implement Service Methods

Add the following methods to the service that is invoked for any server-side operations performed in OlapChart.

1. Initialize the OlapCharts helper class and OlapDataManager with appropriate connection string.

   ~~~ cs
   
    JavaScriptSerializer serializer = new JavaScriptSerializer();
    OlapChart htmlHelper = new OlapChart();        
    static string connectionString = "Data Source=http://bi.syncfusion.com/olap/msmdpump.dll; Initial Catalog=Adventure Works DW 2008 SE;";   
    OlapDataManager DataManager = new OlapDataManager(connectionString);

   ~~~
   {:.prettyprint }


2. Initialize the following service methods.

   ~~~ cs

    //This method provides the required information from server-side for initializing the OlapChart.
    public Dictionary<string, object> InitializeChart(string action, string customObject)
    {
        OlapDataManager DataManager = null;
        dynamic customData = serializer.Deserialize<dynamic>(customObject.ToString());
        DataManager = new OlapDataManager(connectionString); 
        DataManager.SetCurrentReport(CreateOlapReport());
        return htmlHelper.GetJsonData(action, DataManager);
    }
    
    //This method provides the required information from server-side while drill up or down operation is performed in OlapChart.
    public Dictionary<string, object> DrillChart(string action, string drilledSeries, string olapReport, string customObject)
    {
        DataManager.SetCurrentReport(Utils.DeserializeOlapReport(olapReport)); 
        dynamic customData = serializer.Deserialize<dynamic>(customObject.ToString());            
        return htmlHelper.GetJsonData(action, DataManager, drilledSeries);
    }
    //This method exports OlapChart to Excel, Word and PDF.
    public void Export(System.IO.Stream stream)
    {
        System.IO.StreamReader sReader = new System.IO.StreamReader(stream);
        string args = System.Web.HttpContext.Current.Server.UrlDecode(sReader.ReadToEnd());
        OlapDataManager DataManager = new OlapDataManager(connectionString);
        string fileName = "Sample";
        htmlHelper.ExportOlapChart(DataManager, args, fileName, System.Web.HttpContext.Current.Response);
    }
    
    //This method carries the information about the default report that would be rendered within OlapChart initially. 
    private OlapReport CreateOlapReport()
    {
        OlapReport olapReport = new OlapReport();
        olapReport.Name = "Default Report";
        olapReport.CurrentCubeName = "Adventure Works";
        DimensionElement dimensionElementColumn = new DimensionElement();
        dimensionElementColumn.Name = "Customer";
        dimensionElementColumn.AddLevel("Customer Geography", "Country");
        MeasureElements measureElementColumn = new MeasureElements();
        measureElementColumn.Elements.Add(new MeasureElement { Name = "Customer Count" });
        DimensionElement dimensionElementRow = new DimensionElement();
        dimensionElementRow.Name = "Date";
        dimensionElementRow.AddLevel("Fiscal", "Fiscal Year");
        olapReport.SeriesElements.Add(dimensionElementRow);
        olapReport.CategoricalElements.Add(dimensionElementColumn);
        olapReport.CategoricalElements.Add(measureElementColumn);
        return olapReport;
    }  
			
   ~~~
   {:.prettyprint }


### Configure Web.Config

1. Register the assemblies by adding the following code example inside the <system.web> tag in web.config file at the root folder.

   ~~~ html

	<compilation debug="true" targetFramework="4.5">
	   <assemblies>
		  <add assembly="System.Web.Abstractions, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />
		  <add assembly="System.Web.Helpers, Version=2.0.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />
		  <add assembly="System.Web.Routing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />
		  <add assembly="System.Web.Mvc, Version= X.X.X.X, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />
		  <add assembly="System.Web.WebPages, Version= X.X.X.X, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />
		  <add assembly="Syncfusion.EJ, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
		  <add assembly="Syncfusion.EJ.Olap, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
		  <add assembly="Syncfusion.EJ.Mvc, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
		  <add assembly="Syncfusion.Linq.Base, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
		  <add assembly="Syncfusion.Olap.Base, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
          <add assembly="Syncfusion.Pdf.Base, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
          <add assembly="Syncfusion.XlsIO.Base, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
          <add assembly="Syncfusion.DocIO.Base, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
		</assemblies>
	</compilation>


   ~~~
   {:.prettyprint }


   N> x.x.x.x in the above code example refers to the current version of the Essential Studio running in your system.

   #### The version of Syncfusion dlls according to the .NET framework and MVC version are as follows.  For example, 12.1 version is illustrated here.

   _Table: List of MVC versions_

   <table>
   <tr>
   <th>
   MVC Version</th><th>
   MVC Version of Syncfusion dlls</th><th>
   Base Version of Syncfusion dlls</th><th>
   System.Web.Mvc</th><th>
   System.Web.WebPages</th></tr>
   <tr>
   <td>
   MVC3</td><td>
   12.1300.0.43</td><td>
   12.1350.0.43</td><td>
   3.0</td><td>
   1.0</td></tr>
   <tr>
   <td>
   MVC4</td><td>
   12.1400.0.43</td><td>
   12.1400.0.43</td><td>
   4.0</td><td>
   2.0</td></tr>
   <tr>
   <td>
   MVC5</td><td>
   12.1500.0.43</td><td>
   12.1450.0.43</td><td>
   5.0</td><td>
   3.0</td></tr>
   </table>


2. Add the following namespaces to the web.config files in root folder and View folder.

   ~~~ html

	<namespaces>
	   <add namespace="System.Web.Helpers" />
	   <add namespace="System.Web.Mvc" />
	   <add namespace="System.Web.Mvc.Ajax" />
	   <add namespace="System.Web.Mvc.Html" />
	   <add namespace="System.Web.Optimization" />
	   <add namespace="System.Web.Routing" />
	   <add namespace="System.Web.WebPages" />
	   <add namespace="Syncfusion.MVC.EJ"/>
       <add namespace="Syncfusion.JavaScript"/>
	   <add namespace="Syncfusion.JavaScript.DataVisualization"/>
	</namespaces>

   ~~~
   {:.prettyprint }

3. Register the wcf services endpoint in web.config file in root folder by adding the following code examples.
4. You can expose services through the properties such as binding, contract and address etc. using an endpoint.  In your application the service name is "MvcApplication1.wcf.OlapChartService" where "OlapChartService" is the service class name and “MvcApplication1.wcf" is the namespace name where the service class appears.

   The following are the properties that meet the appropriate endpoint.  

   * contract: This property indicates the contract that the endpoint is exposing. Here you are referring IOlapChartService contract and it is "MvcApplication1.wcf.IOlapChartService".
   * binding: In your application, you can use webHttpBinding to post and receive the requests and responses between the client-end and the service-end.
   * behaviorConfiguration: This property contains the name of the behavior to be used in the endpoint. endpointBehaviors are illustrated as follows.

   ~~~ html

		<system.serviceModel>
			<services>
			  <service name="MvcApplication1.wcf.OlapChartService">
				<endpoint address="" behaviorConfiguration="MvcApplication1.wcf.OlapChartServiceAspNetAjaxBehavior"
				  binding="webHttpBinding" contract="MvcApplication1.wcf.IOlapChartService" />
			  </service>
			</services>
		</system.serviceModel>

   ~~~
   {:.prettyprint }

5. The endpointBehaviors contain all the behaviors for an endpoint. You can link each endpoint to the respective behavior only using this name property. In the following code example "MvcApplication1.wcf.OlapChartServiceAspNetAjaxBehavior" refers to the OlapChartService class under the namespace MvcApplication1.wcf in OlapChartService.svc.cs file which is the appropriate behavior for the endpoint. 

   ~~~ html

		<system.serviceModel>
			<behaviors>
			  <endpointBehaviors>
				<behavior name="MvcApplication1.wcf.OlapChartServiceAspNetAjaxBehavior">
				  <enableWebScript />
				</behavior>
			  </endpointBehaviors>
			</behaviors>    
		</system.serviceModel>

   ~~~
   {:.prettyprint }



   N> In this example, “MvcApplication1.wcf” indicates the namespace in the WCF Service and “OlapChartService” indicates the class name in the WCF Service.



6. Set the UnobtrusiveJavaScriptEnabled value as false under appSettings tag as illustrated in the following code example.

   ~~~ html

		<appSettings>
			<add key="webpages:Version" value="2.0.0.0" />
			<add key="webpages:Enabled" value="false" />
			<add key="PreserveLoginUrl" value="true" />
			<add key="ClientValidationEnabled" value="true" />
			<add key="UnobtrusiveJavaScriptEnabled" value="false" />
		</appSettings>
		
   ~~~
   {:.prettyprint }

### Configuring routing file

Add the following highlighted line in RouteConfig.cs file to avoid issues when picking the WCFservice methods.
{% highlight c# %}


public class RouteConfig
{
    public static void RegisterRoutes(RouteCollection routes)
    {
        routes.IgnoreRoute("{resource}.axd/{*pathInfo}");
        //NOTE: In the below highlighted lines _wcf_ is just the folder name inside which service files(*.svc) are present.
        routes.IgnoreRoute("wcf/{resource}.svc/{*pathInfo}"); 
        routes.IgnoreRoute("wcf/{resource}.svc");
        routes.MapRoute(
            name: "Default",
            url: "{controller}/{action}/{id}",
            defaults: new { controller = "Introduction", action = "Index", id = UrlParameter.Optional },
            namespaces: new[] { "MvcApplication1.wcf.Controllers" }
        );
    }
}

{% endhighlight %}

![](Getting-Started_images/Getting-Started_img12.png)

