---
layout: post
title: Exporting
description: exporting
platform: ejmvc
control: Grid
documentation: ug
---

# Exporting

Exporting feature provides support to export Grid data into excel, word and pdf files. The tool bar has ExcelExport, WordExport, PdfExport icons that are used to perform exporting. When you click the toolbar exporting icon, it internally invokes the export() public method of Grid object to export. You can also invoke export() method manually to export.

## MVC

In MVC, exporting is achieved by using action controller method. In controller method, Grid property is passed as string parameter. You need to serialize it into the Grid Property. By using the Export() server method, you can export the Grid into excel, pdf and word documents.
{% highlight js %}

  @(Html.EJ().Grid<OrdersView>("FlatGrid")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

                .ToolbarSettings(toolBar => toolBar.ShowToolbar().ToolbarItems(items =>

                {

items.AddTool(ToolBarItems.ExcelExport);

                    items.AddTool(ToolBarItems.WordExport);

                    items.AddTool(ToolBarItems.PdfExport);

                }))

        .AllowPaging()

        .Columns(col =>

        {

            col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right). Add();          

    col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Add();

            col.Field("OrderDate").HeaderText("Order Date").TextAlign(TextAlign.Right). Add();

            col.Field("ShipCity").HeaderText("Ship City").Add();

        })) 

{% endhighlight  %}
{% highlight c# %}

public partial class GridController : Controller

{

	public ActionResult ExportingGrid()

    {

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            ViewBag.datasource = DataSource;

            return View();

    }

    public void ExportToExcel(string GridModel)

    {

		ExcelExport exp = new ExcelExport();

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		GridProperties obj = ConvertGridObject(GridModel);

		exp.Export(obj, DataSource, "Export.xlsx", ExcelVersion.Excel2010, false, false, "flat-saffron");

	}

	public void ExportToWord(string GridModel)

	{

		WordExport exp = new WordExport();

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		GridProperties obj = ConvertGridObject(GridModel);

		exp.Export(obj, DataSource, "Export.docx", false, false, "flat-saffron");

	}

	public void ExportToPdf(string GridModel)

	{

		PdfExport exp = new PdfExport();

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		GridProperties obj = ConvertGridObject(GridModel);

		exp.Export(obj, DataSource, "Export.pdf", false, false, "flat-saffron");

	}

	private GridProperties ConvertGridObject(string gridProperty)

	{

		JavaScriptSerializer serializer = new JavaScriptSerializer();

		IEnumerable div = (IEnumerable)serializer.Deserialize(gridProperty, typeof(IEnumerable));

		GridProperties gridProp = new GridProperties();

		foreach (KeyValuePair<string, object> ds in div)

		{

			var property = gridProp.GetType().GetProperty(ds.Key, BindingFlags.Instance | BindingFlags.Public | BindingFlags.IgnoreCase);

			if (property != null)

			{

				Type type = property.PropertyType;

				string serialize = serializer.Serialize(ds.Value);

				object value = serializer.Deserialize(serialize, type);

				property.SetValue(gridProp, value, null);

			}

		}

		return gridProp;

	} 
}

{% endhighlight  %}

Exporting the default routing path to server-side contains the action names as ExportToExcel for Excel Exporting, ExportToWord for Word Exporting and ExportToPdf for Pdf Exporting. The default controller name in routing path is the Grid view page’s Controller name. For instance, when Grid is rendered in GridFeatures View Page of Home Controller, then on Excel exporting Grid Content, the routing path is ~/Home/ExportToExcel.



### Export Mapper in MVC

Mappers Grid property is used to modify the default routing path during exporting. By using Mappers, you can use any action name in Controller for exporting and the action can be in any controller (Need not be in the Grid View Page Controller).

{% highlight js %}


 @(Html.EJ().Grid<OrdersView>("FlatGrid")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

                .ToolbarSettings(toolBar => toolBar.ShowToolbar().ToolbarItems(items =>

                {

items.AddTool(ToolBarItems.ExcelExport);

                    items.AddTool(ToolBarItems.WordExport);

                    items.AddTool(ToolBarItems.PdfExport);

                }))

          .Mappers(map => map.ExportToExcelAction("ExcelAction")

            .ExportToPdfAction("PdfAction").ExportToWordAction("WordAction")

          )

        .AllowPaging()

        .Columns(col =>

        {

            col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right). Add();          

    col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Add();

            col.Field("OrderDate").HeaderText("Order Date").TextAlign(TextAlign.Right). Add();

            col.Field("ShipCity").HeaderText("Ship City").Add();

        })) 

{% endhighlight  %}

