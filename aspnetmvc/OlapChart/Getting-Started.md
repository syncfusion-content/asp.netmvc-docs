---
layout: post
title: Getting-Started
description: getting started
platform: ejmvc
control: OLAP Chart
documentation: ug
---

# Getting Started

This section explains briefly about how to create an OLAP Chart in your application with ASP.NET MVC.

## Create your first OLAP Chart in MVC

Control structure

The following screen shot shows the OLAP Chart for Asp.Net MVC.



{{ '![C:/Users/Narendhran Muthuvel/Desktop/NewChart.png](Getting-Started_images/Getting-Started_img1.png)' | markdownify }}
{:.image }


Syncfusion OLAP Controls – Architecture


{{ '![C:/Users/Narendhran Muthuvel/Desktop/blockdiagram.PNG](Getting-Started_images/Getting-Started_img2.png)' | markdownify }}
{:.image }


The architecture gives a clear idea about how the control rendering takes place at client-side and all other analytical operations on each action takes place at server-side.

Service for OLAP Controls

The primary reasons for using service in an OLAP processing are as follows:

DataSource Connectivity: You  can establish a connection between different cube data sources such as

1. Offline Cube
2. Online Cube (XML/A)
3. Cube within SQL Server (locally or through remote), you can move the connectivity related coding to service-side as it is impossible at client-side other than Online Cube (XML/A) option. Using service you can connect any type of cube data source without any limitation.

Cube Schema: As the connection is moved to service side, you obviously use Microsoft__ADOMD__assembly, to get the entire cube schema. Only with the cube schema the following details are achieved for control rendering.

1. Availability of cubes.
2. A complete end-to-end detail such as name, caption, unique name, parent information, child information, its properties etc. about the dimension, hierarchy, level, members are available in cube schema only. 
3. Localized information is also available in cube schema.  

MDX Generator:  You can frame the MDX query using a  MDX generator in Syncfusion.Olap.Base assembly. To execute the framed MDX from the cube data source, you need to sent framed MDX via Microsoft__ADOMD__assembly_._ The executed query is returned back in the form of cell set (contains values) that is converted to Pivot Engine and then to JSON data to render any OLAP controls.

OLAP Report: The OlapReport class in the Syncfusion.Olap.Base assembly holds the complete information about each axes such as column, row and slicer. Using OlapReport class you can maintain the dimension element, measure element, hierarchy name, level name as well as members information that is included and excluded.

As the OlapControl is the key for each and every operation, initially you need to serialize the OlapReport and send to client-side in a form of string.

When you perform any operation such as drill up/down, filtering, sorting etc., you need to send OlapReport from the client-side to the service in a de-serialized and updated format.Further operations are carried with updated OlapReports only and you can send the updated OlapReport back to client-side with JSON data in a serialized format again. 

This process has the OlapReport always updated. You cannot operate serialized OlapReport in client-side and hence it is carried to service having its class in Syncfusion.Olap.Base assembly to perform the update operation_._

Create an application

This section encompasses on how to configure the OLAP Chart component in an application. You can also learn how to pass the required data to OLAP Chart and to customize its various options according to your requirements. 

In the following example, the OLAP Chart component displays the customer count over different fiscal years against various geographical locations. This helps you to analyze the summarized data over different fiscal years.

{{ '![](Getting-Started_images/Getting-Started_img3.png)' | markdownify }}
{:.image }


Open Visual Studio and create a new project using by clicking New Project. Select the category Web and select the ASP.NET MVC4 Web Application template, and then click OK.

The following screen shot displays the Project Creation Wizard.

{{ '![C:/Users/Narendhran Muthuvel/Desktop/screenshots/sshot-3.png](Getting-Started_images/Getting-Started_img4.png)' | markdownify }}
{:.image }






The following screen shot displays how to select Internet application template with razor view engine.

{{ '![C:/Users/Narendhran Muthuvel/Desktop/screenshots/sshot-1.png](Getting-Started_images/Getting-Started_img5.png)' | markdownify }}
{:.image }


Add References, Scripts, Styles and Control

Add References

In the Solution Explorer, right click the References folder, then click Add Reference.

{{ '![C:/Users/Narendhran Muthuvel/Desktop/screenshots/sshot-2.png](Getting-Started_images/Getting-Started_img6.png)' | markdownify }}
{:.image }


The following screen shot illustrates how to reference Syncfusion.Olap.Base.

{{ '![C:/Users/Narendhran Muthuvel/Desktop/screenshots/sshot-4.png](Getting-Started_images/Getting-Started_img7.png)' | markdownify }}
{:.image }


