---
layout: post
title: Relational Getting Started | PivotChart| ASP.NET MVC | Syncfusion
description: relational getting started
platform: ejmvc
control: PivotChart
documentation: ug
---

# Getting Started

>**Important**
Starting with v16.2.0.x, if you refer to Syncfusion assemblies from trial setup or from the NuGet feed, include a license key in your projects. Refer to this [link](https://help.syncfusion.com/common/essential-studio/licensing/license-key) to learn about registering Syncfusion license key in your ASP.NET Core application to use our components.

## Creating a simple application with PivotChart and Relational datasource (Client Mode)

This section covers the information that you need to know to populate a simple PivotChart with Relational data completely on the client-side.

## Project Initialization

Create a new **ASP.NET MVC Web Application** using Visual Studio IDE and name the project as **“PivotChartDemo”**.

Select the View engine as **‘Razor’** and Project template as **‘Internet Application’** and finally click **OK** button to create an application.

Now add the following dependency libraries as references into your MVC Web Application. In order to add them to your application, right-click on **References** in Solution Explorer and select Add Reference. Now in the **Reference Manager** dialog, under **Assemblies > Extension**, the following Syncfusion libraries will be found.

* Syncfusion.EJ
* Syncfusion.EJ.Export
* Syncfusion.EJ.Pivot
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

### Scripts and CSS Initialization

The scripts and style sheets that are mandatorily required to render PivotChart control in an MVC Web Application are mentioned in an appropriate order below:

1. ej.web.all.min.css
2. jQuery-3.0.0.min.js
3. ej.web.all.min.js

[Click here](http://help.syncfusion.com/js/cdn) here to know more about scripts and style sheets available online (CDN Link).

Scripts and style sheets are referred under the <head> tag in **_Layout.cshtml** file which is found inside **Views > Shared folder.**

{% highlight cshtml %}

<head>
    <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" type="text/css" />
    <script src="http://cdn.syncfusion.com/js/assets/external/jquery-3.0.0.min.js" type="text/javascript"></script>
    <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js" type="text/javascript"></script>
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

### Initialize PivotChart

Before initializing, empty the contents of Index.cshtml file under Views > Home folder and add the following codes.

{% highlight cshtml %}

@using Syncfusion.JavaScript;

@Html.EJ().Pivot().PivotChart("PivotChart1")

<style>
    #PivotChart1 {
        width:950px;
        height:460px;
    }
</style>
{% endhighlight %}

### Populate PivotChart With Data

Let us now see how to populate the PivotChart control using a sample JSON data as shown below.

{% highlight cshtml %}

@Html.EJ().Pivot().PivotChart("PivotChart1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad"))

<script type="text/javascript">
    function onLoad(args) {
        args.model.dataSource.data = [
            { Amount: 100, Country: "Canada", Product: "Bike" },
            { Amount: 200, Country: "Germany", Product: "Van" },
            { Amount: 300, Country: "Germany", Product: "Car" },
            { Amount: 150, Country: "United Kingdom", Product: "Bike" },
            { Amount: 200, Country: "Canada", Product: "Car" }
        ]
    }
</script>

<style>
    #PivotChart1 {
        width:950px;
        height:460px;
    }
</style>
{% endhighlight %}

The JSON data is set to the **"data"** property present inside the **"dataSource"** object. **"dataSource"** object allows us to set both datasource as well as the fields that needs to be displayed in the row, column, value and filter section of the PivotChart control.

{% highlight cshtml %}

@Html.EJ().Pivot().PivotChart("PivotChart1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add();}).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Add();})).Size(size=>size.Height("460px").Width("950px"))

{% endhighlight %}

The above code will generate a simple PivotChart with sales amount over products in different regions.

![ASP NET MVC pivot chart control with relational client mode](Relational-Getting-Started_images/PopulatePivotChartWithData.png)

### Apply Sorting

You can sort a field either to ascending or descending order using the "sortOrder" property. Sorting is applicable only for Row and Column fields.

N> By default, fields are arranged in ascending order.

{% highlight cshtml %}

@Html.EJ().Pivot().PivotChart("PivotChart1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource
.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").SortOrder(SortOrder.Descending).Add();})
.Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); })
.Values(values => { values.FieldName("Amount").Add();})).Size(size=>size.Height("460px").Width("950px"))

{% endhighlight %}

![Sorting support in ASP NET MVC pivot chart control](Relational-Getting-Started_images/ApplySorting.png)

### Apply Filtering

Filtering option allows you to specify a set of values that either need to be displayed or hidden. Also filtering option is applicable only for Row, Column and Filter areas.

**"FilterItems"** object allow us to apply filtering to the fields using the following properties:

* FilterType -  indicates whether the values should be included or excluded.
* Values -  contains an array of values that needs to be included or excluded within the particular field.

{% highlight cshtml %}

