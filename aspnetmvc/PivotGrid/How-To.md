---
layout: post
title: How to
description: How to
platform: ejmvc
control: PivotGrid
documentation: ug
---

# How to

## Configure pivot grid through the model properties

There comes a time when you want to set pivot grid properties other than using `PivotGridPropertiesBuilder` i.e., in the Controller side. At that time, you can pass `PivotGridProperties` model instance as a parameter to the pivot grid helper method.

We can set properties to pivot grid control in server-side using the `PivotGridProperties` class and it is used in the view page with the help of pivot grid helper overload.

In addition to the `id` parameter of pivot grid helper method, we can also pass `PivotGridProperties` model as another parameter to the pivot grid helper method.

### Relational

The following code example explains how to render the pivot grid control in relational mode.

{% tabs %}

{% highlight razor %}

    @model Syncfusion.JavaScript.Models.PivotGridProperties
    @(Html.EJ().Pivot().PivotGrid("PivotGrid", Model))

    <script type="text/javascript">

            function load(args) {
                args.model.dataSource.data = pivot_dataset;
            }

    </script>

{% endhighlight  %}

{% highlight c# %}

namespace PivotGrid
{
    public class PivotGridController: Controller
    {
        public ActionResult PivotGridFeatures()
        {
            Syncfusion.JavaScript.Models.PivotGridProperties pgrid = new Syncfusion.JavaScript.Models.PivotGridProperties();

            PivotDataSource pgridDS = new PivotDataSource();

            List<Field> rows = new List<Field>();
            rows.Add(new Field() { FieldName = "Country", FieldCaption = "Country" });
            rows.Add(new Field() { FieldName = "State", FieldCaption = "State" });
            pgridDS.Rows = rows;

            List<Field> cols = new List<Field>();
            cols.Add(new Field() { FieldName = "Product", FieldCaption = "Product" });
            pgridDS.Columns = cols;

            pgrid.Load = "load";

            List<Field> values = new List<Field>();
            values.Add(new Field() { FieldName = "Amount" });
            pgridDS.Values = values;
            pgrid.DataSource = pgridDS;
            return View(pgrid);
        }
    }
}

{% endhighlight  %}

{% endtabs %}

As a result of the previous code example, the pivot grid will be displayed as shown below:

![purejs](How_To_images/purejs.png)

### OLAP

The following code example explains how to render the pivot grid control in OLAP mode.

{% tabs %}

{% highlight razor %}

    @model Syncfusion.JavaScript.Models.PivotGridProperties
    @(Html.EJ().Pivot().PivotGrid("PivotGrid", Model))

{% endhighlight  %}

{% highlight c# %}

namespace PivotGrid
{
    public class PivotGridController: Controller
    {
        public ActionResult PivotGridFeatures()
        {
            Syncfusion.JavaScript.Models.PivotGridProperties pgrid = new Syncfusion.JavaScript.Models.PivotGridProperties();

            PivotDataSource pgridDS = new PivotDataSource();
            pgridDS.Data = "https://bi.syncfusion.com/olap/msmdpump.dll";
            pgridDS.Cube = "Adventure Works";
            pgridDS.Catalog = "Adventure Works DW 2008 SE";


            List<Field> rows = new List<Field>();
            rows.Add(new Field() { FieldName = "[Date].[Fiscal]" });
            pgridDS.Rows = rows;

            List<Field> cols = new List<Field>();
            cols.Add(new Field() { FieldName = "[Customer].[Customer Geography]" });
            pgridDS.Columns = cols;


            List<MeasuresItems> measures = new List<MeasuresItems>();
            measures.Add(new MeasuresItems() { FieldName = "[Measures].[Internet Sales Amount]" });
            List<Field> values = new List<Field>();
            values.Add(new Field() { Measures = measures, Axis = Syncfusion.JavaScript.AxisName.Column });
            pgridDS.Values = values;
            pgrid.DataSource = pgridDS;
            return View(pgrid);
        }
    }
}

{% endhighlight  %}

{% endtabs %}

As a result of the previous code example, the pivot grid will be displayed as shown below:

![OlapClientside](How_To_images/OlapClientside.png)