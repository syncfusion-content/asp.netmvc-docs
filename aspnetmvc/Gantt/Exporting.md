---
layout: post
title: Exporting| Gantt | ASP.NET MVC | Syncfusion
description: exporting
platform: ejmvc
control: Gantt
documentation: ug
---
# Export

Exporting feature provides support to export Gantt content to excel and PDF files. To export the contents, the `ExcelExport` and `PdfExport` toolbar items must be added in the toolbar using the `ToolbarItems` property of `ToolbarSettings`. When you click, the toolbar exporting icons, it internally invokes the export public method of Gantt object to export.

The below code snippet explains the above behavior,

{% tabs %}
{% highlight razor %}

@(Html.EJ().Gantt("GanttContainer")
//...
.ToolbarSettings(tool =>
 {
       tool.ShowToolbar(true);
       tool.ToolbarItems(new List<GanttToolBarItems>()
       {                      
	      GanttToolBarItems.PdfExport, 
	      GanttToolBarItems.ExcelExport
       });
 })
.Datasource(ViewBag.datasource)
)

{% endhighlight %}

{% highlight c# %}

public partial class GanttController : Controller
    {
        public ActionResult GanttExporting()
        {
            ViewBag.datasource = this.GetDataSource();
            return View();
        }
        public void ExportToPdf(string GanttModel)
        {
            PdfExport exp = new PdfExport();
            var datasource = this.DataSource();
            GanttProperties obj = ConvertGanttObject(GanttModel);
            GanttPdfExportSettings settings = new GanttPdfExportSettings();
            settings.Theme = GanttExportTheme.FlatSaffron;
            settings.Locale = Request.Form["locale"];
            exp.Export(obj, datasource, settings, "Gantt");
        }
        public void ExportToExcel(string GanttModel)
        {
            ExcelExport exp = new ExcelExport();
            var DataSource = this.GetEditingDataSource();
            GanttProperties obj = ConvertGanttObject(GanttModel);
            exp.Export(obj, DataSource, "GanttExport.xlsx", ExcelVersion.Excel2010, new GanttExportSettings() { Theme = ExportTheme.FlatSaffron });
        }

        private GanttProperties ConvertGanttObject(string gridProperty)
        {
            JavaScriptSerializer serializer = new JavaScriptSerializer();
            IEnumerable div = (IEnumerable)serializer.Deserialize(gridProperty, typeof(IEnumerable));
            GanttProperties gridProp = new GanttProperties();
            foreach (KeyValuePair<string, object> dataSource in div)
            {
                var property = gridProp.GetType().GetProperty(dataSource.Key, BindingFlags.Instance | BindingFlags.Public | BindingFlags.IgnoreCase);
                if (property != null)
                {
                    Type type = property.PropertyType;
                    string serialize = serializer.Serialize(dataSource.Value);
                    object value = serializer.Deserialize(serialize, type);
                    property.SetValue(gridProp, value, null);
                }
            }
            return gridProp;
        }
    }

{% endhighlight %}
{% endtabs %} 

The below screen shot shows Gantt with excel and Pdf exporting enabled.
![](Export_images/Export_img1.png)

## Server dependencies
Export Helper functions are available in the Assembly `Syncfusion.EJ.Export`, which is available in the Essential Studio & Essential ASP.NET MVC builds. The list of assemblies needed for Gantt Export as follows

* Syncfusion.EJ
* Syncfusion.EJ.Export
* Syncfusion.Linq.Base
* Syncfusion.Compression.Base
* Syncfusion.XlsIO.Base
* Syncfusion.PDF.Base

## Supported Export Types
Currently server helper function allows following two types of exporting.

* Excel
* PDF

## Export Mapper in MVC
Mappers is used to change the default routing path for exporting. By using `Mappers` you can change any action name in controller and the action can be in any controller (Need not to be in Gantt View Page Controller).

{% tabs %} 
{% highlight razor %}

@(Html.EJ().Gantt("GanttContainer")
//...
.Mappers(map => map.ExportToPdfAction("PdfAction").ExportToExcelAction("ExcelAction"))
.ToolbarSettings(tool =>
 {
        tool.ShowToolbar(true);
        tool.ToolbarItems(new List<GanttToolBarItems>()
        {                      
              GanttToolBarItems.PdfExport,
	GanttToolBarItems.ExcelExport

        });
 })
//...
)

{% endhighlight %}

{% highlight c# %}

    public partial class GanttController : Controller
    {
        public void PdfAction(string GanttModel)
        {
            PdfExport exp = new PdfExport();
            var DataSource = this.GetEditingDataSource();
            GanttProperties obj = ConvertGanttObject(GanttModel);
            GanttPdfExportSettings settings = new GanttPdfExportSettings();
            settings.Theme = GanttExportTheme.FlatSaffron;
            settings.Locale = sRequest.Form["locale"];
            exp.Export(obj, DataSource, settings, "Gantt");
        }

       public void ExcelAction(string GanttModel)
        {
            ExcelExport exp = new ExcelExport();
            var DataSource = this.GetEditingDataSource();
            GanttProperties obj = ConvertGanttObject(GanttModel);
            exp.Export(obj, DataSource, "GanttExport.xlsx", ExcelVersion.Excel2010, new GanttExportSettings() { Theme = ExportTheme.FlatSaffron });
        }

    }

{% endhighlight %}
{% endtabs %} 

## Multiple exporting
Multiple export is used for export more than one Gantt object in the same file. Multiple export in Gantt can be enabled by setting `AllowMultipleExporting` property to `true`. Gantt properties of all the Gantt which are available in current page are passed as string array parameter to controller action method.


The following code example describes exporting multiple Gantt in PDF format

{% tabs %} 
{% highlight razor %}

@(Html.EJ().Gantt("GanttContainer")
//...
.AllowMultipleExporting(true)
.ToolbarSettings(tool =>
 {
        tool.ShowToolbar(true);
        tool.ToolbarItems(new List<GanttToolBarItems>()
        {                      
              GanttToolBarItems.PdfExport
        });
 })
 .Mappers(map => map.ExportToPdfAction("MultipleExportToPDF")
.Datasource(ViewBag.datasource)
)

@(Html.EJ().Gantt("GanttContainer1")
//...
 .Datasource(ViewBag.datasource1)
)

@(Html.EJ().Gantt("GanttContainer2")
//...
.Datasource(ViewBag.datasource2)
)

{% endhighlight %}

{% highlight c# %}

public partial class GanttController : Controller
    {

        public void MultipleExportToPDF(string[] GanttModel)
        {
            PdfExport exp = new PdfExport();
            var PlanData = this.GetPlanDataSource();
            var DesignData = this.GetDesignDataSource();
            var ImplementationData = this.GetImplementationDataSource();
            PdfDocument document = null;
            GanttPdfExportSettings settings = new GanttPdfExportSettings();
            settings.Theme = GanttExportTheme.FlatSaffron;
            settings.Locale = Request.Form["locale"];
            int controlCount = 1;
            foreach (string ganttProperty in GanttModel)
            {
                GanttProperties ganttProp = this.ConvertGanttObject(ganttProperty);
                if (controlCount == 1)
                {
                    document = exp.Export(ganttProp, (IEnumerable)PlanData, settings, false);
                }
                else if (controlCount == 2)
                {
                    document = exp.Export(ganttProp, (IEnumerable)DesignData, settings, document, false);
                }
                else
                {
                    exp.Export(ganttProp, (IEnumerable)ImplementationData, settings, "Gantt", document, true);
                }
                count++;
            }
        }
}

{% endhighlight %}
{% endtabs %} 

## Export Theme
The Gantt export supports the below themes, 

* flat-azure
* flat-azure-dark
* flat-lime
* flat-lime-dark
* flat-saffron
* flat-saffron-dark
* gradient-azure
* gradient-azure-dark
* gradient-lime
* gradient-lime-dark
* gradient-saffron
* gradient-saffron-dark
* bootstrap-theme

The desired theme should be passed as a parameter to the Export method and the code snippet for this as follows

{% highlight c# %}

public void ExportToExcel(string GanttModel)
{
    ExcelExport exp = new ExcelExport();
    var DataSource = this.GetEditingDataSource();
    GanttProperties obj = ConvertGanttObject(GanttModel);
    exp.Export(obj, DataSource, "GanttExport.xlsx", ExcelVersion.Excel2010, new GanttExportSettings() { Theme = ExportTheme.FlatSaffron });
}

{% endhighlight %}