@Html.EJ().Pivot().PivotChart("PivotChart1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").FilterItems(filter => { filter.FilterType(PivotFilterType.Exclude).Values(value => { value.Add("United Kingdom"); }); }).Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Add(); })).Size(size=>size.Height("460px").Width("950px"))

{% endhighlight %}

![Filtering support in ASP NET MVC pivot chart control](Relational-Getting-Started_images/ApplyFiltering.png)

## Creating a simple application with PivotChart and Relational datasource (Server Mode)

This section covers the information required to create a simple PivotChart bound to Relational datasource.

N> ASP.NET MVC Web Application will contain a service that transfers data to server-side, processes and returns back to client-side for control rendering and re-rendering. The service utilized for communication could be either WCF or WebAPI based on user requirement.

### Project Initialization

Create a new **ASP.NET MVC Web Application** using Visual Studio IDE and name the project as **“PivotChartDemo”**.

Select the View engine as **‘Razor’** and Project template as **‘Internet Application’** and finally click **OK** button to create an application.

Now add the following dependency libraries as references into your MVC Web Application. In order to add them to your application, right-click on **References** in Solution Explorer and select Add Reference. Now in the **Reference Manager** dialog, under **Assemblies > Extension**, the following Syncfusion libraries will be found.

N> If you have installed any version of Essential Studio, then the location of Syncfusion libraries is [system drive:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\Assemblies].

* Syncfusion.Compression.Base
* Syncfusion.Linq.Base
* Syncfusion.Olap.Base
* Syncfusion.PivotAnalysis.Base
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

Register the referenced assemblies in Web.config files available inside Views folder and also at the root of the application.

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

### Scripts and CSS Initialization

The scripts and style sheets that are mandatorily required to render PivotChart control in a MVC Web Application are mentioned in an appropriate order below:

1. ej.web.all.min.css
2. jQuery-3.0.0.min.js
3. ej.web.all.min.js

[Click here](http://help.syncfusion.com/js/cdn) here to know more about scripts and style sheets available online (CDN Link).

Scripts and style sheets are referred under the <head> tag in **_Layout.cshtml** file which is found inside **Views > Shared folder.**

{% highlight cshtml %}

<head>
    <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" type="text/css" />
    <script src="http://cdn.syncfusion.com/js/assets/external/jquery-3.0.0.min.js" type="text/javascript"></script>
    <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js" type="text/javascript"></script>
</head>
{% endhighlight %}

The script manager is initialized immediately after the `RenderBody()` function call in **_Layout.cshtml** file in-order to generate control related scripts.

{% highlight cshtml %}

<body>
    //....
    //....
    @RenderBody()
    @(Html.EJ().ScriptManager())
</body>
{% endhighlight %}

### Control Initialization

Before initializing, empty the contents of **Index.cshtml** file under **Views > Home** folder and add the following codes. Register the namespaces at the top of the page and then add the control.

{% highlight cshtml %}

@using Syncfusion.JavaScript;

@Html.EJ().Pivot().PivotChart("PivotChart1").Url(Url.Content("/Relational")).Size(size=>size.Width("950px").Height("460px"))

<style>
    #PivotChart1 {
        width:950px;
        height:460px;
    }
</style>

{% endhighlight %}

The **“Url”** property in PivotChart control points the service endpoint, where data are processed and fetched in the form of JSON. The services used in PivotChart control as endpoint are WCF and WebAPI.

N> The above "Index.cshtml" contains WebAPI URL, which is "/Relational". If WCF service is used as endpoint, the URL would look like "/RelationalService.svc".


### WebAPI

**Adding a WebAPI Controller**

To add a WebAPI controller in an existing MVC Web Application, right-click on the project in Solution Explorer and select **Add > New Item**. In the **Add New Item** window, select **WebAPI Controller Class** and name it as **“RelationalController.cs”**, click **Add**.

Now, WebAPI controller is added to the application successfully with the file **“RelationalController.cs”**.

N> While adding WebAPI Controller Class, name it with the suffix ‘Controller’ which is mandatory. For example, in this demo the controller is named as “RelationalController”.

Next, remove all the existing methods such as "Get", "Post", "Put" and "Delete" present inside `RelationalController.cs` file.

