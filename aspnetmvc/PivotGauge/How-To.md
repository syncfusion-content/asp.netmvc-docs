---
layout: post
title: How to
description: How to
platform: ejmvc
control: PivotGauge
documentation: ug
---
# How to

## Configure pivot gauge through the model properties

There comes a time when you want to set pivot gauge properties other than using `PivotGaugePropertiesBuilder` i.e., in the Controller side. At that time, you can pass `PivotGaugeProperties` model instance as a parameter to the pivot gauge helper method.

We can set properties to pivot gauge control in server-side using the `PivotGaugeProperties` class and it is used in the view page with the help of pivot gauge helper overload.

In addition to the `id` parameter of pivot gauge helper method, we can also pass `PivotGaugeProperties` model as another parameter to the pivot gauge helper method.

### Relational

The following code example explains how to render the pivot gauge control in relational mode.

{% tabs %}

{% highlight razor %}

    @model Syncfusion.JavaScript.Models.PivotGaugeProperties
    @(Html.EJ().Pivot().PivotGauge("PivotGauge", Model))

    <script type="text/javascript">

            function load(args) {
                args.model.dataSource.data = pivot_dataset;
            }

    </script>

{% endhighlight  %}

{% highlight c# %}

namespace PivotGauge
{
    public class PivotGaugeController: Controller
    {
        public ActionResult PivotGaugeFeatures()
        {
            Syncfusion.JavaScript.Models.PivotGaugeProperties pgauge = new Syncfusion.JavaScript.Models.PivotGaugeProperties();

            PivotDataSource pgaugeDS = new PivotDataSource();

            List<Field> rows = new List<Field>();
            rows.Add(new Field() { FieldName = "Country", FieldCaption = "Country" });
            rows.Add(new Field() { FieldName = "State", FieldCaption = "State" });
            pgaugeDS.Rows = rows;

            List<Field> cols = new List<Field>();
            cols.Add(new Field() { FieldName = "Product", FieldCaption = "Product" });
            pgaugeDS.Columns = cols;

            pgauge.Load = "load";

            List<Field> values = new List<Field>();
            values.Add(new Field() { FieldName = "Amount" });
            pgaugeDS.Values = values;
            pgauge.DataSource = pgaugeDS;
            return View(pgauge);
        }
    }
}

{% endhighlight  %}

{% endtabs %}

As a result of the previous code example, the pivot gauge will be displayed as shown below:

![PopulatePivotGaugeWithData](How_To_images/PopulatePivotGaugeWithData.png)

### OLAP

The following code example explains how to render the pivot gauge control in OLAP mode.

{% tabs %}

{% highlight razor %}

    @model Syncfusion.JavaScript.Models.PivotGaugeProperties
    @(Html.EJ().Pivot().PivotGauge("PivotGauge", Model))

{% endhighlight  %}

{% highlight c# %}

namespace PivotGauge
{
    public class PivotGaugeController: Controller
    {
        public ActionResult PivotGaugeFeatures()
        {
            Syncfusion.JavaScript.Models.PivotGaugeProperties pgauge = new Syncfusion.JavaScript.Models.PivotGaugeProperties();

            PivotDataSource pgaugeDS = new PivotDataSource();
            pgaugeDS.Data = "https://bi.syncfusion.com/olap/msmdpump.dll";
            pgaugeDS.Cube = "Adventure Works";
            pgaugeDS.Catalog = "Adventure Works DW 2008 SE";


            List<Field> rows = new List<Field>();
            rows.Add(new Field() { FieldName = "[Date].[Fiscal]" });
            pgaugeDS.Rows = rows;

            List<Field> cols = new List<Field>();
            cols.Add(new Field() { FieldName = "[Customer].[Customer Geography]" });
            pgaugeDS.Rows = cols;


            List<MeasuresItems> measures = new List<MeasuresItems>();
            measures.Add(new MeasuresItems() { FieldName = "[Measures].[Internet Sales Amount]" });
            List<Field> values = new List<Field>();
            values.Add(new Field() { Measures = measures, Axis = Syncfusion.JavaScript.AxisName.Column });
            pgaugeDS.Values = values;
            pgauge.DataSource = pgaugeDS;
            return View(pgauge);
        }
    }
}

{% endhighlight  %}

{% endtabs %}

As a result of the previous code example, the pivot gauge will be displayed as shown below:

![PopulatePivotGaugeWithDataSource](How_To_images/PopulatePivotGaugeWithDataSource.png)