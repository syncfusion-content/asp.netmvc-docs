---
layout: post
title: Exporting | Grid | ASP.NET MVC | Syncfusion
description: exporting
platform: ejmvc
control: Grid
documentation: ug
---

# Exporting

The `Exporting` feature provides support to export Grid data into excel, word and PDF files. To export the grid, `export` JavaScript method should be called with export action as parameter. To make it work from grid tool bar the `ExcelExport`, `WordExport`, `PdfExport` toolbar items needs to be added in grid tool bar using the `ToolbarItems` property of `ToolbarSettings` which are used to perform exporting. When you click the toolbar exporting icon, it internally invokes the `export` public method of Grid object to export.The code snippet for this is as follows.

{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<OrdersView>("FlatGrid")

    .DataSource((IEnumerable<object>)ViewBag.datasource)

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

		GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);

		exp.Export(obj, DataSource, "Export.xlsx", ExcelVersion.Excel2010, false, false, "flat-saffron");

	}

	public void ExportToWord(string GridModel)

	{

		WordExport exp = new WordExport();

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);

		exp.Export(obj, DataSource, "Export.docx", false, false, "flat-saffron");

	}

	public void ExportToPdf(string GridModel)

	{

		PdfExport exp = new PdfExport();

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);

		exp.Export(obj, DataSource, "Export.pdf", false, false, "flat-saffron");

	}

    }

{% endhighlight  %}
{% endtabs %}

# Hierarchy Grid Exporting

Grid will be exported with its child Grid. This can be achieved by enabling the `IncludeChildGrid` property of the respective Exporting classes like `GridExcelExport`, `GridWordExport` and `GridPdfExport` and include the dataSource needed for ChildGrid in the GridProperties object after deserializing them. Remaining procedures will be same as the normal Grid Exporting.

N> Excel File will be exported in the collapsed state with the expand/collapse icon whereas other file-formats like Pdf and Word will be exported in the expanded state.

{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<object>("HierarchyGrid")
        .Datasource((IEnumerable<object>)ViewBag.parentData)
        .ToolbarSettings(toolBar => toolBar.ShowToolbar().ToolbarItems(items =>
                {
                    items.AddTool(ToolBarItems.ExcelExport);
                    items.AddTool(ToolBarItems.WordExport);
                    items.AddTool(ToolBarItems.PdfExport);
                }))
        .Columns(col =>
        {
            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("FirstName").HeaderText("First Name").Width(100).Add();
            col.Field("Title").Width(120).Add();
            col.Field("City").Width(100).Add();
            col.Field("Country").Width(100).Add();
        })
        .ChildGrid(child =>
        {
            child.Datasource((IEnumerable<object>)ViewBag.childData)
            .QueryString("EmployeeID")
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("ShipCity").HeaderText("Ship City").Width(100).Add();
                col.Field("Freight").TextAlign(TextAlign.Right).Format("{0:C2}").Width(120).Add();
                col.Field("ShipName").HeaderText("Ship Name").Width(100).Add();
            });
        })
    )
 

{% endhighlight  %}
{% highlight c# %}

        public class HomeController : Controller
    {
        public ActionResult Index()
        {
            var order = new NorthWndDataContext().Orders.Take(100).ToList();
            var emp = new NorthWndDataContext().Employees.ToList();
            ViewBag.childData = order;
            ViewBag.parentData = emp;
            return View();
        }
        public void ExportToExcel(string GridModel)
        {
            ExcelExport exp = new ExcelExport();
            var DataSource = new NorthWndDataContext().Employees.ToList();
            GridProperties obj = ConvertGridObject(GridModel);
            obj.ChildGrid.DataSource = new NorthWndDataContext().Orders.Take(100).ToList();
            GridExcelExport expo = new GridExcelExport();
            expo.IncludeChildGrid = true;
            exp.Export(obj, DataSource, expo);
        }
        public void ExportToWord(string GridModel)
        {
            WordExport exp = new WordExport();
            var DataSource = new NorthWndDataContext().Employees.ToList();
            GridProperties obj = ConvertGridObject(GridModel);
            obj.ChildGrid.DataSource = new NorthWndDataContext().Orders.Take(100).ToList();
            GridWordExport expo = new GridWordExport();
            expo.IncludeChildGrid = true;
            exp.Export(obj, DataSource, expo);
        }
        public void ExportToPdf(string GridModel)
        {
            PdfExport exp = new PdfExport();
            var DataSource = new NorthWndDataContext().Employees.ToList();
            GridProperties obj = ConvertGridObject(GridModel);
            obj.ChildGrid.DataSource = new NorthWndDataContext().Orders.Take(100).ToList();
            GridPdfExport expo = new GridPdfExport();
            expo.IncludeChildGrid = true;
            expo.Unicode = true;
            exp.Export(obj, DataSource, expo);
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
                    object value = null;
                    string serialize = serializer.Serialize(ds.Value);
                    if (ds.Key == "childGrid")
                        value = ConvertGridObject(serialize);
                    else
                        value = serializer.Deserialize(serialize, type);
                    property.SetValue(gridProp, value, null);
                }
            }
            return gridProp;
        }
    }


