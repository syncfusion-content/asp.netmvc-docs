---
layout: post
title: Relational Getting Started | PivotClient| ASP.NET MVC | Syncfusion
description: relational getting started
platform: ejmvc
control: PivotClient
documentation: ug
---

# Getting Started

>**Important**
Starting with v16.2.0.x, if you refer to Syncfusion assemblies from trial setup or from the NuGet feed, include a license key in your projects. Refer to this [link](https://help.syncfusion.com/common/essential-studio/licensing/license-key) to learn about registering Syncfusion license key in your ASP.NET Core application to use our components.

## Creating a simple application with PivotClient and Relational datasource (Client Mode)

This section covers the information that you need to know to populate a simple PivotClient with Relational data completely on the client-side.

## Project Initialization

Create a new **ASP.NET MVC Web Application** using Visual Studio IDE and name the project as **“PivotClientDemo”**.

Select the View engine as **‘Razor’** and Project template as **‘Internet Application’** and finally click **OK** button to create an application.

Now add the following dependency libraries as references into your MVC Web Application. In order to add them to your application, right-click on **References** in Solution Explorer and select Add Reference. Now in the **Reference Manager** dialog, under **Assemblies > Extension**, the following Syncfusion libraries will be found.

* Syncfusion.EJ
* Syncfusion.EJ.Pivot
* Syncfusion.EJ.Export
* Syncfusion.EJ.MVC

The version of Syncfusion libraries based on .NET Framework and MVC version are classified below. For example, version is illustrated as,

<table>
<tr>
<th>MVC Version</th>
<th>MVC Version of Syncfusion assembly</th>
<th>Base Version of Syncfusion assembly</th>
<th>System.Web.Mvc</th>
<th>System.Web.WebPages</th>
</tr>
<tr>
<td>MVC3</td>
<td>{{ site.mvc3releaseversion }}</td>
<td>{{ site.35esreleaseversion }}</td>
<td>3.0</td>
<td>1.0</td>
</tr>
<tr>
<td>MVC4</td>
<td>{{ site.mvc4releaseversion }}</td>
<td>{{ site.40esreleaseversion }}</td>
<td>4.0</td>
<td>2.0</td>
</tr>
<tr>
<td>MVC5</td>
<td>{{ site.mvc5releaseversion }}</td>
<td>{{ site.45esreleaseversion }}</td>
<td>5.0</td>
<td>3.0</td>
</tr>
</table>

Register the referred assemblies in Web.config files available inside Views folder and also at the root of the application.

{% highlight xml %}

<compilation debug="true" targetFramework="4.0">
    <assemblies>
        ……
        ……
        <add assembly="Syncfusion.EJ, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.EJ.Pivot, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.EJ.Export, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.EJ.Mvc, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
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

### Scripts and CSS References

The scripts and style sheets that are mandatorily required to render PivotClient control in a MVC Web Application are mentioned in an appropriate order below:

1. ej.web.all.min.css
2. jQuery-3.0.0.min.js
3. ej.web.all.min.js
4. jsrender.min.js

Scripts and style sheets are referred under the <head> tag in _Layout.cshtml file which is found inside Views > Shared folder.

{% highlight html %}

<head>
    <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" type="text/css" />
    <script src="http://cdn.syncfusion.com/js/assets/external/jquery-3.0.0.min.js" type="text/javascript"></script>
    <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js" type="text/javascript"></script>
    <script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js" type="text/javascript"></script>

</head>

{% endhighlight %}

The script manager is initialized immediately after the `RenderBody()` function call in **_Layout.cshtml** file in-order to generate control related scripts.

{% highlight cshtml %}

<body>
    ……
    ……
    @RenderBody()
    @(Html.EJ().ScriptManager())
</body>
{% endhighlight %}

### Initialize PivotClient

Before initializing, empty the contents of Index.cshtml file under Views > Home folder and add the following codes.

{% highlight html %}

@Html.EJ().Pivot().PivotClient("PivotClient1").Title("Relational Browser")

{% endhighlight %}

### Populate PivotClient With Data

Let us now see how to populate the PivotClient control using a sample JSON data as shown below.

{% highlight html %}

@Html.EJ().Pivot().PivotClient("PivotClient1").Title("Relational Browser").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad"))

<script type="text/javascript">
function onLoad(args) {
    args.model.dataSource.data = [
                    { Amount: 100, Country: "Canada", Date: "FY 2005", Product: "Bike", Quantity: 2, State: "Alberta" },
                    { Amount: 200, Country: "Canada", Date: "FY 2006", Product: "Van", Quantity: 3, State: "British Columbia" },
                    { Amount: 300, Country: "Canada", Date: "FY 2007", Product: "Car", Quantity: 4, State: "Brunswick" },
                    { Amount: 150, Country: "Canada", Date: "FY 2008", Product: "Bike", Quantity: 3, State: "Manitoba" },
                    { Amount: 200, Country: "Canada", Date: "FY 2006", Product: "Car", Quantity: 4, State: "Ontario" },
                    { Amount: 100, Country: "Canada", Date: "FY 2007", Product: "Van", Quantity: 1, State: "Quebec" },
                    { Amount: 200, Country: "France", Date: "FY 2005", Product: "Bike", Quantity: 2, State: "Charente-Maritime" },
                    { Amount: 250, Country: "France", Date: "FY 2006", Product: "Van", Quantity: 4, State: "Essonne" },
                    { Amount: 300, Country: "France", Date: "FY 2007", Product: "Car", Quantity: 3, State: "Garonne (Haute)" },
                    { Amount: 150, Country: "France", Date: "FY 2008", Product: "Van", Quantity: 2, State: "Gers" },
                    { Amount: 200, Country: "Germany", Date: "FY 2006", Product: "Van", Quantity: 3, State: "Bayern" },
                    { Amount: 250, Country: "Germany", Date: "FY 2007", Product: "Car", Quantity: 3, State: "Brandenburg" },
                    { Amount: 150, Country: "Germany", Date: "FY 2008", Product: "Car", Quantity: 4, State: "Hamburg" },
                    { Amount: 200, Country: "Germany", Date: "FY 2008", Product: "Bike", Quantity: 4, State: "Hessen" },
                    { Amount: 150, Country: "Germany", Date: "FY 2007", Product: "Van", Quantity: 3, State: "Nordrhein-Westfalen" },
                    { Amount: 100, Country: "Germany", Date: "FY 2005", Product: "Bike", Quantity: 2, State: "Saarland" },
                    { Amount: 150, Country: "United Kingdom", Date: "FY 2008", Product: "Bike", Quantity: 5, State: "England" },
                    { Amount: 250, Country: "United States", Date: "FY 2007", Product: "Car", Quantity: 4, State: "Alabama" },
                    { Amount: 200, Country: "United States", Date: "FY 2005", Product: "Van", Quantity: 4, State: "California" },
                    { Amount: 100, Country: "United States", Date: "FY 2006", Product: "Bike", Quantity: 2, State: "Colorado" },
                    { Amount: 150, Country: "United States", Date: "FY 2008", Product: "Car", Quantity: 3, State: "New Mexico" },
                    { Amount: 200, Country: "United States", Date: "FY 2005", Product: "Bike", Quantity: 4, State: "New York" },
                    { Amount: 250, Country: "United States", Date: "FY 2008", Product: "Car", Quantity: 3, State: "North Carolina" },
                    { Amount: 300, Country: "United States", Date: "FY 2007", Product: "Van", Quantity: 4, State: "South Carolina" }
    ]
}
</script>

{% endhighlight %}

The JSON data is set to the **"data"** property present inside the **"dataSource"** object. **"dataSource"** object allows us to set both datasource as well as the fields that needs to be displayed in the row, column, value and filter section of the PivotClient control.

{% highlight html %}

@Html.EJ().Pivot().PivotClient("PivotClient1").Title("Relational Browser").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add();}).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Add();}))

