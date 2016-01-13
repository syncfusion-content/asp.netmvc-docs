---
layout: post
title: Report Parameters | ReportViewer | ASP.NET MVC | Syncfusion
description: report parameters
platform: ejmvc
control: ReportViewer
documentation: ug
---

# Report Parameters

The ReportViewer has support to add report parameters to ReportViewer at runtime. The ReportViewer has Parameters property that is the list of ReportParameter type to add collection of report parameters to it. You can add report parameters either through ReportViewer model when creating ReportViewer control or through Web API.

The following code example illustrates how to add ReportParameter at control creation.

{% highlight CSHTML %}

@(Html.EJ().ReportViewer("viewer").ProcessingMode(Syncfusion.JavaScript.ReportViewerEnums.ProcessingMode.Remote)
.ReportPath("InvoiceTemplate.rdl")
.ReportServiceUrl("/api/ReportApi")
.Parameters(param => {param.Name("InvoiceID").Labels(new List<string>() { "InvoiceID" }).Values(new List<string>() { "10250" }).Add();}))

{% endhighlight %}

The following code example illustrates how to add ReportParameter in Web API.


{% highlight C# %}

public class ReportsController : ApiController, IReportController
{
    /// <summary>
    /// Report Initialization method that is triggered when report begins to be processed.
    /// </summary>
    /// <param name="reportOptions">The ReportViewer options.</param>
    public void OnInitReportOptions(ReportViewerOptions reportOptions)
    {
        List<ReportParameter> parameters = new List<ReportParameter>();
        parameters.Add(new ReportParameter() { Name = "InvoiceID", Labels = new List<string>() { "InvoiceID" }, Values = new List<string>() { "10250" } });
        reportOptions.ReportModel.Parameters = parameters;
    }        
}

{% endhighlight %}