{% highlight c# %}

public partial class GridController : Controller

    {

public ActionResult ExportingGrid()

        {

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            ViewBag.datasource = DataSource;

            return View();

        }

        public void ExcelAction(string GridModel)

        {

            ExcelExport exp = new ExcelExport();

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            GridProperties obj = ConvertGridObject(GridModel);

            exp.Export(obj, DataSource, "Export.xlsx", ExcelVersion.Excel2010, false, false, "flat-saffron");

        }

        public void WordAction(string GridModel)

        {

            WordExport exp = new WordExport();

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            GridProperties obj = ConvertGridObject(GridModel);

            exp.Export(obj, DataSource, "Export.docx", false, false, "flat-saffron");

        }

        public void PdfAction(string GridModel)

        {

            PdfExport exp = new PdfExport();

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            GridProperties obj = ConvertGridObject(GridModel);

            exp.Export(obj, DataSource, "Export.pdf", false, false, "flat-saffron");

        }

        private GridProperties ConvertGridObject(string gridProperty)

        {

            JavaScriptSerializer serializer = new JavaScriptSerializer();

            IEnumerable div = (IEnumerable)serializer.Deserialize(gridProperty, typeof(IEnumerable));

            GridProperties gridProp = new GridProperties();

            foreach (KeyValuePair<string, object> ds in div)

            {

                var property = gridProp.GetType().GetProperty(ds.Key, BindingFlags.Instance | BindingFlags.Public | BindingFlags.IgnoreCase);

                if (property != null)

                {

                    Type type = property.PropertyType;

                    string serialize = serializer.Serialize(ds.Value);

                    object value = serializer.Deserialize(serialize, type);

                    property.SetValue(gridProp, value, null);

                }

            }

            return gridProp;

        }  
}

{% endhighlight  %}

#### Customizing Themes

Themes are used to enhance the UI appearance of the grid in the exported document. There are two string and enum supports for specifying the themes. You can also export the grid without applying any styles. The various inbuilt theme options provided to be applied on the exported theme are

<table>
<tr><td><b>Enum</b></td><td><b>Equivalent string input</b></td></tr>

<tr><td>ExportTheme.FlatAzure</td><td>default-theme</td></tr>

<tr><td>ExportTheme.FlatSaffron</td><td>flat-saffron</td></tr>

<tr><td>ExportTheme.FlatLime</td><td>flat-lime</td></tr>

<tr><td>ExportTheme.FlatDarkAzure</td><td>flat-azure-dark</td></tr>

<tr><td>ExportTheme.FlatDarkSaffron</td><td>flat-saffron-dark</td></tr>

<tr><td>ExportTheme.FlatDarkLime</td><td>flat-lime-dark</td></tr>

<tr><td>ExportTheme.GradientAzure</td><td>gradient-azure</td></tr>

<tr><td>ExportTheme.GradientSaffron</td><td>gradient-saffron</td></tr>

<tr><td>ExportTheme.GradientLime</td><td>gradient-lime</td></tr>

<tr><td>ExportTheme.GradientDarkAzure</td><td>gradient-azure-dark</td></tr>

<tr><td>ExportTheme.GradientDarkSaffron</td><td>gradient-saffron-dark</td></tr>

<tr><td>ExportTheme.GradientDarkLime</td><td>gradient-lime-dark</td></tr>

<tr><td>ExportTheme.BootstrapTheme</td><td>bootstrap-theme</td></tr>

<tr><td>ExportTheme.None</td><td>none</td></tr>
</table>

{% highlight c# %}

    public partial class GridController : Controller

    {
        public void ExportToExcel(string GridModel)

        {

            ExcelExport exp = new ExcelExport();

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            GridProperties obj = Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties),GridModel);

            exp.Export(obj, DataSource, "Export.xlsx", ExcelVersion.Excel2010, false, false, "none");

        }

        public void ExportToWord(string GridModel)

        {

            WordExport exp = new WordExport();

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            GridProperties obj = Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties),GridModel);

            exp.Export(obj, DataSource, "Export.docx", false, false, ExportTheme.FlatSaffron);

        }

        public void ExportToPdf(string GridModel)

        {

            PdfExport exp = new PdfExport();

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            GridProperties obj = Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties),GridModel);

            exp.Export(obj, DataSource, "Export.pdf", false, false, "flat-saffron");

        }
        
        public ActionResult ExportingGrid()

        {

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            ViewBag.datasource = DataSource;

            return View();

        }
        
      }

{% endhighlight %}

{% highlight razor %}

    @(Html.EJ().Grid<OrdersView>("FlatGrid")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

                .ToolbarSettings(toolBar => toolBar.ShowToolbar().ToolbarItems(items =>

                {

                    items.AddTool(ToolBarItems.ExcelExport);

                    items.AddTool(ToolBarItems.WordExport);

                    items.AddTool(ToolBarItems.PdfExport);

                }))

        .AllowPaging()

        .Columns(col =>

        {

            col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right). Add();          

            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Add();

            col.Field("OrderDate").HeaderText("Order Date").TextAlign(TextAlign.Right). Add();

            col.Field("ShipCity").HeaderText("Ship City").Add();

        })) 

