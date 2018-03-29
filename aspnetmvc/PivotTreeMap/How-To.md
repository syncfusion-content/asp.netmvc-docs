---
layout: post
title: How to
description: How to
platform: ejmvc
control: PivotTreeMap
documentation: ug
---
# How to

## Configure pivot tree map through the model properties

There comes a time when you want to set pivot tree map properties other than using `PivotTreeMapPropertiesBuilder` i.e., in the Controller side. At that time, you can pass `PivotTreeMapProperties` model instance as a parameter to the pivot tree map helper method.

We can set properties to pivot tree map control in server-side using the `PivotTreeMapProperties` class and it is used in the view page with the help of pivot tree map helper overload.

In addition to the `id` parameter of pivot tree map helper method, we can also pass `PivotTreeMapProperties` model as another parameter to the pivot tree map helper method.

The following code example explains how to render the pivot tree map control in relational mode.

The following code example which will explain to render the pivot tree map control.

{% tabs %}

{% highlight razor %}

    @model Syncfusion.JavaScript.Models.PivotTreeMapProperties
    @(Html.EJ().Pivot().PivotTreeMap("PivotTreeMap", Model))

{% endhighlight  %}

{% highlight c# %}

namespace PivotTreeMap
{
    public class PivotTreeMapController: Controller
    {
        public ActionResult PivotTreeMapFeatures()
        {
            Syncfusion.JavaScript.Models.PivotTreeMapProperties ptreemap = new Syncfusion.JavaScript.Models.PivotTreeMapProperties();

            PivotDataSource ptreemapDS = new PivotDataSource();
            ptreemapDS.Data = "https://bi.syncfusion.com/olap/msmdpump.dll";
            ptreemapDS.Cube = "Adventure Works";
            ptreemapDS.Catalog = "Adventure Works DW 2008 SE";


            List<Field> rows = new List<Field>();
            rows.Add(new Field() { FieldName = "[Date].[Fiscal]" });
            ptreemapDS.Rows = rows;

            List<Field> cols = new List<Field>();
            cols.Add(new Field() { FieldName = "[Customer].[Customer Geography]" });
            ptreemapDS.Columns = cols;


            List<MeasuresItems> measures = new List<MeasuresItems>();
            measures.Add(new MeasuresItems() { FieldName = "[Measures].[Internet Sales Amount]" });
            List<Field> values = new List<Field>();
            values.Add(new Field() { Measures = measures, Axis = Syncfusion.JavaScript.AxisName.Column });
            ptreemapDS.Values = values;
            ptreemap.DataSource = ptreemapDS;
            return View(ptreemap);
        }
    }
}

{% endhighlight  %}

{% endtabs %}

As a result of the previous code example, the pivot tree map will be displayed as shown below:

![OlapClientside](Getting-Started_images/OlapClientside.png)