{% endhighlight  %}
{% endtabs %}

## Server Dependencies

Export Helper functions are available in the Assembly `Syncfusion.EJ.Export`, which is available in the Essential Studio builds. Full list of assemblies needed for the Grid Export is as follows.

    1.  Syncfusion.EJ
    2.  Syncfusion.EJ.Export
    3.  Syncfusion.Linq.Base
    4.  Syncfusion.Compression.Base
    5.  Syncfusion.DocIO.Base
    6.  Syncfusion.XlsIO.Base
    7.  Syncfusion.PDF.Base


## Support Export Types

Currently server helper function allows following three types of exporting.

    1.  Word
    2.  Excel
    3.  PDF

##  Server side handlers

In MVC, exporting is achieved by using action controller method. In controller method, Grid property is passed as string parameter and you need to deserialize it into the Grid Property. By using the `Export` server method, you can export the Grid into excel, PDF and word documents.

{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<OrdersView>("FlatGrid")

    .DataSource((IEnumerable<object>)ViewBag.datasource)

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

		GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);

		exp.Export(obj, DataSource, "Export.xlsx", ExcelVersion.Excel2010, false, false, "flat-saffron");

	}

	public void ExportToWord(string GridModel)

	{

		WordExport exp = new WordExport();

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);

		exp.Export(obj, DataSource, "Export.docx", false, false, "flat-saffron");

	}

	public void ExportToPdf(string GridModel)

	{

		PdfExport exp = new PdfExport();

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);

		exp.Export(obj, DataSource, "Export.pdf", false, false, "flat-saffron");

	}

    }

{% endhighlight  %}

{% endtabs %} 

On Exporting, the default routing path to server-side that contains the action name as ExportToExcel for Excel Exporting, ExportToWord for Word Exporting and ExportToPdf for PDF Exporting. The default controller name in routing path is the Grid view page’s Controller name. For instance, when the Grid is rendered in GridFeatures View Page of the Home Controller, then on Excel exporting Grid Content the default routing path will be ~/Home/ExportToExcel.



## Export Mapper in MVC

The `Mappers` Grid property is used to modify the default routing path during exporting. By using Mappers, you can use any action name in Controller for exporting and the action can be in any controller (Need not to be in Grid View Page Controller).

{% tabs %}
 
{% highlight razor %}


    @(Html.EJ().Grid<OrdersView>("FlatGrid")

    .DataSource((IEnumerable<object>)ViewBag.datasource)

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

		GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);

		exp.Export(obj, DataSource, "Export.xlsx", ExcelVersion.Excel2010, false, false, "flat-saffron");

	}

	public void WordAction(string GridModel)

	{

		WordExport exp = new WordExport();

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
        
		exp.Export(obj, DataSource, "Export.docx", false, false, "flat-saffron");

	}

	public void PdfAction(string GridModel)

	{

		PdfExport exp = new PdfExport();

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);

		exp.Export(obj, DataSource, "Export.pdf", false, false, "flat-saffron");

	}

    }

{% endhighlight  %}

{% endtabs %}

## ColumnTemplate Exporting

To export the grid with columnTemplate we have to set the `IsTemplateColumnIncluded` as true in the parameter of the export method. You can handle the template elements in server-side event while exporting grid to various files such as Excel, PDF and Word.

The server-side events available in template column exporting and its argument types are listed in the following table.

<table>
<tr>
<th>
Event Name
</th>
<th>
Argument
</th>
<th>
Description
</th>
</tr>
<tr>
<td>
ExcelColumnTemplateInfo
</td>
<td>
currentCell, Row
</td>
<td>
It returns the current cell and row of excel sheet.
</td>
</tr>
<tr>
<td>
WordColumnTemplateInfo
</td>
<td>
currentCell, Row
</td>
<td>
It returns the current cell and row of word.
</td>
</tr>
<tr>
<td>
PdfColumnTemplateInfo
</td>
<td>
currentCell, Row
</td>
<td>
It returns the current cell and row of PDF.
</td>
</tr>
<tr>
<td>
ExcelChildGridInfo
</td>
<td>
current row, row data, GridProperties
</td>
<td>
Customize the cell and child Grid
</td>
</tr>
<tr>
<td>
PdfChildGridInfo
</td>
<td>
current row, row data, GridProperties
</td>
<td>
Customize the cell and child Grid
</td>
</tr>
<tr>
<td>
WordChildGridInfo
</td>
<td>
current row, row data, GridProperties
</td>
<td>
Customize the cell and child Grid
</td>
</tr>