Select the following assemblies: 

* Microsoft.AnalysisServices.AdomdClient.dll,
* Syncfusion.Core.dll
* Syncfusion.Linq.Base.dll
* Syncfusion.EJ.dll
* Syncfusion.EJ.MVC.dll 
* Syncfusion.EJ.Olap.dll 
* Syncfusion.Olap.Base.dll

Click OK.

Add Scripts and Styles

1. Add the script files and CSS files in the head tag of the _Layout.cshtml page.

{{ '![](Getting-Started_images/Getting-Started_img8.jpeg)' | markdownify }}
{:.image }
_Note: 1. Please follow the following order while adding scripts and styles._

>    _2. Apart from cdn files rest of them can be acquired from the following location_

> _C:\Users\<UserName>\AppData\Local\Syncfusion\EssentialStudio\<Version>\JavaScript\assets\_

[CSHTML]



<head>

<link href="http://cdn.syncfusion.com/13.1.0.21/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />

<script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js" type="text/javascript"> </script>

<script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js" type="text/javascript"> </script>

<script src="http://cdn.syncfusion.com/js/assets/external/jquery.globalize.min.js"> </script>

<script src="http://cdn.syncfusion.com/13.1.0.21/js/web/ej.web.all.min.js"> </script>

</head>





2. Add the following code example in the body tag of the _Layout.cshtml page.

[CSHTML]

<body>

   @RenderBody()

   @Html.EJ().ScriptManager()   

</body>





Add Control in View page

Add the following code example in the Index.cshtml page that is already created.

[CSHTML]

@using Syncfusion.JavaScript;

@using Syncfusion.JavaScript.Olap;

@using Syncfusion.JavaScript.DataVisualization;



<div>

@Html.EJ().Olap().OlapChart("OlapChart1").Url(Url.Content("~/wcf/OlapChartService.svc")) </div> 

Add WCF service for OLAP Chart

Creating WCF Services

1. Right click the project and select Add>New Folder.  Name the folder as _wcf_.
2. Now right-click the _wcf_ folder created and select Add > New Item.  In the Add New Item window, select WCF Service and name it OlapChartService.svc
3. Click Add. 

{{ '![C:/Users/Narendhran Muthuvel/Desktop/screenshots/sshot-10.png](Getting-Started_images/Getting-Started_img9.png)' | markdownify }}
{:.image }


Add service methods inside Interface

Add the following code sample inside the IOlapChartService interface available in the IOlapChartService.cs file.

