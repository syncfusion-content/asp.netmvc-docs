---
layout: post
title: SSRS-Configuration
description: ssrs configuration
platform: ejmvc
control: ReportViewer
documentation: ug
---

# SSRS Configuration

The ReportViewer has support to load RDL/RDLC reports from SSRS server. You have to set your SSRS server URL to ReportViewer’sreportServerUrl property and set the relative path of RDL/RDLC file in SSRS to ReportViewer’sreportPath property. 

{% highlight c# %}

[EJMVC]

@(Html.EJ().ReportViewer("viewer").ProcessingMode(Syncfusion.JavaScript.ReportViewerEnums.ProcessingMode.Remote)
.ReportServiceUrl("/api/SSRSReport")
.ReportServerUrl("http://76.74.153.81/ReportServer")
.ReportPath("/SSRSSamples2/Territory Sales New ")) 

{% endhighlight %}

## Network Credentials for SSRS

The Network credentials can be given at WebAPI Controller to connect the SSRS server.

{% highlight c# %}

                   /// <summary>

        /// Report Initialization method that is triggered when report begins to process.

        /// </summary>

        /// <param name="reportOptions">The ReportViewer options.</param>

        public void OnInitReportOptions(ReportViewerOptions reportOptions)

        {

           //Adds SSRS Server and Database Credentials here.

            reportOptions.ReportModel.ReportServerCredential = new System.Net.NetworkCredential("ssrs", "RDLReport1");

            reportOptions.ReportModel.DataSourceCredentials.Add(new DataSourceCredentials("AdventureWorks", "ssrs1", "RDLReport1"));

        }

{% endhighlight %}

> Note: DataSource credentials must be added to the ReportViewer for Shared DataSources that do not have credentials in the connection string and used in the SSRS Reports.