</table>

You can modify the template column of exporting files using server events. The code snippet for this is as follows.

{% tabs %}
 
{% highlight razor %}

<script type="text/x-jsrender" id="columnTemplate">
        <a href="https://www.syncfusion.com">{{:FirstName}}</a>
</script>

@(Html.EJ().Grid<EmployeeView>("ColumnTemplate")
  .Datasource((IEnumerable<object>)ViewBag.datasource)
  .AllowPaging()
  .ToolbarSettings(toolBar => toolBar.ShowToolbar().ToolbarItems(items =>
   {
     items.AddTool(ToolBarItems.ExcelExport);
     items.AddTool(ToolBarItems.WordExport);
     items.AddTool(ToolBarItems.PdfExport);
   }))
  .Mappers(map => map.ExportToExcelAction("ColumnTemplateExportToExcel").ExportToPdfAction("ColumnTemplateExportToPdf").ExportToWordAction("ColumnTemplateToWord"))
  .Columns(col =>
   {
     col.HeaderText("First Name").Template("#columnTemplate").TextAlign(TextAlign.Center).Width(80).Add();
     col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(100).Add();
     col.Field("LastName").HeaderText("Last Name").Width(100).Add();
     col.Field("BirthDate").HeaderText("Birth Date").TextAlign(TextAlign.Right).Width(100).Format("{0:MM/dd/yyyy}").Add();
     col.Field("Country").Width(100).HeaderText("Country").Add();
   })
)

{% endhighlight %}