{% highlight c# %}

namespace PivotChartDemo
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

namespace PivotChartDemo
{
    public class RelationalController : ApiController
    {

    }
}
{% endhighlight %}

**Datasource Initialization**

A simple collection is provided as a datasource for the PivotChart in this demo section. This datasource is placed inside a separate class “ProductSales” in `RelationalController.cs` file. Refer to the following code example.

{% highlight c# %}

namespace PivotChartDemo {
    //....
    //....
    internal class ProductSales
    {
        public string Product
        {
            get;
            set;
        }

        public string Date
        {
            get;
            set;
        }

        public string Country
        {
            get;
            set;
        }

        public string State
        {
            get;
            set;
        }

        public int Quantity
        {
            get;
            set;
        }

        public double Amount
        {
            get;
            set;
        }

        public static ProductSalesCollection GetSalesData()
        {
            /// Geography
            string[] countries = new string[] { "Australia", "Canada", "France", "Germany", "United Kingdom", "United States" };
            string[] ausStates = new string[] { "New South Wales", "Queensland", "South Australia", "Tasmania", "Victoria" };
            string[] canadaStates = new string[] { "Alberta", "British Columbia", "Brunswick", "Manitoba", "Ontario", "Quebec" };
            string[] franceStates = new string[] { "Charente-Maritime", "Essonne", "Garonne (Haute)", "Gers" };
            string[] germanyStates = new string[] { "Bayern", "Brandenburg", "Hamburg", "Hessen", "Nordrhein-Westfalen", "Saarland" };
            string[] ukStates = new string[] { "England" };
            string[] ussStates = new string[] { "New York", "North Carolina", "Alabama", "California", "Colorado", "New Mexico", "South Carolina" };

            /// Time
            string[] dates = new string[] { "FY 2005", "FY 2006", "FY 2007", "FY 2008", "FY 2009" };

            /// Products
            string[] products = new string[] { "Bike", "Van", "Car" };
            Random r = new Random(123345345);

            int numberOfRecords = 2000;
            ProductSalesCollection listOfProductSales = new ProductSalesCollection();
            for (int i = 0; i < numberOfRecords; i++)
            {
                ProductSales sales = new ProductSales();
                sales.Country = countries[r.Next(1, countries.GetLength(0))];
                sales.Quantity = r.Next(1, 12);
                /// 1 percent discount for 1 quantity
                double discount = (30000 * sales.Quantity) * (double.Parse(sales.Quantity.ToString()) / 100);
                sales.Amount = (30000 * sales.Quantity) - discount;
                sales.Date = dates[r.Next(r.Next(dates.GetLength(0) + 1))];
                sales.Product = products[r.Next(r.Next(products.GetLength(0) + 1))];
                switch (sales.Product)
                {
                    case "Car":
                        {
                            sales.Date = "FY 2005";
                            break;
                        }
                }
                switch (sales.Country)
                {
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

        public override string ToString()
        {
            return string.Format("{0}-{1}-{2}", this.Country, this.State, this.Product);
        }

        public class ProductSalesCollection : List<ProductSales> { }
    }
}
{% endhighlight %}


**Service methods in WebAPI Controller**

Define the service methods inside RelationalController class, found inside `RelationalController.cs` file, created while adding WebAPI Controller Class to the Application.

{% highlight c# %}

namespace PivotChartDemo {
    public class RelationalController: ApiController {
        PivotChart pivotChart = new PivotChart();

        [System.Web.Http.ActionName("InitializeChart")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> InitializeChart(Dictionary<string, object> jsonResult)
        {
            this.BindData();
            return pivotChart.GetJsonData(jsonResult["action"].ToString(), ProductSales.GetSalesData());
        }

        [System.Web.Http.ActionName("DrillChart")]
        [System.Web.Http.HttpPost]
        public Dictionary<string, object> DrillChart(Dictionary<string, object> jsonResult)
        {
            this.BindData();
            return pivotChart.GetJsonData(jsonResult["action"].ToString(), ProductSales.GetSalesData(), jsonResult["drilledSeries"].ToString());
        }

        private void BindData()
        {
            this.pivotChart.PivotEngine.PivotRows.Add(new PivotItem { FieldMappingName = "Country", FieldHeader = "Country", TotalHeader = "Total" });
            this.pivotChart.PivotEngine.PivotRows.Add(new PivotItem { FieldMappingName = "State", FieldHeader = "State", TotalHeader = "Total" });
            this.pivotChart.PivotEngine.PivotColumns.Add(new PivotItem { FieldMappingName = "Product", FieldHeader = "Product", TotalHeader = "Total" });
            this.pivotChart.PivotEngine.PivotCalculations.Add(new PivotComputationInfo { CalculationName = "Amount", Description = "Amount", FieldHeader = "Amount", FieldName = "Amount", Format = "C", SummaryType = Syncfusion.PivotAnalysis.Base.SummaryType.DoubleTotalSum });
        }
    }
    .....
    ..... // Datasource initialization
    .....
}

{% endhighlight %}

**Configure routing in WebAPIConfig Class**

Open the WebAPIConfig.cs file found in **App_Start** folder. Then routing could be configured as shown in the following code example.

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

Now, **PivotChart** will be rendered with amount over a set of products across different customer geographic locations.

![ASP NET MVC pivot chart control in relational server mode](Relational-Getting-Started_images/ServerMode.png)

### WCF

This section demonstrates the utilization of WCF service as endpoint binding Relational datasource to a simple PivotChart. For more details on this topic, [click here](https://help.syncfusion.com/aspnetmvc/PivotChart/relational-connectivity#wcf).


