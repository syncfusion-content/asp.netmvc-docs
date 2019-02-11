---
layout: post
title: How to | PivotClient | ASP.NET MVC | Syncfusion
description: How to
platform: ejmvc
control: PivotClient
documentation: ug
---
# How to

## Configure pivot client through the model properties

There comes a time when you want to set pivot client properties other than using `PivotClientPropertiesBuilder` i.e., in the Controller side. At that time, you can pass `PivotClientProperties` model instance as a parameter to the pivot client helper method.

We can set properties to pivot client control in server-side using the `PivotClientProperties` class and it is used in the view page with the help of pivot client helper overload.

In addition to the `id` parameter of pivot client helper method, we can also pass `PivotClientProperties` model as another parameter to the pivot client helper method.

### Relational

The following code example explains how to render the pivot client control in relational mode.

{% tabs %}

{% highlight razor %}

    @model Syncfusion.JavaScript.Models.PivotClientProperties
    @(Html.EJ().Pivot().PivotClient("PivotClient", Model))


    <script type="text/javascript">

        function load(args) {
            args.model.dataSource.data = pivot_dataset;
        }

    </script>

{% endhighlight  %}

{% highlight c# %}

namespace PivotClient
{
    public class PivotClientController: Controller
    {
        public ActionResult PivotClientFeatures()
        {
            Syncfusion.JavaScript.Models.PivotClientProperties pivotclient = new Syncfusion.JavaScript.Models.PivotClientProperties();

            PivotDataSource pivotclientDS = new PivotDataSource();

            List<Field> rows = new List<Field>();
            rows.Add(new Field() { FieldName = "Country", FieldCaption = "Country" });
            rows.Add(new Field() { FieldName = "State", FieldCaption = "State" });
            pivotclientDS.Rows = rows;

            List<Field> cols = new List<Field>();
            cols.Add(new Field() { FieldName = "Product", FieldCaption = "Product" });
            pivotclientDS.Columns = cols;

             pivotclient.Load = "load";

            List<Field> values = new List<Field>();
            values.Add(new Field() { FieldName = "Amount" });
            pivotclientDS.Values = values;
            pivotclient.DataSource = pivotclientDS;
            return View(pivotclient);
        }
    }
}

{% endhighlight  %}

{% endtabs %}

As a result of the previous code example, the pivot client will be displayed as shown below:

![purejs](How_To_images/purejs.png)

### OLAP

The following code example explains how to render the pivot client control in OLAP mode.

{% tabs %}

{% highlight razor %}

    @model Syncfusion.JavaScript.Models.PivotClientProperties
    @(Html.EJ().Pivot().PivotClient("PivotClient", Model))

{% endhighlight  %}

{% highlight c# %}

namespace PivotClient
{
    public class PivotClientController: Controller
    {
        public ActionResult PivotClientFeatures()
        {
            Syncfusion.JavaScript.Models.PivotClientProperties pivotclient = new Syncfusion.JavaScript.Models.PivotClientProperties();

            PivotDataSource pivotclientDS = new PivotDataSource();
            pivotclientDS.Data = "https://bi.syncfusion.com/olap/msmdpump.dll";
            pivotclientDS.Cube = "Adventure Works";
            pivotclientDS.Catalog = "Adventure Works DW 2008 SE";


            List<Field> rows = new List<Field>();
            rows.Add(new Field() { FieldName = "[Date].[Fiscal]" });
            pivotclientDS.Rows = rows;

            List<Field> cols = new List<Field>();
            cols.Add(new Field() { FieldName = "[Customer].[Customer Geography]" });
            pivotclientDS.Columns = cols;

            List<MeasuresItems> measures = new List<MeasuresItems>();
            measures.Add(new MeasuresItems() { FieldName = "[Measures].[Internet Sales Amount]" });
            List<Field> values = new List<Field>();
            values.Add(new Field() { Measures = measures, Axis = Syncfusion.JavaScript.AxisName.Column });
            pivotclientDS.Values = values;
            pivotclient.DataSource = pivotclientDS;
            return View(pivotclient);
        }
    }
}

{% endhighlight  %}

{% endtabs %}

As a result of the previous code example, the pivot client will be displayed as shown below:

![OlapClientside](How_To_images/OlapClientside.png)