{% endhighlight %}

When the theme is set as none and the autoFormat is not set to the grid, then no theme is applied to the exported grid. The grid is exported without any theme as in the following screenshots:

![](Exporting_images/Customizing-Themes_img1.png)

Fig 1: Excel file – Without themes

##### AutoFormat Class



The **AutoFormat** Class can be used to customize the styles or themes applied to the exported grid. With the autoFormat class, you can provide required color to the grid content, altrow background or border color.

The customized theme is applied to the grid, only when the selected theme is either “none” or ExportTheme.None.

The various properties available under the autoFormat class are listed in the following table.

<table>
<tr>
<td>
<b>Properties</b></td><td>
<b>Type</b></td><td>
<b>Description</b></td></tr>
<tr>
<td>
FontFamily</td><td>
String</td><td>
The font name</td></tr>
<tr>
<td>
HeaderBorderColor</td><td>
System.Drawing.Color</td><td>
The border color of the grid header</td></tr>
<tr>
<td>
HeaderFontSize</td><td>
int</td><td>
The size of the grid header font</td></tr>
<tr>
<td>
GHeaderBgColor</td><td>
System.Drawing.Color</td><td>
The Column Header cell color and the Group Header Indent cell color</td></tr>
<tr>
<td>
ContentBgColor</td><td>
System.Drawing.Color</td><td>
The background color of the content</td></tr>
<tr>
<td>
ContentBorderColor</td><td>
System.Drawing.Color</td><td>
The border color of the grid content</td></tr>
<tr>
<td>
ContentFontSize</td><td>
int</td><td>
The font size of the grid content</td></tr>
<tr>
<td>
GContentFontColor</td><td>
System.Drawing.Color</td><td>
The font color of the record field cell</td></tr>
<tr>
<td>
GCaptionBorderColor</td><td>
System.Drawing.Color</td><td>
The border color of the group caption cell</td></tr>
<tr>
<td>
AltRowBgColor</td><td>
System.Drawing.Color</td><td>
The background color of the alternative row of the grid content</td></tr>
</table>

{% highlight c# %}

    public partial class GridController : Controller

    {

        public void ExportToExcel(string GridModel)

        {

            ExcelExport exp = new ExcelExport();

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            GridProperties obj = ConvertGridObject(GridModel);

            exp.Export(obj, DataSource, "Export.xlsx", ExcelVersion.Excel2010, false, false, "none");

        }

        public void ExportToWord(string GridModel)

        {

            WordExport exp = new WordExport();

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            GridProperties obj = ConvertGridObject(GridModel);

            exp.Export(obj, DataSource, "Export.docx", false, false, ExportTheme.None);

        }

        public void ExportToPdf(string GridModel)

        {

            PdfExport exp = new PdfExport();

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            GridProperties obj = ConvertGridObject(GridModel);

            exp.Export(obj, DataSource, "Export.pdf", false, false, "none");

        }

        private GridProperties ConvertGridObject(string gridProperty)

        {

            GridProperties gridProp = Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties),gridProperty);

            AutoFormat auto = new AutoFormat();

            auto.FontFamily = "Arial";

            auto.ContentBorderColor = Color.Brown;

            auto.ContentFontSize = 10;

            auto.GCaptionBorderColor = Color.Cornsilk;

            auto.GContentFontColor = Color.DarkBlue;

            auto.HeaderFontSize = 12;

            auto.HeaderBorderColor = Color.Red;

            auto.ContentBgColor = Color.Wheat;

            auto.GHeaderBgColor = Color.Crimson;

            auto.AltRowBgColor = Color.LightCyan;

            gridProp.AutoFormat = auto;

            return gridProp;

        }
        
        public ActionResult ExportingGrid()

        {

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            ViewBag.datasource = DataSource;

            return View();

        }
        
      }

{% endhighlight %}

{% highlight razor %}

    @(Html.EJ().Grid<OrdersView>("FlatGrid")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

                .ToolbarSettings(toolBar => toolBar.ShowToolbar().ToolbarItems(items =>

                {

                    items.AddTool(ToolBarItems.ExcelExport);

                    items.AddTool(ToolBarItems.WordExport);

                    items.AddTool(ToolBarItems.PdfExport);

                }))

        .AllowPaging()

        .Columns(col =>

        {

            col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Add();

            col.Field("CustomerID").HeaderText("Customer ID").Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right). Add();          

            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Add();

            col.Field("OrderDate").HeaderText("Order Date").TextAlign(TextAlign.Right). Add();

            col.Field("ShipCity").HeaderText("Ship City").Add();

        })) 

{% endhighlight %}

![](Exporting_images/Customizing-Themes_img2.png)

Fig 4: Excel file – With customized themes