{% endhighlight %}

Now, PivotClient is rendered with PivotChart and PivotGrid with "Country" field in Row, "Product" field in Column and "Amount" field in Value section.

![ASP NET MVC pivot client control with relational client mode](Getting-Started_images/purejs.png)

## Creating a simple application with PivotClient and Relational datasource (Server Mode)

This section covers the information required to create a simple PivotClient bound to Relational datasource.

N> ASP.NET MVC Web Application will contain a service that transfers data to server-side, processes and returns back to client-side for control rendering and re-rendering. The service utilized for communication could be either WCF or WebAPI based on user requirement.

### Project Initialization

Create a new **ASP.NET MVC Web Application** using Visual Studio IDE and name the project as **“PivotClientDemo”**.

Select the View engine as **‘Razor’** and Project template as **‘Internet Application’** and finally click **OK** button to create an application.

Now add the following dependency libraries as references into your MVC Web Application. In order to add them to your application, right-click on **References** in Solution Explorer and select Add Reference. Now in the **Reference Manager** dialog, under **Assemblies > Extension**, the following Syncfusion libraries will be found.

N> If you have installed any version of Essential Studio, then the location of Syncfusion libraries is [system drive:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\Assemblies].

* Syncfusion.Compression.Base
* Syncfusion.Linq.Base
* Syncfusion.Olap.Base
* Syncfusion.PivotAnalysis.Base
* System.Data.SqlServerCe (Version: 4.0.0.0)
* Syncfusion.XlsIO.Base
* Syncfusion.Pdf.Base
* Syncfusion.DocIO.Base
* Syncfusion.EJ
* Syncfusion.EJ.Export
* Syncfusion.EJ.Pivot
* Syncfusion.EJ.MVC