{% highlight c# %}

public partial class GridController : Controller

{
  public void ColumnTemplateExportToExcel(string GridModel)
  {
    ExcelExport exp = new ExcelExport();
    var DataSource =  new NorthwindDataContext().EmployeeViews.ToList();
    GridProperties obj = ConvertGridObject(GridModel);
    obj.ExcelColumnTemplateInfo = templateInfo;
    exp.Export(obj, DataSource, "Export.xlsx", ExcelVersion.Excel2010, false, true, "flat-saffron");
  }

  public void ColumnTemplateToWord(string GridModel)
  {
    WordExport exp = new WordExport();
    var DataSource =  new NorthwindDataContext().EmployeeViews.ToList();
    GridProperties obj = ConvertGridObject(GridModel);
    obj.WordColumnTemplateInfo = WordTemplateInfo;
    exp.Export(obj, DataSource, "Export.docx", false, true, "flat-saffron");
  }
  public void ColumnTemplateExportToPdf(string GridModel)
  {
    PdfExport exp = new PdfExport();
    var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
    GridProperties obj = ConvertGridObject(GridModel);
    obj.PdfColumnTemplateInfo = PdfTemplateInfo;
    exp.Export(obj, DataSource, "Export.pdf", false, true, "flat-saffron");
  }
  public void templateInfo(object currentCell, object row)
  {
    IRange range = (IRange)currentCell;
    object templates;
    foreach (var data in row.GetType().GetProperties())
    {
      if (range.Value.Contains(data.Name))
      {
        templates = row.GetType().GetProperty(data.Name).GetValue(row, null);
        range.Value = range.Value.Replace(data.Name, templates.ToString());
        var regex = new Regex("<a [^>]*href=(?:'(?<href>.*?)')|(?:\"(?<href>.*?)\")", RegexOptions.IgnoreCase);
        var urls = regex.Matches(range.Value.ToString()).OfType<match>().Select(m => m.Groups["href"].Value).SingleOrDefault();
        IHyperLink hyperlink = (range.Parent as Syncfusion.XlsIO.Implementation.WorksheetImpl).HyperLinks.Add(range);
        hyperlink.Type = ExcelHyperLinkType.Url;
        hyperlink.TextToDisplay = templates.ToString();
        hyperlink.Address = urls;
      }
    }
  }
  public void WordTemplateInfo(object currentCell, object row)
  {
    WTableCell wCell = (WTableCell)currentCell;
    object templates;
    foreach (var data in row.GetType().GetProperties())
    {
      if (wCell.LastParagraph.Text.ToString().Contains(data.Name))
      {
        templates = row.GetType().GetProperty(data.Name).GetValue(row, null);
        var regex = new Regex("<a [^>]*href=(?:'(?<href>.*?)')|(?:\"(?<href>.*?)\")", RegexOptions.IgnoreCase);
        var urls = regex.Matches(wCell.LastParagraph.Text).OfType<Match>().Select(m => m.Groups["href"].Value).SingleOrDefault();
        wCell.LastParagraph.Text = "";
        IWField field = wCell.LastParagraph.AppendHyperlink(urls, templates.ToString(), HyperlinkType.WebLink);
      }
    }
  }

  public void PdfTemplateInfo(object currentCell, object row)
  {
    Syncfusion.Pdf.Grid.PdfGridCell range = (Syncfusion.Pdf.Grid.PdfGridCell)currentCell;
    object templates;
    range.Value = Uri.UnescapeDataString(range.Value.ToString());
    foreach (var data in row.GetType().GetProperties())
    {
      if (range.Value.ToString().Contains(data.Name))
      {
        templates = row.GetType().GetProperty(data.Name).GetValue(row, null);
        var regex = new Regex("<a [^>]*href=(?:'(?<href>.*?)')|(?:\"(?<href>.*?)\")", RegexOptions.IgnoreCase);
        var urls = regex.Matches(range.Value.ToString()).OfType<Match>().Select(m => m.Groups["href"].Value).SingleOrDefault();
        RectangleF rectangle = new RectangleF(10, 40, 30, 30);
        PdfUriAnnotation uriAnnotation = new PdfUriAnnotation(rectangle, urls);
        uriAnnotation.Text = templates.ToString();
        range.Value = uriAnnotation;
      }
     }
   }
}
{% endhighlight %}

{% endtabs %}

## DetailTemplate Exporting

To export the grid with detail template we have to set the `IncludeDetailRow` as true in the parameter of the export method. You can handle template elements using server-side event while exporting grid to various files such as Excel, PDF and Word.

The server-side events available in detail template exporting and its argument types are listed in the following table.

<table>
<tr>
<th>
Event Name
</th>
<th>
Argument
</th>
<th>
Description
</th>
</tr>
<tr>
<td>
ExcelDetailTemplateInfo
</td>
<td>
currentCell, Row
</td>
<td>
It returns the current cell and row of excel sheet.
</td>
</tr>
<tr>
<td>
WordDetailTemplateInfo
</td>
<td>
currentCell, Row
</td>
<td>
It returns the current cell and row of word.
</td>
</tr>
<tr>
<td>
PdfDetailTemplateInfo
</td>
<td>
currentCell, Row
</td>
<td>
It returns the current cell and row of PDF.
</td>
</tr>
</table>

You can modify the detailTemplate of exporting files using server events. The code snippet for this is as follows:

{% tabs %}
 
{% highlight razor %}

<script id="tabGridContents" type="text/x-jsrender">
    <b> More Details: </b> <br /><br /> <b class='detail'>Last Name</b> - {{:LastName}} <br /> <br /> <b class='detail'>Home Phone</b> - {{:HomePhone}} <br /> <br /> <b class='detail'>Exten No</b> - {{:Extension}}
  
</script>

@(Html.EJ().Grid<EmployeeView>("DetailTemplate")
   .Datasource((IEnumerable<object>)ViewBag.datasource)
   .ToolbarSettings(toolBar => toolBar.ShowToolbar().ToolbarItems(items =>
   {
     items.AddTool(ToolBarItems.ExcelExport);
     items.AddTool(ToolBarItems.WordExport);
     items.AddTool(ToolBarItems.PdfExport);
   }))
  .Columns(col =>
   {
     col.Field("EmployeeID").HeaderText("Employee ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
     col.Field("FirstName").HeaderText("First Name").Width(100).Add();
     col.Field("Title").Width(120).Add();
     col.Field("City").Width(100).Add();
     col.Field("Country").Width(100).Add();
   })
  .DetailsTemplate("#tabGridContents")
)

{% endhighlight %}

{% highlight c# %}

public class GridController : Controller
{
    public ActionResult GridFeatures()
    {
       var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
       ViewBag.dataSource = DataSource;
       return View();
    }
    public void ExportToExcel(string GridModel)
    {
      ExcelExport exp = new ExcelExport();
      var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
      GridProperties obj = ConvertGridObject(GridModel);
      GridExcelExport exp2 = new GridExcelExport() { IncludeDetailRow = true, Theme = "flat-saffron", FileName = "Export.xlsx" };
      obj.ExcelDetailTemplateInfo = templateInfo;
      exp.Export(obj, DataSource, exp2);
   }
   public void ExportToWord(string GridModel)
   {
     WordExport exp = new WordExport();
     var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
     GridProperties obj = ConvertGridObject(GridModel);
     obj.WordDetailTemplateInfo = WordDetailTemplateInfo;
     GridWordExport exp1 = new GridWordExport() { IncludeDetailRow = true, Theme = "flat-saffron", FileName = "Export.docx" };
     exp.Export(obj, DataSource, exp1);
   }
   public void ExportToPDF(string GridModel)
   {
     PdfExport exp = new PdfExport();
     var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
     GridProperties obj = ConvertGridObject(GridModel);     
     obj.PdfDetailTemplateInfo = PdfDetailTemplateInfo;
     GridPdfExport exp3 = new GridPdfExport() { IncludeDetailRow = true, Theme = "flat-saffron", FileName = "Export.pdf" };
     exp.Export(obj, DataSource, exp3);
   }
   public void templateInfo(object currentCell, object row)
   {
     IRange range = (IRange)currentCell;
     object templates;
     foreach (var data in row.GetType().GetProperties())
     {
       if (range.Value.Contains(data.Name))
       {
         templates = row.GetType().GetProperty(data.Name).GetValue(row, null);
         range.Value = range.Value.Replace(data.Name, templates.ToString());
         var charsToRemove = new string[] { '{', '}', '<b>', ':', '</b>', '<br />', 'style', '=', 'class', '</div>', '<p>', '</p>', 'detail', '<b', '>', };
         foreach (var c in charsToRemove)
         {
            range.Value = range.Value.ToString().Replace(c, string.Empty);
         }
         range.HorizontalAlignment = ExcelHAlign.HAlignCenter;
       }
     }
   }
   public void WordDetailTemplateInfo(object currentCell, object row)
   {
      WTableCell wCell = (WTableCell)currentCell;
      object templates;
      foreach (var data in row.GetType().GetProperties())
      {
        if (wCell.LastParagraph.Text.ToString().Contains(data.Name))
        {
          templates = row.GetType().GetProperty(data.Name).GetValue(row, null);
          wCell.LastParagraph.Text = wCell.LastParagraph.Text.ToString().Replace(data.Name, templates.ToString());
          var charsToRemove = new string[] { '{', '}', '<b>', ':', '</b>', '<br />', 'style', '=', 'class', '</div>', '<p>', '</p>', 'detail', '<b', '>', };
          foreach (var c in charsToRemove)
          {
             wCell.LastParagraph.Text  = wCell.LastParagraph.Text.ToString().Replace(c, string.Empty); //
          }
        }
      }
   }
   public void PdfDetailTemplateInfo(object currentCell, object row)
   {
     Syncfusion.Pdf.Grid.PdfGridCell range = (Syncfusion.Pdf.Grid.PdfGridCell)currentCell;
     object templates;
     foreach (var data in row.GetType().GetProperties())
     {
       if (range.Value.ToString().Contains(data.Name))
       {
         templates = row.GetType().GetProperty(data.Name).GetValue(row, null);
         range.Value = range.Value.ToString().Replace(data.Name, templates.ToString());
         var charsToRemove = new string[] { '{', '}', '<b>', ':', '</b>', '<br />', 'style', '=', 'class', '</div>', '<p>', '</p>', 'detail', '<b', '>', };
         foreach (var c in charsToRemove)
         {
            range.Value = range.Value.ToString().Replace(c, string.Empty);
         }
       }
     }
   }
  private GridProperties ConvertGridObject(string gridProperty)
  {
    JavaScriptSerializer serializer = new JavaScriptSerializer();
    IEnumerable div = (IEnumerable)serializer.Deserialize(gridProperty, typeof(IEnumerable));
    GridProperties gridProp = new GridProperties();
    foreach (KeyValuePair<string, object> data in div)
    {
      var property = gridProp.GetType().GetProperty(data.Key, BindingFlags.Instance | BindingFlags.Public | BindingFlags.IgnoreCase);
      if (property != null)
      {
        Type type = property.PropertyType;
        string serialize = serializer.Serialize(data.Value);
        object value = serializer.Deserialize(serialize, type);
        property.SetValue(gridProp, value, null);
      }
    }
    return gridProp;
  }
}

{% endhighlight %}

{% endtabs %}

##  Multiple Exporting

The `AllowMultipleExporting` property allows you to export multiple grids into same file. Once you enable the `AllowMultipleExporting`, grid properties of all the grid which are available in current page are passed as string array parameter to controller action method.
In controller action method you are able to export all the grids available in the current page. The code snippet for this is as follows.

{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<EmployeeView>("Grid")
    .DataSource((System.Data.DataTable)ViewBag.datasource1)
    .AllowMultipleExporting()
    .AllowPaging()
    .ToolbarSettings(toolBar => toolBar.ShowToolbar().ToolbarItems(items =>
    {
        items.AddTool(ToolBarItems.ExcelExport);
        items.AddTool(ToolBarItems.WordExport);
        items.AddTool(ToolBarItems.PdfExport);
    }))
    .Mappers(map => map.ExportToExcelAction("ExportToExcel").ExportToPdfAction("/Home/ExportToExcel").ExportToWordAction("MultipleExportToWord"))
    .Columns(col =>
    {
        col.Field("EmployeeID").HeaderText("Employee ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(125).Add();
        col.Field("FirstName").HeaderText("First Name").Width(100).Add();
        col.Field("LastName").HeaderText("Last Name").Width(100).Add();
        col.Field("Title").HeaderText("Title").Width(150).Add();

    })
    )

{% endhighlight  %}

 {% highlight c# %}

// Excel export

    public void MultipleExportToExcel(string[] GridModel)

    {
        ExcelExport exp = new ExcelExport();
        var EmployeeData = new NorthwindDataContext().EmployeeViews.Take(5).ToList();
        var OrderData = new NorthwindDataContext().OrdersViews.Take(5).ToList();
        bool initial = true;
        IWorkbook book = null;
        foreach(string gridProperty in GridModel)
        {
            GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), gridProperty);
            if (initial)
            {
                book = exp.Export(gridProp, EmployeeData, "Export.xlsx", ExcelVersion.Excel2010, true, true, "flat-saffron", true);
                initial = false;
            } 
            else
            {
                exp.Export(gridProp, OrderData, "Export.xlsx", ExcelVersion.Excel2010, true, true, "flat-saffron", false, book, MultipleExportType.AppendToSheet, "Second Grid");
            }
        }

    }

// Word export

    public void MultipleExportToWord(string[] GridModel)

    {
        WordExport exp = new WordExport();
        var EmployeeData = new NorthwindDataContext().EmployeeViews.Take(5).ToList();
        var OrderData = new NorthwindDataContext().OrdersViews.Take(5).ToList();
        IWordDocument document = null;
        bool initial = true;;
        foreach(string gridProperty in GridModel)
        {
            GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), gridProperty);
            if (initial)
            {
                document = exp.Export(gridProp, EmployeeData, "Export.docx", true, true, "flat-saffron", true);
                initial = false;
            } else
            {
                exp.Export(gridProp, OrderData, "Export.docx", true, true, "flat-saffron", false, document, "Second Grid");
            }
        }

    }

// PDF export

    public void MultipleExportToPdf(string[] GridModel)
    {
        PdfExport exp = new PdfExport();
        var EmployeeData = new NorthwindDataContext().EmployeeViews.Take(5).ToList();
        var OrderData = new NorthwindDataContext().OrdersViews.Take(5).ToList();
        PdfDocument document = null;
        bool initial = true;
        foreach(string gridProperty in GridModel)
        {
            GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), gridProperty);
            if (initial)
            {
                document = exp.Export(gridProp, EmployeeData, "Export.pdf", true, true, "flat-saffron", true);
                initial = false;
            } else

            {
                exp.Export(gridProp, OrderData, "Export.pdf", true, true, "flat-saffron", false, document, "Second Grid");
            }
        }
    }


