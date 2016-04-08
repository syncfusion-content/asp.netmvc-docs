---
layout: post
title: OLAP Connectivity | PivotGrid | ASP.NET MVC | Syncfusion
description: olap connectivity 
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Data Binding 

## Binding PivotGrid to Offline Cube

To connect an OLAP Cube available in local machine, set the physical path of the Cube in the connection string. The following code example illustrates the same.

{% highlight c# %}

string connectionString = @"DataSource= system drive:\OfflineCube\Adventure_Works_Ext.cub; Provider = MSOLAP;";
OlapDataManager DataManager = new OlapDataManager(connectionString);

{% endhighlight %}

## Binding PivotGrid to Cube in local SQL Server

To connect an OLAP Cube available in SQL Server Analysis Service in local machine, set the server name and database name in the connection string. When you have any credentials to connect your Cube, then set the “User ID” and “Password” attributes accordingly. The following code example illustrates the same.

{% highlight c# %}

string connectionString = "Data source=localhost; Initial Catalog=Adventure Works DW;";
OlapDataManager DataManager = new OlapDataManager(connectionString);

{% endhighlight %}

## Binding PivotGrid to Cube in online SQL Server

To connect an OLAP Cube available in SQL Server Analysis Service in online server through **XML/A**, set the host server link and database name in the connection string. When you have any credentials to connect your Cube, then set the “User ID” and “Password” attributes accordingly. The following code example illustrates the same.


{% highlight c# %}

static string connectionString = "Data Source=http://bi.syncfusion.com/olap/msmdpump.dll; Initial Catalog=Adventure Works DW 2008 SE;";   
OlapDataManager DataManager = new OlapDataManager(connectionString);

{% endhighlight %}

## Binding PivotGrid to Cube in online Mondrian Server

To connect an OLAP Cube available in Mondrian Server through **XML/A**, set the host server link and database name in the connection string. When you have any credentials to connect your Cube, then set the “User ID” and “Password” attributes accordingly. The following code example illustrates the same.

{% highlight c# %}

string connectionString = @"Data Source = http://localhost:8080/mondrian/xmla; Initial Catalog =FoodMart;";
OlapDataManager DataManager = new OlapDataManager(connectionString);
DataManager.DataProvider.ProviderName = Syncfusion.Olap.DataProvider.Providers.Mondrian;

{% endhighlight %}


## Binding PivotGrid to Cube in online ActivePivot Server
To connect an OLAP Cube available in ActivePivot Server through **XML/A**, set the host server link and database name in the connection string. When you have any credentials to connect your Cube, then set the “User ID” and “Password” attributes accordingly. The following code example illustrates the same.

{% highlight c# %}

string connectionString=@"Data Source = http://localhost:8080/cva_s/xmla; Initial Catalog = CVAS;";
OlapDataManager DataManager = new OlapDataManager(connectionString);
DataManager.DataProvider.ProviderName=Syncfusion.Olap.DataProvider.Providers.ActivePivot;

{% endhighlight %}

## WCF

**Adding a WCF Service**

To add a WCF service in an existing MVC web application, right-click on project in Solution Explorer and select **Add > New Item**. In the **Add New Item** window, select WCF Service and name it as **OLAPService.svc**, click Add.

Now, WCF service is added into your application successfully and it comprises of the following files. The utilization of these files is explained in the immediate sections.

* OLAPService.svc
* OLAPService.svc.cs
* IOLAPService.svc.cs

**Configuring WCF Service Class**

Remove the **“DoWork”** method present inside both `OLAPService.svc.cs` and `IOLAPService.cs` files.  Next, add **“AspNetCompatibilityRequirements”** attribute on top of main class present inside OLAPService.svc.cs and set **“RequirementsMode”** value to **“Allowed”**.

{% highlight c# %}

namespace PivotGridDemo
{
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class OLAPService: IOLAPService
    {
    
    }
}

{% endhighlight %}

**List of Dependency Libraries**

Next you need to add the below mentioned dependency libraries into your Web Application. These libraries could be found in GAC (Global Assembly Cache) as well.
 
To add them to your Web Application, right-click on **References** in Solution Explorer and select **Add Reference**. Now in the **Reference Manager** dialog, under **Assemblies > Extension**, the following Syncfusion libraries are found. 

N> If you have installed any version of SQL Server Analysis Service (SSAS) or Microsoft ADOMD.NET utility, then the location of Microsoft.AnalysisServices.AdomdClient library is [system drive:\Program Files (x86)\Microsoft.NET\ADOMD.NET]

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

**List of Namespaces**

Following are the list of namespaces to be added on top of the main class inside `OLAPService.svc.cs` file.

{% highlight c# %}

using System.Web.Script.Serialization;
using System.ServiceModel.Activation;
using Syncfusion.Olap.Manager;
using Syncfusion.Olap.Reports;
using Syncfusion.JavaScript;
using OLAPUTILS = Syncfusion.JavaScript.Olap;

namespace PivotGridDemo
{
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class OLAPService: IOLAPService
    {
    
    }
}

{% endhighlight %}


**Datasource Initialization**

Now, the connection string to connect OLAP Cube, PivotGrid and JavaScriptSerializer instances are created immediately inside the main class in `OLAPService.svc.cs` file.

{% highlight c# %}

namespace PivotGridDemo
{
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class OLAPService: IOLAPService
    {
        PivotGrid htmlHelper = new PivotGrid();
        string connectionString = "Data Source=http://bi.syncfusion.com/olap/msmdpump.dll; Initial Catalog=Adventure Works DW 2008 SE;";
        JavaScriptSerializer serializer = new JavaScriptSerializer();
     	……
        ……
    }
}

{% endhighlight %}

**Service methods in WCF Service**

First, define the service methods inside **IOLAPService** interface, found in `IOLAPService.cs` file, created while adding WCF Service to your Web Application.

{% highlight c# %}

namespace PivotGridDemo {
    [ServiceContract]
    public interface IOLAPService {
        [OperationContract]
        Dictionary < string, object > InitializeGrid(string action, string gridLayout, bool enablePivotFieldList, object customObject);

        [OperationContract]
        Dictionary < string, object > DrillGrid(string action, string cellPosition, string currentReport, string headerInfo, string layout, object customObject);

        [OperationContract]
        Dictionary < string, object > Paging(string action, string pagingInfo, string currentReport, string gridLayout, object customObject);

        [OperationContract]
        Dictionary < string, object > NodeDropped(string action, string dropType, string nodeInfo, string filterParams, string currentReport);

        [OperationContract]
        Dictionary < string, object > RemoveButton(string action, string headerInfo, string currentReport);

        [OperationContract]
        Dictionary < string, object > FetchMembers(string action, string headerTag, string currentReport);

        [OperationContract]
        Dictionary < string, object > Filtering(string action, string filterParams, string currentReport);

        [OperationContract]
        Dictionary < string, object > MemberExpanded(string action, bool checkedStatus, string parentNode, string tag, string cubeName, string currentReport);

        [OperationContract]
        void Export(System.IO.Stream stream);
    }

}

{% endhighlight %}

Secondly, elaborate the service methods inside the main class, found in `OLAPService.svc.cs` file

{% highlight c# %}

namespace PivotGridDemo {
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class OLAPService: IOLAPService {
        PivotGrid htmlHelper = new PivotGrid();
        string connectionString = "Data Source=http://bi.syncfusion.com/olap/msmdpump.dll; Initial Catalog=Adventure Works DW 2008 SE;";
        JavaScriptSerializer serializer = new JavaScriptSerializer();

        //This method provides the required information from the server side when initializing the PivotGrid.
        public Dictionary < string, object > InitializeGrid(string action, string gridLayout, bool enablePivotFieldList, object customObject) {
            OlapDataManager DataManager = null;
            dynamic customData = serializer.Deserialize < dynamic > (customObject.ToString());
            DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(CreateOlapReport());
            return htmlHelper.GetJsonData(action, DataManager, gridLayout, enablePivotFieldList);
        }

        //This method provides the required information from the server side when drill up/down operation is performed in PivotGrid.
        public Dictionary < string, object > DrillGrid(string action, string cellPosition, string currentReport, string headerInfo, string layout, object customObject) {
            dynamic customData = serializer.Deserialize < dynamic > (customObject.ToString());
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(OLAPUTILS.Utils.DeserializeOlapReport(currentReport));
            return htmlHelper.GetJsonData(action, connectionString, DataManager, cellPosition, headerInfo, layout);
        }

        //This method provides the required information from the server side when tree node is dropped in PivotTable Field List.
        public Dictionary < string, object > NodeDropped(string action, string dropType, string nodeInfo, string filterParams, string currentReport) {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(OLAPUTILS.Utils.DeserializeOlapReport(currentReport));
            return htmlHelper.GetJsonData(action, DataManager, dropType, nodeInfo, filterParams, true);
        }

        //This method provides the required information from the server side when filtering values in PivotTable Field List.
        public Dictionary < string, object > Filtering(string action, string filterParams, string currentReport) {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(OLAPUTILS.Utils.DeserializeOlapReport(currentReport));
            return htmlHelper.GetJsonData(action, DataManager, null, filterParams);
        }

        //This method provides the required information from the server side when opening the editor in PivotTable Field List.
        public Dictionary < string, object > FetchMembers(string action, string headerTag, string currentReport) {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(OLAPUTILS.Utils.DeserializeOlapReport(currentReport));
            return htmlHelper.GetJsonData(action, DataManager, null, headerTag);
        }

        //This method provides the required information from the server side when paging is done in PivotGrid.
        public Dictionary < string, object > Paging(string action, string pagingInfo, string currentReport, string gridLayout, object customObject) {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(htmlHelper.SetPaging(currentReport, pagingInfo));
            return htmlHelper.GetJsonData(action, DataManager, gridLayout);
        }

        //This method provides the required information from the server side when removing the split button from PivotTable Field List.
        public Dictionary < string, object > RemoveButton(string action, string headerInfo, string currentReport) {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            DataManager.SetCurrentReport(OLAPUTILS.Utils.DeserializeOlapReport(currentReport));
            return htmlHelper.GetJsonData(action, DataManager, null, headerInfo);
        }

        //This method provides the required information from the server side when expanding member in member editor.
        public Dictionary < string, object > MemberExpanded(string action, bool checkedStatus, string parentNode, string tag, string cubeName, string currentReport) {
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            if (!string.IsNullOrEmpty(currentReport))
                DataManager.SetCurrentReport(OLAPUTILS.Utils.DeserializeOlapReport(currentReport));
            return htmlHelper.GetJsonData(action, DataManager, checkedStatus, parentNode, tag, cubeName);
        }

        //This method export PivotGrid to Excel, CSV, Word and PDF.
        public void Export(System.IO.Stream stream) {
            System.IO.StreamReader sReader = new System.IO.StreamReader(stream);
            string args = System.Web.HttpContext.Current.Server.UrlDecode(sReader.ReadToEnd());
            OlapDataManager DataManager = new OlapDataManager(connectionString);
            string fileName = "Sample";
            htmlHelper.ExportPivotGrid(DataManager, args, fileName, System.Web.HttpContext.Current.Response);
        }

        //This method carries the information about the default report which when be rendered within PivotGrid initially.
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

**Configuring Web Configuration File**

You can expose services through the properties, binding, contract and address by using an endpoint.

* Contract: This property indicates that the contract of the endpoint is exposing. Here you are referring to `IOLAPService` contract and hence it is `PivotGridDemo.IOLAPService`.
* Binding: In your application, you use `webHttpBinding` to post and receive the requests and responses between the client-end and the service.
* behaviorConfiguration: This property contains the name of the behavior to be used in the endpoint.

The endpointBehaviors are illustrated as follows. 
 
{% highlight xml %}

<system.serviceModel>
    …… 
    ……
    <services>
        <service name="PivotGridDemo.OLAPService">
            <endpoint address="" behaviorConfiguration="PivotGridDemo.OLAPServiceAspNetAjaxBehavior" binding="webHttpBinding" contract="PivotGridDemo.IOLAPService" /> </service>
    </services>
</system.serviceModel>

{% endhighlight %}

The endpointBehaviors contain all the behaviors for an endpoint. You can link each endpoint to the respective behavior only by using this name property.

{% highlight xml %}

<system.serviceModel>
    <behaviors>
        <endpointBehaviors>
            <behavior name="PivotGridDemo.OLAPServiceAspNetAjaxBehavior">
                <enableWebScript /> </behavior>
        </endpointBehaviors>
    </behaviors>
    …… 
    ……
</system.serviceModel>

{% endhighlight %}

**Configuring routing file**

Routing configuration needs to be done in `RouteConfig.cs` file found under **AppStart** folder. The configuration would allow picking appropriate WCF service without any issues.

{% highlight c# %}

public static void RegisterRoutes(RouteCollection routes) {
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");
    //NOTE: In the following highlighted lines _wcf_ is just the folder name inside which service files(*.svc) are present.
    routes.IgnoreRoute("{resource}.svc/{*pathInfo}");
    routes.IgnoreRoute("{resource}.svc");
    routes.MapRoute(
        name: "Default",
        url: "{controller}/{action}/{id}",
        defaults: new {
            controller = "Home", action = "Index", id = UrlParameter.Optional
        },
        namespaces: new [] {
            "PivotGridDemo.Controllers"
        }
    );
}

{% endhighlight %}

N> In this example, **“PivotGridDemo”** indicates the name and root namespace of the Web Application created in Visual Studio IDE and “OLAPService” indicates the name of the WCF service created.

Now, **PivotGrid** will be rendered with Internet Sales Amount over a period of fiscal years across different customer geographic locations.

![](Getting-Started_images/olapwebapi.png) 