The version of Syncfusion libraries based on .NET Framework and MVC version are classified below. For example, version is illustrated as,

<table>
<tr>
<th>
MVC Version</th><th>
MVC Version of Syncfusion assembly</th><th>
Base Version of Syncfusion assembly</th><th>
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

Register the referenced assemblies in "Web.config" files available inside Views folder and also at the root of the application.

{% highlight xml %}

<compilation debug="true" targetFramework="4.0">
    <assemblies>
        ……
        ……
        <add assembly="Syncfusion.EJ, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.EJ.Pivot, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.EJ.Mvc, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.Linq.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.EJ.Export, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.Olap.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.Compression.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.PivotAnalysis.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.Pdf.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.XlsIO.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
        <add assembly="Syncfusion.DocIO.Base, Version= {{ site.40esreleaseversion }}, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" />
    </assemblies>
</compilation>

{% endhighlight %}

Register the required namespaces in Web.config files available inside Views folder and also at the root of the application.

{% highlight xml %}

<namespaces>
    ……
    ……
    <add namespace="Syncfusion.MVC.EJ" />
    <add namespace="Syncfusion.JavaScript" />
</namespaces>

{% endhighlight %}

N> Registering assemblies and namespaces earlier helps to include the control in view page with the help of intellisense.

Set the **UnobtrusiveJavaScriptEnabled** property to false under **appSettings** tag in "Web.config" file at the root folder.

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

The scripts and style sheets that are mandatorily required to render PivotClient control in a MVC Web Application are mentioned in an appropriate order below:

1. ej.web.all.min.css
2. jQuery-3.0.0.min.js
3. ej.web.all.min.js
4. jsrender.min.js

