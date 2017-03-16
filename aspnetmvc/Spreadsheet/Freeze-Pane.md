---
layout: post
title: Freeze Pane with Spreadsheet widget for Syncfusion Essential ASP .Net MVC
description: How to use the Spreadsheet Freeze Pane
platform: ejmvc
control: Spreadsheet
documentation: ug
keywords: Freeze, unfreeze, freezePanes, freezeleftcolumn, freezetoprow
--- 

# Freeze Pane 
Freeze pane allows you to keep a portion of the sheet visible, while scrolling through the rest of the worksheet. 

The freeze pane can be applied in a following ways,

1. User Interface
2. Initial Load
3. Method

### User Interface
Select any cell and on OTHERS tab click Freeze Panes in Freeze Panes dropdown list.

![](Freeze-Pane_images/Freeze-Pane_img1.png)

### Initial Load
You can use `AllowFreezing ` property to enable or disable freeze pane in Spreadsheet.
To specify number of rows and columns to be frozen, use `FrozenRows` and `FrozenColumns` property in sheets.

The following code example describes the above behavior,

{% tabs %}
{% highlight cshtml %}
@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        .AllowFreezing(true)
        .Sheets(sheet =>
        {
            sheet.Datasource((IEnumerable<object>)ViewBag.Datasource).FrozenRows(5).FrozenColumns(2).Add();
        })
    })
)
{% endhighlight %}
{% highlight c# %}
namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            List<PersonDetail> lItems = new List<PersonDetail>();
            lItems.Add(new PersonDetail() { SupplierID = 1, CompanyName = "Exotic Liquids", ContactName = "Charlotte Cooper", ContactTitle = "Purchasing Manager", City = "London", PostalCode = "EC1 4SD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 2, CompanyName = "New Orleans Cajun Delights", ContactName = "Shelley Burke", ContactTitle = "Order Administrator", City = "New Orleans", PostalCode = "70117", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 3, CompanyName = "Grandma Kelly's Homestead", ContactName = "Regina Murphy", ContactTitle = "Sales Representative", City = "Ann Arbor", PostalCode = "48104", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 4, CompanyName = "Tokyo Traders", ContactName = "Yoshi Nagase", ContactTitle = "Marketing Manager", City = "Tokyo", PostalCode = "100", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 5, CompanyName = "Cooperativa de Quesos 'Las Cabras'", ContactName = "Antonio del Valle Saavedra", ContactTitle = "Export Administrator", City = "Oviedo", PostalCode = "33007", Country = "Spain" });
            lItems.Add(new PersonDetail() { SupplierID = 6, CompanyName = "Mayumi's", ContactName = "Mayumi Ohno", ContactTitle = "Marketing Representative", City = "Osaka", PostalCode = "545", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 7, CompanyName = "Pavlova, Ltd.", ContactName = "Ian Devling", ContactTitle = "Marketing Manager", City = "Melbourne", PostalCode = "3058", Country = "Australia" });
            lItems.Add(new PersonDetail() { SupplierID = 8, CompanyName = "Specialty Biscuits, Ltd.", ContactName = "Peter Wilson", ContactTitle = "Sales Representative", City = "Manchester", PostalCode = "M14 GSD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 9, CompanyName = "PB Knäckebröd AB", ContactName = "Lars Peterson", ContactTitle = "Sales Agent", City = "Göteborg", PostalCode = "S-345 67", Country = "Sweden" });
            ViewBag.Datasource = lItems;
            return View();
        }
    }
}
{% endhighlight %}
{% endtabs %}

N> The default value of `AllowFreezing ` property is true.

### Method
You can freeze rows or columns using [`freezePanes`](https://help.syncfusion.com/api/js/ejspreadsheet#methods:xlfreeze-freezepanes "freezePanes") method. 

The following code example describes the above behavior,

{% tabs %}
{% highlight cshtml %}
@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Datasource((IEnumerable<object>)ViewBag.Datasource).Add();
    })
    .ClientSideEvents(events => events.LoadComplete("loadComplete"))
)
<script type="text/javascript">
    function loadComplete(args) {
        if (!this.isImport)
            this.XLFreeze.freezePanes(5,2);
    }
