---
layout: post
title: Exporting
description: exporting
platform: ejmvc
control: Grid
documentation: ug
---

## Exporting

Exporting feature provides support to export Grid data into excel, word and pdf files. The tool bar has ExcelExport, WordExport, PdfExport icons that are used to perform exporting. When you click the toolbar exporting icon, it internally invokes the export() public method of Grid object to make export. You can also invoke export() method manually to make export.

### MVC

In MVC, exporting is achieved by using action controller method. In controller method, Grid property is passed as string parameter. You need to serialize it into Grid Property. Using Export() server method you can export the Grid into excel, pdf and word documents.

[MVC]

[razor]



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



[Controller]



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

        }    }



On Exporting the default routing path to server-side that contains the action name as ExportToExcel for Excel Exporting, ExportToWord for Word Exporting and ExportToPdf for Pdf Exporting. The default controller name in routing path is the Grid view page’s Controller name. For instance, when Grid is rendered in GridFeatures View Page of Home Controller, then on Excel exporting Grid Content, the routing path is ~/Home/ExportToExcel.



#### Export Mapper in MVC

Mappers Grid property is used to modify the default routing path during exporting. By using Mappers, you can use any action name in Controller for exporting and the action can be in any controller (Need not to be in Grid View Page Controller).



[MVC]

[razor]



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



[Controller]



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

        }    }