[Click here](http://help.syncfusion.com/js/cdn) here to know more about scripts and style sheets available online (CDN Link).

Scripts and style sheets are referred under the <head> tag in **_Layout.cshtml** file which is found inside **Views > Shared folder.**

{% highlight html %}

<head>
    <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" type="text/css" />
    <script src="http://cdn.syncfusion.com/js/assets/external/jquery-3.0.0.min.js" type="text/javascript"></script>
    <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js" type="text/javascript"></script>
    <script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js" type="text/javascript"></script>
</head>

{% endhighlight %}

The script manager is initialized immediately after the `RenderBody()` function call in **_Layout.cshtml** file in-order to generate control related scripts.

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

@using Syncfusion.JavaScript;

@Html.EJ().Pivot().PivotClient("PivotClient1").Title("Relational Browser").Url(Url.Content("/Relational"))

{% endhighlight %}

The **“Url”** property in PivotClient control points the service endpoint, where data are processed and fetched in the form of JSON. The services used in PivotClient control as endpoint are WCF and WebAPI.

N> The above "Index.cshtml" contains WebAPI URL, which is "/Relational". If WCF service is used as endpoint, the URL would look like "/RelationalService.svc".


### WebAPI

**Adding a WebAPI Controller**

To add a WebAPI controller in an existing MVC Web Application, right-click on the project in Solution Explorer and select **Add > New Item**. In the **Add New Item** window, select **WebAPI Controller Class** and name it **“RelationalController.cs”**, click **Add**.

Now, WebAPI controller is added to the application successfully with the file **“RelationalController.cs”**.

N> While adding WebAPI Controller Class, name it with the suffix ‘Controller’ which is mandatory. For example, in this demo the controller is named as “RelationalController”.

Next, remove all the existing methods such as "Get", "Post", "Put" and "Delete" present inside `RelationalController.cs` file.

{% highlight c# %}

namespace PivotClientDemo
{
    public class RelationalController: ApiController
    {

    }
}

{% endhighlight %}

**Adding the List of Namespaces**

The following are the list of namespaces to be added on top of the main class inside `RelationalController.cs` file.

{% highlight c# %}

using Syncfusion.JavaScript;
using Syncfusion.PivotAnalysis.Base;
using System;
using System.Collections.Generic;
using System.Data;
using System.Data.SqlServerCe;
using System.Linq;
using System.Net.Http;
using System.Text;
using System.Web;
using System.Web.Http;
using System.Web.Script.Serialization;

namespace PivotClientDemo
{
    public class RelationalController : ApiController
    {

    }
}

{% endhighlight %}

**Datasource Initialization**

A simple collection is provided as a datasource for the PivotClient in this demo section. This datasource is placed inside a separate class “ProductSales” in `RelationalController.cs` file. Refer to the following code example.

{% highlight c# %}

namespace PivotClientDemo {
    …………
    …………
    internal class ProductSales {
        public string Product {
            get;
            set;
        }

        public string Date {
            get;
            set;
        }

        public string Country {
            get;
            set;
        }

        public string State {
            get;
            set;
        }

        public int Quantity {
            get;
            set;
        }

        public double Amount {
            get;
            set;
        }

        public static ProductSalesCollection GetSalesData() {
            /// Geography
            string[] countries = new string[] {
                "Australia",
                "Canada",
                "France",
                "Germany",
                "United Kingdom",
                "United States"
            };
            string[] ausStates = new string[] {
                "New South Wales",
                "Queensland",
                "South Australia",
                "Tasmania",
                "Victoria"
            };
            string[] canadaStates = new string[] {
                "Alberta",
                "British Columbia",
                "Brunswick",
                "Manitoba",
                "Ontario",
                "Quebec"
            };
            string[] franceStates = new string[] {
                "Charente-Maritime",
                "Essonne",
                "Garonne (Haute)",
                "Gers",
            };
            string[] germanyStates = new string[] {
                "Bayern",
                "Brandenburg",
                "Hamburg",
                "Hessen",
                "Nordrhein-Westfalen",
                "Saarland"
            };
            string[] ukStates = new string[] {
                "England"
            };
            string[] ussStates = new string[] {
                "New York",
                "North Carolina",
                "Alabama",
                "California",
                "Colorado",
                "New Mexico",
                "South Carolina"
            };

            /// Time
            string[] dates = new string[] {
                "FY 2005",
                "FY 2006",
                "FY 2007",
                "FY 2008",
                "FY 2009"
            };

            /// Products
            string[] products = new string[] {
                "Bike",
                "Van",
                "Car"
            };
            Random r = new Random(123345345);

            int numberOfRecords = 2000;
            ProductSalesCollection listOfProductSales = new ProductSalesCollection();
            for (int i = 0; i < numberOfRecords; i++) {
                ProductSales sales = new ProductSales();
                sales.Country = countries[r.Next(1, countries.GetLength(0))];
                sales.Quantity = r.Next(1, 12);
                /// 1 percent discount for 1 quantity
                double discount = (30000 * sales.Quantity) * (double.Parse(sales.Quantity.ToString()) / 100);
                sales.Amount = (30000 * sales.Quantity) - discount;
                sales.Date = dates[r.Next(r.Next(dates.GetLength(0) + 1))];
                sales.Product = products[r.Next(r.Next(products.GetLength(0) + 1))];
                switch (sales.Product) {
                    case "Car":
                        {
                            sales.Date = "FY 2005";
                            break;
                        }
                }
                switch (sales.Country) {
                    case "Australia":
                        {
                            sales.State = ausStates[r.Next(ausStates.GetLength(0))];
                            break;
                        }
                    case "Canada":
                        {
                            sales.State = canadaStates[r.Next(canadaStates.GetLength(0))];
                            break;
                        }
                    case "France":
                        {
                            sales.State = franceStates[r.Next(franceStates.GetLength(0))];
                            break;
                        }
                    case "Germany":
                        {
                            sales.State = germanyStates[r.Next(germanyStates.GetLength(0))];
                            break;
                        }
                    case "United Kingdom":
                        {
                            sales.State = ukStates[r.Next(ukStates.GetLength(0))];
                            break;
                        }
                    case "United States":
                        {
                            sales.State = ussStates[r.Next(ussStates.GetLength(0))];
                            break;
                        }
                }
                listOfProductSales.Add(sales);
            }

            return listOfProductSales;
        }

        public override string ToString() {
            return string.Format("{0}-{1}-{2}", this.Country, this.State, this.Product);
        }

        public class ProductSalesCollection: List < ProductSales > {}
    }
}

{% endhighlight %}


**Service methods in WebAPI Controller**

Define the service methods inside RelationalController class, found inside `RelationalController.cs` file, created while adding WebAPI Controller Class to the Application.

{% highlight c# %}

namespace PivotClientDemo {
    public class RelationalController: ApiController
    {
        PivotClient pivotClient = new PivotClient();
        PivotChart pivotChart = new PivotChart();
        PivotGrid pivotGrid = new PivotGrid();
        JavaScriptSerializer serializer = new JavaScriptSerializer();
        string conStringforDB = "";//Enter appropriate connection string to connect database for saving and loading operation of reports.

        [System.Web.Http.ActionName("InitializeClient")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> InitializeClient(Dictionary<string, object> jsonResult)
        {
            this.BindData();
            return pivotClient.GetJsonData(jsonResult["action"].ToString(), ProductSales.GetSalesData(), null);
        }

        [System.Web.Http.ActionName("FetchMembers")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> FetchMembers(Dictionary<string, object> jsonResult)
        {
            pivotClient.PopulateData(jsonResult["currentReport"].ToString());
            var dict = pivotClient.GetJsonData(jsonResult["action"].ToString(), ProductSales.GetSalesData(), jsonResult["headerTag"].ToString());
            return dict;
        }

        [System.Web.Http.ActionName("DrillChart")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> DrillChart(Dictionary<string, object> jsonResult)
        {
            this.BindData();
            this.pivotChart.PivotEngine.PivotRows = this.pivotClient.PivotReport.PivotRows;
            this.pivotChart.PivotEngine.PivotColumns = this.pivotClient.PivotReport.PivotColumns;
            this.pivotChart.PivotEngine.PivotCalculations = this.pivotClient.PivotReport.PivotCalculations;
            return pivotChart.GetJsonData(jsonResult["action"].ToString(), ProductSales.GetSalesData(), jsonResult["drilledSeries"].ToString());
        }

        [System.Web.Http.ActionName("Filtering")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> Filtering(Dictionary<string, object> jsonResult)
        {
            pivotClient.PopulateData(jsonResult["currentReport"].ToString());
            var dict = pivotClient.GetJsonData(jsonResult["action"].ToString(), ProductSales.GetSalesData(), jsonResult["filterParams"].ToString());
            return dict;
        }

        [System.Web.Http.ActionName("NodeDropped")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> NodeDropped(Dictionary<string, object> jsonResult)
        {
            Dictionary<string, object> dict = pivotClient.GetJsonData(jsonResult["action"].ToString(), ProductSales.GetSalesData(), jsonResult["args"].ToString());
            return dict;
        }

        [System.Web.Http.ActionName("ToolbarOperations")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> ToolbarOperations(Dictionary<string, object> jsonResult)
        {
            Dictionary<string, object> dict = pivotClient.GetJsonData(jsonResult["action"].ToString(), ProductSales.GetSalesData(), jsonResult["args"].ToString());
            return dict;
        }

        [System.Web.Http.ActionName("Export")]
        [System.Web.Http.HttpPost]
        public void Export()
        {
            string args = HttpContext.Current.Request.Form.GetValues(0)[0];
            Dictionary<string, string> gridParams = serializer.Deserialize<Dictionary<string, string>>(args);
            pivotClient.PopulateData(gridParams["currentReport"]);
            string fileName = "Sample";
            pivotClient.ExportPivotClient(ProductSales.GetSalesData(), args, fileName, System.Web.HttpContext.Current.Response);
        }

       [System.Web.Http.ActionName("SaveReportToDB")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> SaveReportToDB(Dictionary<string, object> jsonResult)
        {
            string operationalMode = jsonResult["operationalMode"].ToString(), analysisMode = jsonResult["analysisMode"].ToString(), reportName = string.Empty;
            bool isDuplicate = true;
            SqlCeConnection con = new SqlCeConnection() { ConnectionString = conStringforDB };
            con.Open();
            reportName = jsonResult["reportName"].ToString() + "##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower();
            SqlCeCommand cmd1 = null;
            foreach (DataRow row in GetDataTable().Rows)
            {
                if ((row.ItemArray[0] as string).Equals(reportName))
                {
                    isDuplicate = false;
                    cmd1 = new SqlCeCommand("update ReportsTable set Report=@Reports where ReportName like @ReportName", con);
                }
            }
            if (isDuplicate)
            {
                cmd1 = new SqlCeCommand("insert into ReportsTable Values(@ReportName,@Reports)", con);
            }
            cmd1.Parameters.Add("@ReportName", reportName);
            cmd1.Parameters.Add("@Reports", Encoding.UTF8.GetBytes(jsonResult["clientReports"].ToString()).ToArray());
            cmd1.ExecuteNonQuery();
            con.Close();
            Dictionary<string, object> dictionary = new Dictionary<string, object>();
            dictionary.Add("CurrentAction", "Save");
            return dictionary;

        }

        [System.Web.Http.ActionName("RemoveReportFromDB")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> RemoveReportFromDB(Dictionary<string, object> jsonResult)
        {
            string operationalMode = jsonResult["operationalMode"].ToString(), analysisMode = jsonResult["analysisMode"].ToString(), reportName = string.Empty;
            SqlCeConnection con = new SqlCeConnection() { ConnectionString = conStringforDB };
            con.Open();
            reportName = jsonResult["reportName"].ToString() + "##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower();
            SqlCeCommand cmd1 = null;
            foreach (DataRow row in GetDataTable().Rows)
            {
                if ((row.ItemArray[0] as string).Equals(reportName))
                {
                    cmd1 = new SqlCeCommand("DELETE FROM ReportsTable WHERE ReportName LIKE '%" + reportName + "%'", con);
                }
            }
            cmd1.ExecuteNonQuery();
            con.Close();
            Dictionary<string, object> dictionary = new Dictionary<string, object>();
            dictionary.Add("CurrentAction", "Remove");
            return dictionary;

        }

        [System.Web.Http.ActionName("RenameReportInDB")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> RenameReportInDB(Dictionary<string, object> jsonResult)
        {
            string operationalMode = jsonResult["operationalMode"].ToString(), analysisMode = jsonResult["analysisMode"].ToString(), reportName = string.Empty, renameReport = string.Empty;
            SqlCeConnection con = new SqlCeConnection() { ConnectionString = conStringforDB };
            con.Open();
            reportName = jsonResult["selectedReport"].ToString() + "##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower();
            renameReport = jsonResult["renameReport"].ToString() + "##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower();
            SqlCeCommand cmd1 = null;
            foreach (DataRow row in GetDataTable().Rows)
            {
                if ((row.ItemArray[0] as string).Equals(reportName))
                {
                    cmd1 = new SqlCeCommand("update ReportsTable set ReportName=@RenameReport where ReportName like '%" + reportName + "%'", con);
                }
            }
            cmd1.Parameters.Add("@RenameReport", renameReport);
            cmd1.ExecuteNonQuery();
            con.Close();
            Dictionary<string, object> dictionary = new Dictionary<string, object>();
            dictionary.Add("CurrentAction", "Rename");
            return dictionary;
        }

        [System.Web.Http.ActionName("FetchReportListFromDB")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> FetchReportListFromDB(Dictionary<string, object> jsonResult)
        {
            string reportNames = string.Empty, currentRptName = string.Empty, operationalMode = jsonResult["operationalMode"].ToString(), analysisMode = jsonResult["analysisMode"].ToString();
            foreach (System.Data.DataRow row in GetDataTable().Rows)
            {
                currentRptName = (row.ItemArray[0] as string);
                if (currentRptName.IndexOf("##" + operationalMode + "#>>#" + analysisMode) >= 0)
                {
                    currentRptName = currentRptName.Replace("##" + operationalMode + "#>>#" + analysisMode, "");
                    reportNames = reportNames == "" ? currentRptName : reportNames + "__" + currentRptName;
                }
            }
            Dictionary<string, object> dictionary = new Dictionary<string, object>();
            dictionary.Add("ReportNameList", reportNames);
            dictionary.Add("action", jsonResult["action"].ToString());
            return dictionary;
        }

        [System.Web.Http.ActionName("LoadReportFromDB")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> LoadReportFromDB(Dictionary<string, object> jsonResult)
        {
            PivotReport report = new PivotReport();
            string operationalMode = jsonResult["operationalMode"].ToString(), analysisMode = jsonResult["analysisMode"].ToString();
            Dictionary<string, object> dictionary = new Dictionary<string, object>();
            string currentRptName = string.Empty;
            foreach (DataRow row in GetDataTable().Rows)
            {
                currentRptName = (row.ItemArray[0] as string).Replace("##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower(), "");
                if (currentRptName.Equals(jsonResult["reportName"].ToString()))
                {
                    byte[] reportString = new byte[2 * 1024];
                    reportString = (row.ItemArray[1] as byte[]);
                    if (analysisMode.ToLower() == "pivot" && operationalMode.ToLower() == "servermode")
                        dictionary = pivotClient.GetJsonData("LoadReport", ProductSales.GetSalesData(), Encoding.UTF8.GetString(reportString));
                    else
                        dictionary.Add("report", Encoding.UTF8.GetString(reportString));
                    break;
                }
            }
            return dictionary;
        }
        private DataTable GetDataTable()
        {
            SqlCeConnection con = new SqlCeConnection() { ConnectionString = conStringforDB };
            con.Open();
            DataSet dSet = new DataSet();
            new SqlCeDataAdapter("Select * from ReportsTable", con).Fill(dSet);
            con.Close();
            return dSet.Tables[0];
        }
        private void BindData()
        {
            this.pivotClient.PivotReport.PivotRows.Add(new PivotItem { FieldMappingName = "Country", FieldHeader = "Country", TotalHeader = "Total" });
            this.pivotClient.PivotReport.PivotColumns.Add(new PivotItem { FieldMappingName = "Product", FieldHeader = "Product", TotalHeader = "Total" });
            this.pivotClient.PivotReport.PivotCalculations.Add(new PivotComputationInfo { CalculationName = "Amount", Description = "Amount", FieldHeader = "Amount", FieldName = "Amount", Format = "C", SummaryType = Syncfusion.PivotAnalysis.Base.SummaryType.DoubleTotalSum });
        }
    }
        .....
        ..... // Initialize the datasource
        .....
}

{% endhighlight %}

**Configure routing in WebAPIConfig Class**

Open the "WebApiConfig.cs" file found in **App_Start** folder. Then routing could be configured as shown in the following code example.

{% highlight c# %}

public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        config.Routes.MapHttpRoute(
            name: "DefaultApi",
            routeTemplate: "{controller}/{action}/{id}",
            defaults: new { id = RouteParameter.Optional }
        );
    }
}
{% endhighlight %}

Now, **PivotClient** is rendered with PivotChart and PivotGird with "Country" field in Row, "Product" field in Column and "Amount" field in Value section.

![ASP NET MVC pivot client control with relational server mode](Getting-Started_images/relaionalwebapi.png)

### WCF

This section demonstrates the utilization of WCF service as endpoint binding Relational datasource to a simple PivotClient. For more details on this topic, [click here](https://help.syncfusion.com/aspnetmvc/PivotClient/relational-connectivity#wcf).