</script>
{% endhighlight %}
{% highlight c# %}
namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            List<PersonDetail> lItems = new List<PersonDetail>();
            lItems.Add(new PersonDetail() { SupplierID = 1, CompanyName = "Exotic Liquids", ContactName = "Charlotte Cooper", ContactTitle = "Purchasing Manager", City = "London", PostalCode = "EC1 4SD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 2, CompanyName = "New Orleans Cajun Delights", ContactName = "Shelley Burke", ContactTitle = "Order Administrator", City = "New Orleans", PostalCode = "70117", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 3, CompanyName = "Grandma Kelly's Homestead", ContactName = "Regina Murphy", ContactTitle = "Sales Representative", City = "Ann Arbor", PostalCode = "48104", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 4, CompanyName = "Tokyo Traders", ContactName = "Yoshi Nagase", ContactTitle = "Marketing Manager", City = "Tokyo", PostalCode = "100", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 5, CompanyName = "Cooperativa de Quesos 'Las Cabras'", ContactName = "Antonio del Valle Saavedra", ContactTitle = "Export Administrator", City = "Oviedo", PostalCode = "33007", Country = "Spain" });
            lItems.Add(new PersonDetail() { SupplierID = 6, CompanyName = "Mayumi's", ContactName = "Mayumi Ohno", ContactTitle = "Marketing Representative", City = "Osaka", PostalCode = "545", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 7, CompanyName = "Pavlova, Ltd.", ContactName = "Ian Devling", ContactTitle = "Marketing Manager", City = "Melbourne", PostalCode = "3058", Country = "Australia" });
            lItems.Add(new PersonDetail() { SupplierID = 8, CompanyName = "Specialty Biscuits, Ltd.", ContactName = "Peter Wilson", ContactTitle = "Sales Representative", City = "Manchester", PostalCode = "M14 GSD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 9, CompanyName = "PB Knäckebröd AB", ContactName = "Lars Peterson", ContactTitle = "Sales Agent", City = "Göteborg", PostalCode = "S-345 67", Country = "Sweden" });
            ViewBag.Datasource = lItems;
            return View();
        }
    }
}
{% endhighlight %}
{% endtabs %}

The following output is displayed as a result of the above behavior.
![](Freeze-Pane_images/Freeze-Pane_img2.png)

N> When we apply freeze pane by selecting cell “A1”, rows and columns are frozen based on the middle cell in the worksheet.

## Freeze Rows
It allows you to keep the certain number of rows visible while scrolling through the rest of the worksheet.

The freeze rows can be applied in a following ways,

1. Initial Load
2. Method

### Initial Load
You can freeze rows using `FrozenRows` property in sheets. 

The following code example describes the above behavior,

{% tabs %}
{% highlight cshtml %}
@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Datasource((IEnumerable<object>)ViewBag.Datasource).FrozenRows(3).Add();
    })
)
{% endhighlight %}
{% highlight c# %}
namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            List<PersonDetail> lItems = new List<PersonDetail>();
            lItems.Add(new PersonDetail() { SupplierID = 1, CompanyName = "Exotic Liquids", ContactName = "Charlotte Cooper", ContactTitle = "Purchasing Manager", City = "London", PostalCode = "EC1 4SD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 2, CompanyName = "New Orleans Cajun Delights", ContactName = "Shelley Burke", ContactTitle = "Order Administrator", City = "New Orleans", PostalCode = "70117", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 3, CompanyName = "Grandma Kelly's Homestead", ContactName = "Regina Murphy", ContactTitle = "Sales Representative", City = "Ann Arbor", PostalCode = "48104", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 4, CompanyName = "Tokyo Traders", ContactName = "Yoshi Nagase", ContactTitle = "Marketing Manager", City = "Tokyo", PostalCode = "100", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 5, CompanyName = "Cooperativa de Quesos 'Las Cabras'", ContactName = "Antonio del Valle Saavedra", ContactTitle = "Export Administrator", City = "Oviedo", PostalCode = "33007", Country = "Spain" });
            lItems.Add(new PersonDetail() { SupplierID = 6, CompanyName = "Mayumi's", ContactName = "Mayumi Ohno", ContactTitle = "Marketing Representative", City = "Osaka", PostalCode = "545", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 7, CompanyName = "Pavlova, Ltd.", ContactName = "Ian Devling", ContactTitle = "Marketing Manager", City = "Melbourne", PostalCode = "3058", Country = "Australia" });
            lItems.Add(new PersonDetail() { SupplierID = 8, CompanyName = "Specialty Biscuits, Ltd.", ContactName = "Peter Wilson", ContactTitle = "Sales Representative", City = "Manchester", PostalCode = "M14 GSD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 9, CompanyName = "PB Knäckebröd AB", ContactName = "Lars Peterson", ContactTitle = "Sales Agent", City = "Göteborg", PostalCode = "S-345 67", Country = "Sweden" });
            ViewBag.Datasource = lItems;
            return View();
        }
    }
}
{% endhighlight %}
{% endtabs %}

### Method
You can freeze rows using [`freezeRows`](https://help.syncfusion.com/api/js/ejspreadsheet#methods:xlfreeze-freezeRows "freezeRows") method. 

The following code example describes the above behavior,

{% tabs %}
{% highlight cshtml %}
@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Datasource((IEnumerable<object>)ViewBag.Datasource).Add();
    })
    .ClientSideEvents(events => events.LoadComplete("loadComplete"))
)
<script type="text/javascript">
    function loadComplete(args) {
        if (!this.isImport)
            this.XLFreeze.freezeRows(3);
    }
