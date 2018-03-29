---
layout: post
title: How to
description: How to
platform: ejmvc
control: PivotChart
documentation: ug
---

# How to

## Configure pivot chart through the model properties

There comes a time when you want to set pivot chart properties other than using `PivotChartPropertiesBuilder` i.e., in the Controller side. At that time, you can pass `PivotChartProperties` model instance as a parameter to the pivot chart helper method.

We can set properties to pivot chart control in server-side using the `PivotChartProperties` class and it is used in the view page with the help of pivot chart helper overload.

In addition to the `id` parameter of pivot chart helper method, we can also pass `PivotChartProperties` model as another parameter to the pivot chart helper method.

### Relational

The following code example explains how to render the pivot chart control in relational mode.

{% tabs %}

{% highlight razor %}

    @model Syncfusion.JavaScript.Models.PivotChartProperties
    @(Html.EJ().Pivot().PivotChart("PivotChart", Model))

    <script type="text/javascript">

        function load(args) {
            args.model.dataSource.data = pivot_dataset;
        }

    </script>

{% endhighlight  %}

{% highlight c# %}

namespace PivotChart
{
    public class PivotChartController: Controller
    {
        public ActionResult PivotChartFeatures()
        {
            Syncfusion.JavaScript.Models.PivotChartProperties pchart = new Syncfusion.JavaScript.Models.PivotChartProperties();

            PivotDataSource pchartDS = new PivotDataSource();

            List<Field> rows = new List<Field>();
            rows.Add(new Field() { FieldName = "Country", FieldCaption = "Country" });
            rows.Add(new Field() { FieldName = "State", FieldCaption = "State" });
            pchartDS.Rows = rows;

            List<Field> cols = new List<Field>();
            cols.Add(new Field() { FieldName = "Product", FieldCaption = "Product" });
            pchartDS.Columns = cols;

            pchart.Load = "load";

            List<Field> values = new List<Field>();
            values.Add(new Field() { FieldName = "Amount" });
            pchartDS.Values = values;
            pchart.DataSource = pchartDS;
            return View(pchart);
        }
    }
}

{% endhighlight  %}

{% endtabs %}

As a result of the previous code example, the pivot chart will be displayed as shown below:

![PopulatePivotChartWithData](How_To_images/PopulatePivotChartWithData.png)

### OLAP

The following code example explains how to render the pivot chart control in OLAP mode.

{% tabs %}

{% highlight razor %}

    @model Syncfusion.JavaScript.Models.PivotChartProperties
    @(Html.EJ().Pivot().PivotChart("PivotChart", Model))

{% endhighlight  %}

{% highlight c# %}

namespace PivotChart
{
    public class PivotChartController: Controller
    {
        public ActionResult PivotChartFeatures()
        {
            Syncfusion.JavaScript.Models.PivotChartProperties pchart = new Syncfusion.JavaScript.Models.PivotChartProperties();

            PivotDataSource pchartDS = new PivotDataSource();
            pchartDS.Data = "https://bi.syncfusion.com/olap/msmdpump.dll";
            pchartDS.Cube = "Adventure Works";
            pchartDS.Catalog = "Adventure Works DW 2008 SE";


            List<Field> rows = new List<Field>();
            rows.Add(new Field() { FieldName = "[Date].[Fiscal]" });
            pchartDS.Rows = rows;

            List<Field> cols = new List<Field>();
            cols.Add(new Field() { FieldName = "[Customer].[Customer Geography]" });
            pchartDS.Rows = cols;


            List<MeasuresItems> measures = new List<MeasuresItems>();
            measures.Add(new MeasuresItems() { FieldName = "[Measures].[Internet Sales Amount]" });
            List<Field> values = new List<Field>();
            values.Add(new Field() { Measures = measures, Axis = Syncfusion.JavaScript.AxisName.Column });
            pchartDS.Values = values;
            pchart.DataSource = pchartDS;
            return View(pchart);
        }
    }
}

{% endhighlight  %}

{% endtabs %}

As a result of the previous code example, the pivot chart will be displayed as shown below:

![PopulatePivotChartWithDataSource](How_To_images/PopulatePivotChartWithDataSource.png)