{% endhighlight %}

{% endtabs %} 

## DataTable Exporting

Grid has support to export DataTable type datasource. This support helps when a Grid has no view model, and a DataTable is bound to a Grid.

{% tabs %}
 
{% highlight razor %}

   @(Html.EJ().Grid<object>("DataTableGrid")
      .Datasource((DataTable)ViewBag.dataTable)
      .AllowPaging()
      .ToolbarSettings(toolBar => toolBar.ShowToolbar().ToolbarItems(items =>
       {
          items.AddTool(ToolBarItems.ExcelExport);
          items.AddTool(ToolBarItems.WordExport);
          items.AddTool(ToolBarItems.PdfExport);
       }))
       .Columns(col =>
        {
          col.Field("ProductID").HeaderText("Product ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
          col.Field("ProductName").HeaderText("Product Name").Width(80).Add();
          col.Field("SupplierID").HeaderText("Supplier ID").TextAlign(TextAlign.Right).Width(75).Add();
          col.Field("CategoryID").HeaderText("Category ID").Width(80).Add();
        })
    )

{% endhighlight %}

{% highlight c# %}

  public class GridController : Controller
  {
    DataTable _dTable = new DataTable();
    List<Product> data = new List<Product>();
    
    public void GetGridDT()
    {
      var connection = ConfigurationManager.ConnectionStrings["NORTHWNDConnectionString"].ConnectionString;
      using (var dataAdapter = new SqlDataAdapter("SELECT * from Products", connection))
      {
         dataAdapter.Fill(_dTable);
      }
    }
    
    public ActionResult GridFeatures()
    {
        GetGridDT();
        ViewBag.dataTable = _dTable;
        return View();
    }
    public void ExportToExcel(string GridModel)
    {
        ExcelExport exp = new ExcelExport();
        GetGridDT();
        DataTable DataSource = _dTable;
        GridProperties properties = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
        exp.Export(properties, DataSource, "Export.xlsx", ExcelVersion.Excel2010, false, false, "flat-saffron");
    }
    public void ExportToWord(string GridModel)
    {
        WordExport exp = new WordExport();
        GetGridDT();
        DataTable DataSource = _dTable;
        GridProperties properties = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
        exp.Export(properties, DataSource, "Export.docx", false, false, "flat-saffron");
    }
    public void ExportToPdf(string GridModel)
    {
        PdfExport exp = new PdfExport();
        GetGridDT();
        DataTable DataSource = _dTable;
        GridProperties properties = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
        exp.Export(properties, DataSource, "Export.pdf", false, false, "flat-saffron");
    }
}

{% endhighlight %}

{% endtabs %}

  
## Export required grid in single file

You can export required grids in single file using the `ej.Grid.exportAll` method. This method can be used with export action and array of jQuery selector of grid which need to be export. The code snippet for it is as follows:

{% highlight js %}

    $('#exportAll').click(function(){
			ej.Grid.exportAll('MultipleExportToExcel',['Grid1', 'Grid2']);
		});

{% endhighlight %}

## List of properties ignored on export

Following are the list of properties that are excluded during grid export, to reduce the unwanted data transfer to server.  

* dataSource
* query
* rowTemplate
* detailsTemplate
* pageSettings
* enableRTL
* cssClass

##Export only visible records


By default the `pageSettings` is ignored in export to facilitate all pages export. To achieve current visible page record export, the `pageSettings` should be removed from ignore list using the following code.

The snippet for this is as follows:

{% highlight js %}

	var grid = $('#Grid').ejGrid('instance');
	grid.ignoreOnExport.splice(grid.ignoreOnExport.indexOf('pageSettings'), 1);

{% endhighlight %}

On server before calling the `Export` function, the data source should be processed using DataOperations's Execute function. 

{% highlight c# %}

    public void ExportToExcel(string GridModel)
    {
        ExcelExport exp = new ExcelExport();
        var DataSource = new NorthwindDataContext().OrdersViews.ToList();
        GridProperties properties =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
        var dataSource = new DataOperations().Execute(GridModel, DataSource);
        exp.Export(properties, dataSource, "Export.xlsx", ExcelVersion.Excel2010, false, false, "flat-saffron");
    }

    public void ExportToWord(string GridModel)
    {
        WordExport exp = new WordExport();
        var DataSource = new NorthwindDataContext().OrdersViews.ToList();
        GridProperties properties =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
        var dataSource = new DataOperations().Execute(GridModel, DataSource);
        exp.Export(properties, dataSource, "Export.docx", false, false, "flat-saffron");
    }
    public void ExportToPdf(string GridModel)
    {
        PdfExport exp = new PdfExport();
        var DataSource = new NorthwindDataContext().OrdersViews.ToList();
        GridProperties properties = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
        var dataSource = new DataOperations().Execute(GridModel, DataSource);
        exp.Export(properties, dataSource, "Export.pdf", false, false, "flat-saffron");
    }

{% endhighlight %}

## Local data 

By default, client data source is not sent to server to prevent the unwanted data transfer since all data origin is in server. In case, if you don't want to query the data source again for exporting in server, the grid's client [`dataSource`](http://help.syncfusion.com/js/api/ejgrid#members:datasource) can be sent to server on export PostBack by removing the [`dataSource`](http://help.syncfusion.com/js/api/ejgrid#members:datasource) property in grid's ignore list. The code snippet for this is as follows.

{% highlight js %}

var grid = $('#GridId').ejGrid('instance');
grid.ignoreOnExport.splice(grid.ignoreOnExport.indexOf('dataSource'), 1);

{% endhighlight %}



## Themes

The grid export have 13 theme option to match with our [built-in control themes](http://helpjs.syncfusion.com/js/theming-in-essential-javascript-components#). They are as follows.

<table>
<tr><th>Enum</th><th>Equivalent string input</th></tr>

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

Also, it has `none` option which will export the grid without any theme.  The desired theme name can be passed as a parameter to `Export` method and the code snippet for this is as follows.

{% tabs %}

{% highlight c# %}

    public partial class GridController : Controller

    {
	public void ExportToExcel(string GridModel)

	{

		ExcelExport exp = new ExcelExport();

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties),GridModel);

		exp.Export(obj, DataSource, "Export.xlsx", ExcelVersion.Excel2010, false, false, "none");

	}

	public void ExportToWord(string GridModel)

	{

		WordExport exp = new WordExport();

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties),GridModel);

		exp.Export(obj, DataSource, "Export.docx", false, false, ExportTheme.FlatSaffron);

	}

	public void ExportToPdf(string GridModel)

	{

		PdfExport exp = new PdfExport();

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties),GridModel);

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

	.DataSource((IEnumerable<object>)ViewBag.datasource)

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
{% endtabs %}  
When the theme is set as none and the autoFormat is not set to the grid, then no theme is applied to the exported grid. The grid is exported without any theme as in the following screenshots:

![](Exporting_images/Customizing-Themes_img1.png)


## AutoFormat Class



The **AutoFormat** Class can be used to customize the styles or themes applied to the exported grid. With the autoFormat class, you can provide required color to the grid content, alt row background or border color.

The various properties available under the autoFormat class are listed in the following table.

<table>
<tr>
<th>
Properties</th><th>
Type</th><th>
Description</th></tr>
<tr>
<td>
FontFamily</td><td>
String</td><td>
The font name</td></tr>
<tr>
<td>
HeaderBorderColor</td><td>
System.Drawing.Color</td><td>
The border color of the grid header.</td></tr>
<tr>
<td>
HeaderFontSize</td><td>
int</td><td>
The size of the grid header font.</td></tr>
<tr>
<td>
GHeaderBgColor</td><td>
System.Drawing.Color</td><td>
The Column Header cell color and the Group Header Indent cell color.</td></tr>
<tr>
<td>
ContentBgColor</td><td>
System.Drawing.Color</td><td>
The background color of the content.</td></tr>
<tr>
<td>
ContentBorderColor</td><td>
System.Drawing.Color</td><td>
The border color of the grid content.</td></tr>
<tr>
<td>
ContentFontSize</td><td>
int</td><td>
The font size of the grid content.</td></tr>
<tr>
<td>
GContentFontColor</td><td>
System.Drawing.Color</td><td>
The font color of the record field cell.</td></tr>
<tr>
<td>
GCaptionBorderColor</td><td>
System.Drawing.Color</td><td>
The border color of the group caption cell.</td></tr>
<tr>
<td>
AltRowBgColor</td><td>
System.Drawing.Color</td><td>
The background color of the alternative row of the grid content.</td></tr>
</table>


{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<OrdersView>("FlatGrid")

    .DataSource((IEnumerable<object>)ViewBag.datasource)

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
{% highlight c# %}

    public partial class GridController : Controller

    {

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

		exp.Export(obj, DataSource, "Export.docx", false, false, ExportTheme.FlatSaffron);

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

		GridProperties gridProp = Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties),gridProperty);
		
		GridExtensions ext = new GridExtensions();

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
		
		ext.SetTheme(auto, "flat-saffron");

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


{% endtabs %} 
![](Exporting_images/Customizing-Themes_img2.png)

## Exporting server events

`Exporting` feature supports server-side event handler. You can handle server-side event while exporting grid to various files such as Excel, PDF and Word. The various server-side events available in Exporting and its argument types are listed in the following table.

<table>
<tr>
<th>
Event Name
</th>
<th>
Argument 
</th>
<th>
Description
</th>
</tr>
<tr>
<td>
ServerExcelQueryCellInfo
</td>
<td>
currentCell
</td>
<td>
It returns the current cell of excel sheet.
</td>
</tr>
<tr>
<td>
ServerExcelRowInfo
</td>
<td>
range
</td>
<td>
It returns the current row of excel sheet.
</td>
</tr>
<tr>
<td>
ServerWordQueryCellInfo
</td>
<td>
currentCell
</td>
<td>
It returns the current cell of word.
</td>
</tr>
<tr>
<td>
ServerWordRowInfo
</td>
<td>
range
</td>
<td>
It returns the current row of word.
</td>
</tr>
<tr>
<td>
ServerPdfQueryCellInfo
</td>
<td>
currentCell
</td>
<td>
It returns the current cell of PDF.
</td>
</tr>
<tr>
<td>
ServerPdfRowInfo
</td>
<td>
range
</td>
<td>
It returns the current row of PDF.
</td>
</tr>
</table>


You can customize the particular cell or particular  row of exporting files using server events. The code snippet for this is as follows.

{% tabs %}
 
{% highlight razor %}

    @(Html.EJ().Grid<OrdersView>("FlatGrid")

    .DataSource((IEnumerable<object>)ViewBag.datasource)

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
{% highlight c# %}

    public partial class GridController : Controller

    {

	public void ExportToExcel(string GridModel)
    {
            ExcelExport exp = new ExcelExport();
            var DataSource = new NorthwindDataContext().EmployeeViews.Take(100).ToList(); 
            GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
            obj.ServerExcelQueryCellInfo = QueryCellInfo;
            exp.Export(obj, DataSource, "Export.xlsx", ExcelVersion.Excel2010, false, false, "flat-saffron");
    }
    public void QueryCellInfo(object currentCell)
    {
            IRange range = (IRange)currentCell;
            if (range.Column==1 && int.Parse(range.Value) == 5)
                range.CellStyle.Color = Color.Red;
    } 
	public ActionResult ExportingGrid()
	{

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		ViewBag.datasource = DataSource;

		return View();

	}

    }

{% endhighlight %}


{% endtabs %}

![](Exporting_images/Exporting_Serverside_Event.png)