[C#]

    [ServiceContract]

    public interface IOlapChartService

    {

        [OperationContract]

        Dictionary<string, object> InitializeChart(string action, string customObject);                [OperationContract]

        Dictionary<string, object> DrillChart(string action, string drilledSeries, string olapReport, string customObject);

    }

Add Namespaces

Add the following necessary namespaces to implement the service methods.

[C#]

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

Create Class in Service file

Create the OlapChartService class to implement the service methods. Inherit the class from the IOlapChartService interface that is created automatically when any new service is added.

[C#]

namespace MvcApplication1

{

    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]

    public class OlapChartService : IOlapChartService

    {

    }

}

Implement Service Methods

Add the following methods to the service that is invoked for any server-side operations performed in OlapChart.

1. Initialize the OlapCharts helper class and OlapDataManager with appropriate connection string.


[C#]

JavaScriptSerializer serializer = new JavaScriptSerializer();

OlapChart htmlHelper = new OlapChart();        

static string connectionString = "Data Source=http://bi.syncfusion.com/olap/msmdpump.dll; Initial Catalog=Adventure Works DW 2008 SE;";   

OlapDataManager DataManager = new OlapDataManager(connectionString);





2. Initialize the following service methods.

[C#]



//This method provides the required information from the server side for initializing the OlapChart.

         public Dictionary<string, object> InitializeChart(string action, string customObject)

        {

            OlapDataManager DataManager = null;

            dynamic customData =     serializer.Deserialize<dynamic>(customObject.ToString());

                DataManager = new OlapDataManager(connectionString); 

            DataManager.SetCurrentReport(CreateOlapReport());

            return htmlHelper.GetJsonData(action, DataManager);

        }



//This method provides the required information from the server side while drill up/down operation is performed in OlapChart.

        public Dictionary<string, object> DrillChart(string action, string drilledSeries, string olapReport)

        {

            DataManager.SetCurrentReport(Utils.DeserializeOlapReport(olapReport)); 

dynamic customData = serializer.Deserialize<dynamic>(customObject.ToString());            

            return htmlHelper.GetJsonData(action, DataManager, drilledSeries);

        }



//This method carries the information about the default report which would be rendered within OlapChart initially. 

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





Configure Web.Config

1. Register the assemblies by adding the following code example inside the <system.web> tag in _web.config_ file at the root folder.


[web.config]

<compilation debug="true" targetFramework="4.5">

      <assemblies>

        <add assembly="System.Web.Abstractions, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />

        <add assembly="System.Web.Helpers, Version=2.0.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />

        <add assembly="System.Web.Routing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />

        <add assembly="System.Web.Mvc, Version= X.X.X.X, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />

        <add assembly="System.Web.WebPages, Version= X.X.X.X, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />

        <add assembly="Syncfusion.Core, Version= X.X.X.X, Culture=neutral, PublicKeyToken=632609B4D040F6B4" />

        <add assembly="Syncfusion.EJ, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />

        <add assembly="Syncfusion.EJ.Olap, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />

        <add assembly="Syncfusion.EJ.Mvc, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />

        <add assembly="Syncfusion.Linq.Base, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />

        <add assembly="Syncfusion.Olap.Base, Version= X.X.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />

      </assemblies>

    </compilation>





{{ '![](Getting-Started_images/Getting-Started_img10.jpeg)' | markdownify }}
{:.image }
_Note: x.x.x.x in the above code example refers to the current version of the Essential Studio running in your system._

The version of Syncfusion dlls according to the .NET framework and MVC version are as follows.  For example, 12.1 version is illustrated here.

_Table: List of MVC versions_

<table>
<tr>
<td>
MVC Version</td><td>
MVC Version of Syncfusion dlls</td><td>
Base Version of Syncfusion dlls</td><td>
System.Web.Mvc</td><td>
System.Web.WebPages</td></tr>
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



[web.config]

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

3. Register the WCFservices endpoint in web.config file in root folder by adding the following code examples.
4. You can expose services through the properties such as binding, contract and address etc. using an endpoint.  In your application the service name is "MvcApplication1.OlapChartService" where "OlapChartService" is the service class name and “MvcApplication1" is the namespace name where the service class appears.

The following are the properties that meet the appropriate endpoint.  

* contract: This property indicates the contract that the endpoint is exposing. Here you are referring IOlapChartService contract and hence it is "MvcApplication1.IOlapChartService".
* binding: In your application, you can use webHttpBinding to post and receive the requests and responses between the client-end and the service-end.
* behaviorConfiguration: This property contains the name of the behavior to be used in the endpoint. endpointBehaviors are illustrated as follows.

[web.config]

<system.serviceModel>

    <services>

      <service name="MvcApplication1.OlapChartService">

        <endpoint address="" behaviorConfiguration="MvcApplication1.OlapChartServiceAspNetAjaxBehavior"

          binding="webHttpBinding" contract="MvcApplication1.IOlapChartService" />

      </service>

    </services>

</system.serviceModel>



5. The endpointBehaviors contain all the behaviors for an endpoint. You can link each endpoint to the respective behavior only using this name property. In the following code example "MvcApplication1.OlapChartServiceAspNetAjaxBehavior" refers to the OlapChartService class under the namespace MvcApplication1 in OlapChartService.svc.cs file that is the appropriate behavior for the endpoint. 



[web.config]

<system.serviceModel>

    <behaviors>

      <endpointBehaviors>

        <behavior name="MvcApplication1.OlapChartServiceAspNetAjaxBehavior">

          <enableWebScript />

        </behavior>

      </endpointBehaviors>

    </behaviors>    

</system.serviceModel>



{{ '![](Getting-Started_images/Getting-Started_img11.jpeg)' | markdownify }}
{:.image }
_Note: In this example, “MvcApplication1” indicates the name of the project and “OlapChartService” indicates the name of the WCF service created._



6. Set the UnobtrusiveJavaScriptEnabled value as false under appSettings tag as illustrated in the following code example.



[web.config]

<appSettings>

    <add key="webpages:Version" value="2.0.0.0" />

    <add key="webpages:Enabled" value="false" />

    <add key="PreserveLoginUrl" value="true" />

    <add key="ClientValidationEnabled" value="true" />

    <add key="UnobtrusiveJavaScriptEnabled" value="false" />

</appSettings>

Configuring routing file

Add the following highlighted line in RouteConfig.cs file to avoid issues when picking the WCFservice methods.

[C#]



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

                 namespaces: new[] { "MVCSampleBrowser.Controllers" }

            );

        }

    }



{{ '![](Getting-Started_images/Getting-Started_img12.png)' | markdownify }}
{:.image }