</script>
{% endhighlight %}
{% highlight c# %}
namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            List<PersonDetail> lItems = new List<PersonDetail>();
            lItems.Add(new PersonDetail() { SupplierID = 1, CompanyName = "Exotic Liquids", ContactName = "Charlotte Cooper", ContactTitle = "Purchasing Manager", City = "London", PostalCode = "EC1 4SD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 2, CompanyName = "New Orleans Cajun Delights", ContactName = "Shelley Burke", ContactTitle = "Order Administrator", City = "New Orleans", PostalCode = "70117", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 3, CompanyName = "Grandma Kelly's Homestead", ContactName = "Regina Murphy", ContactTitle = "Sales Representative", City = "Ann Arbor", PostalCode = "48104", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 4, CompanyName = "Tokyo Traders", ContactName = "Yoshi Nagase", ContactTitle = "Marketing Manager", City = "Tokyo", PostalCode = "100", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 5, CompanyName = "Cooperativa de Quesos 'Las Cabras'", ContactName = "Antonio del Valle Saavedra", ContactTitle = "Export Administrator", City = "Oviedo", PostalCode = "33007", Country = "Spain" });
            lItems.Add(new PersonDetail() { SupplierID = 6, CompanyName = "Mayumi's", ContactName = "Mayumi Ohno", ContactTitle = "Marketing Representative", City = "Osaka", PostalCode = "545", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 7, CompanyName = "Pavlova, Ltd.", ContactName = "Ian Devling", ContactTitle = "Marketing Manager", City = "Melbourne", PostalCode = "3058", Country = "Australia" });
            lItems.Add(new PersonDetail() { SupplierID = 8, CompanyName = "Specialty Biscuits, Ltd.", ContactName = "Peter Wilson", ContactTitle = "Sales Representative", City = "Manchester", PostalCode = "M14 GSD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 9, CompanyName = "PB Knäckebröd AB", ContactName = "Lars Peterson", ContactTitle = "Sales Agent", City = "Göteborg", PostalCode = "S-345 67", Country = "Sweden" });
            ViewBag.Datasource = lItems;
            return View();
        }
    }
}
{% endhighlight %}
{% endtabs %}

The following output is displayed as a result of the above code example.
![](Freeze-Pane_images/Freeze-Pane_img3.png)

N> On OTHERS tab click Freeze Top Row in FreezePanes dropdown list, to freeze top row. You can also freeze top row using [`freezeTopRow`](https://help.syncfusion.com/api/js/ejspreadsheet#methods:xlfreeze-freezetoprow "freezeTopRow") method. 

## Freeze Columns
It allows you to keep the certain number of column visible while scrolling through the rest of the work sheet.

The freeze columns can be applied in a following ways,

1. Initial Load
2. Method

### Initial Load
You can apply freeze columns using `FrozenColumns` property in sheets.
The following code example describes the above behavior

{% tabs %}
{% highlight cshtml %}
@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Datasource((IEnumerable<object>)ViewBag.Datasource).FrozenColumns(3).Add();
    })
)
{% endhighlight %}
{% highlight c# %}
namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            List<PersonDetail> lItems = new List<PersonDetail>();
            lItems.Add(new PersonDetail() { SupplierID = 1, CompanyName = "Exotic Liquids", ContactName = "Charlotte Cooper", ContactTitle = "Purchasing Manager", City = "London", PostalCode = "EC1 4SD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 2, CompanyName = "New Orleans Cajun Delights", ContactName = "Shelley Burke", ContactTitle = "Order Administrator", City = "New Orleans", PostalCode = "70117", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 3, CompanyName = "Grandma Kelly's Homestead", ContactName = "Regina Murphy", ContactTitle = "Sales Representative", City = "Ann Arbor", PostalCode = "48104", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 4, CompanyName = "Tokyo Traders", ContactName = "Yoshi Nagase", ContactTitle = "Marketing Manager", City = "Tokyo", PostalCode = "100", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 5, CompanyName = "Cooperativa de Quesos 'Las Cabras'", ContactName = "Antonio del Valle Saavedra", ContactTitle = "Export Administrator", City = "Oviedo", PostalCode = "33007", Country = "Spain" });
            lItems.Add(new PersonDetail() { SupplierID = 6, CompanyName = "Mayumi's", ContactName = "Mayumi Ohno", ContactTitle = "Marketing Representative", City = "Osaka", PostalCode = "545", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 7, CompanyName = "Pavlova, Ltd.", ContactName = "Ian Devling", ContactTitle = "Marketing Manager", City = "Melbourne", PostalCode = "3058", Country = "Australia" });
            lItems.Add(new PersonDetail() { SupplierID = 8, CompanyName = "Specialty Biscuits, Ltd.", ContactName = "Peter Wilson", ContactTitle = "Sales Representative", City = "Manchester", PostalCode = "M14 GSD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 9, CompanyName = "PB Knäckebröd AB", ContactName = "Lars Peterson", ContactTitle = "Sales Agent", City = "Göteborg", PostalCode = "S-345 67", Country = "Sweden" });
            ViewBag.Datasource = lItems;
            return View();
        }
    }
}
{% endhighlight %}
{% endtabs %}

### Method
You can apply freeze columns using [`freezeColumns`](https://help.syncfusion.com/api/js/ejspreadsheet#methods:xlfreeze-freezeColumns "freezeColumns") method. 
The following code example describes the above behavior

{% tabs %}
{% highlight cshtml %}
@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Datasource((IEnumerable<object>)ViewBag.Datasource).Add();
    })
    .ClientSideEvents(events => events.LoadComplete("loadComplete"))
)
<script type="text/javascript">
    function loadComplete(args) {
        if(!this.isImport) 
            this.XLFreeze.freezeColumns(3);
    }
</script>
{% endhighlight %}
{% highlight c# %}
namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            List<PersonDetail> lItems = new List<PersonDetail>();
            lItems.Add(new PersonDetail() { SupplierID = 1, CompanyName = "Exotic Liquids", ContactName = "Charlotte Cooper", ContactTitle = "Purchasing Manager", City = "London", PostalCode = "EC1 4SD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 2, CompanyName = "New Orleans Cajun Delights", ContactName = "Shelley Burke", ContactTitle = "Order Administrator", City = "New Orleans", PostalCode = "70117", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 3, CompanyName = "Grandma Kelly's Homestead", ContactName = "Regina Murphy", ContactTitle = "Sales Representative", City = "Ann Arbor", PostalCode = "48104", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 4, CompanyName = "Tokyo Traders", ContactName = "Yoshi Nagase", ContactTitle = "Marketing Manager", City = "Tokyo", PostalCode = "100", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 5, CompanyName = "Cooperativa de Quesos 'Las Cabras'", ContactName = "Antonio del Valle Saavedra", ContactTitle = "Export Administrator", City = "Oviedo", PostalCode = "33007", Country = "Spain" });
            lItems.Add(new PersonDetail() { SupplierID = 6, CompanyName = "Mayumi's", ContactName = "Mayumi Ohno", ContactTitle = "Marketing Representative", City = "Osaka", PostalCode = "545", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 7, CompanyName = "Pavlova, Ltd.", ContactName = "Ian Devling", ContactTitle = "Marketing Manager", City = "Melbourne", PostalCode = "3058", Country = "Australia" });
            lItems.Add(new PersonDetail() { SupplierID = 8, CompanyName = "Specialty Biscuits, Ltd.", ContactName = "Peter Wilson", ContactTitle = "Sales Representative", City = "Manchester", PostalCode = "M14 GSD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 9, CompanyName = "PB Knäckebröd AB", ContactName = "Lars Peterson", ContactTitle = "Sales Agent", City = "Göteborg", PostalCode = "S-345 67", Country = "Sweden" });
            ViewBag.Datasource = lItems;
            return View();
        }
    }
}
{% endhighlight %}
{% endtabs %}

The following output is displayed as a result of the above code example.
![](Freeze-Pane_images/Freeze-Pane_img4.png)

N> On OTHERS tab click Freeze First Column in FreezePanes dropdown list, to freeze left Column. You can also apply freeze first column using [`freezeLeftColumn`](https://help.syncfusion.com/api/js/ejspreadsheet#methods:xlfreeze-freezeleftcolumn "freezeLeftColumn") method. 

## Unfreeze Pane
Unfreeze all the rows and columns to scroll through entire sheet.

The unfreeze pane can be applied in a following ways,

1. User Interface
2. Method

### User Interface
On OTHERS tab click Unfreeze Panes in Freeze Panes dropdown list.
![](Freeze-Pane_images/Freeze-Pane_img5.png)

### Method
You can unfreeze rows or columns using [`unfreezePanes`](https://help.syncfusion.com/api/js/ejspreadsheet#methods:xlfreeze-unfreezepanes "unfreezePanes") method. 

The following code example describes the above behavior,

{% tabs %}
{% highlight cshtml %}
@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Datasource((IEnumerable<object>)ViewBag.Datasource).Add();
    })
    .ClientSideEvents(events => events.LoadComplete("loadComplete"))
)
<script type="text/javascript">
    function loadComplete(args) {
        if (!this.isImport){
            this.XLFreeze.freezePanes(5,2);
            this.XLFreeze.unfreezePanes();
        }
    }
</script>
{% endhighlight %}
{% highlight c# %}
namespace MVCSampleBrowser.Controllers
{
    public partial class SpreadsheetController : Controller
    {
        public ActionResult Default()
        {
            List<PersonDetail> lItems = new List<PersonDetail>();
            lItems.Add(new PersonDetail() { SupplierID = 1, CompanyName = "Exotic Liquids", ContactName = "Charlotte Cooper", ContactTitle = "Purchasing Manager", City = "London", PostalCode = "EC1 4SD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 2, CompanyName = "New Orleans Cajun Delights", ContactName = "Shelley Burke", ContactTitle = "Order Administrator", City = "New Orleans", PostalCode = "70117", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 3, CompanyName = "Grandma Kelly's Homestead", ContactName = "Regina Murphy", ContactTitle = "Sales Representative", City = "Ann Arbor", PostalCode = "48104", Country = "USA" });
            lItems.Add(new PersonDetail() { SupplierID = 4, CompanyName = "Tokyo Traders", ContactName = "Yoshi Nagase", ContactTitle = "Marketing Manager", City = "Tokyo", PostalCode = "100", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 5, CompanyName = "Cooperativa de Quesos 'Las Cabras'", ContactName = "Antonio del Valle Saavedra", ContactTitle = "Export Administrator", City = "Oviedo", PostalCode = "33007", Country = "Spain" });
            lItems.Add(new PersonDetail() { SupplierID = 6, CompanyName = "Mayumi's", ContactName = "Mayumi Ohno", ContactTitle = "Marketing Representative", City = "Osaka", PostalCode = "545", Country = "Japan" });
            lItems.Add(new PersonDetail() { SupplierID = 7, CompanyName = "Pavlova, Ltd.", ContactName = "Ian Devling", ContactTitle = "Marketing Manager", City = "Melbourne", PostalCode = "3058", Country = "Australia" });
            lItems.Add(new PersonDetail() { SupplierID = 8, CompanyName = "Specialty Biscuits, Ltd.", ContactName = "Peter Wilson", ContactTitle = "Sales Representative", City = "Manchester", PostalCode = "M14 GSD", Country = "UK" });
            lItems.Add(new PersonDetail() { SupplierID = 9, CompanyName = "PB Knäckebröd AB", ContactName = "Lars Peterson", ContactTitle = "Sales Agent", City = "Göteborg", PostalCode = "S-345 67", Country = "Sweden" });
            ViewBag.Datasource = lItems;
            return View();
        }
    }
}
{% endhighlight %}
{% endtabs %}

The following output is displayed as a result of the above code example.
![](Freeze-Pane_images/Freeze-Pane_img6.png)


