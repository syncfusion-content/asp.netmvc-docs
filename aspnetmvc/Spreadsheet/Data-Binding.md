---
title: Data binding with Spreadsheet widget | Syncfusion
description: How to perform Data Binding and configure its properties like dataSource, query etc.
platform: ejmvc
control: Spreadsheet
documentation: ug
---
# Data Binding

Spreadsheet can be populated with external datasource using `DataSource` property. The `DataSource` property can be assigned either with the instance of `DataManager` or JSON data array collection. Spreadsheet supports three different kinds of Data binding.

* Local Data
* Remote Data
* HTML Table Data

## Local Data

To bind local data to the Spreadsheet, you can assign a JSON array to the worksheet `DataSource` property. The following code illustrates how to bind local data to the Spreadsheet,

{% tabs %}
{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        range.Datasource((IEnumerable<object>)ViewBag.Datasource).ShowHeader(false).Add();
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
            List<OrderDetail> lItems = new List<OrderDetail>();
            lItems.Add(new OrderDetail() { OrderID = 10248, CustomerID = "VINET", EmployeeID = 5, ShipCity = "Reims", ShipCountry = "France" });
            lItems.Add(new OrderDetail() { OrderID = 10249, CustomerID = "TOMSP", EmployeeID = 6, ShipCity = "Münster", ShipCountry = "Germany" });
            lItems.Add(new OrderDetail() { OrderID = 10250, CustomerID = "HANAR", EmployeeID = 4, ShipCity = "Rio de Janeiro", ShipCountry = "Brazil" });
            lItems.Add(new OrderDetail() { OrderID = 10251, CustomerID = "VICTE", EmployeeID = 3, ShipCity = "Lyon", ShipCountry = "France" });
            lItems.Add(new OrderDetail() { OrderID = 10252, CustomerID = "SUPRD", EmployeeID = 4, ShipCity = "Charleroi", ShipCountry = "Belgium" });
            ViewBag.Datasource = lItems;
            return View();
        }
    }
}

{% endhighlight %}
{% endtabs %}

The following output is displayed as a result of the above code snippets.
![Local data binding](Data-Binding_images/Data-Binding_img1.png)

## Remote Data

To bind remote data to the Spreadsheet, you can assign a service data as an instance of `DataManager` to the worksheet `DataSource` property. The following code illustrates how to bind remote data to the Spreadsheet,

{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Datasource("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders")
        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight'])
        .take(50)").Add();
    })
)
    
{% endhighlight %}

The following output is displayed as a result of the above code snippets.
![Remote data binding](Data-Binding_images/Data-Binding_img2.png)

### Offline Mode

To avoid sending post back request to server on every action, Spreadsheet allows user to create, update and delete data on client side. To enable this, set `Offline` property of `DataManager` as `true` to fetch all data from server on initial rendering of Spreadsheet and perform all operation on client side.

The following code illustrates Offline data binding for Spreadsheet,

{% highlight cshtml %}

@(Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/").Offline(true)))

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.DataManagerID("FlatData")
        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipName',  'ShipAddress'])")
        .PrimaryKey("OrderID").Add();
    })
)
    
{% endhighlight %}

The following output is displayed as a result of the above code snippets.
![Offline mode](Data-Binding_images/Data-Binding_img2.png)

N> For further reference about `Offline` property in `DataManager` refer following [`link`](https://help.syncfusion.com/aspnetmvc/datamanager/data-binding#offline-mode "link")

## HTML Table Data

An HTML Table element can also be used as the data source of Spreadsheet. To use HTML Table as data source, the table element should be passed to worksheet `DataSource` property of Spreadsheet as an instance of the `DataManager`. The following code illustrates how to bind HTML Table data to the Spreadsheet,

{% highlight cshtml %}

@(Html.EJ().DataManager("FlatData").Table("#_table1"))

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.DataManagerID("FlatData").Add();
    })
)

<script id="_table1" type="text/template">    
    <table id="Table1">
        <thead>
            <tr>
                <th>Laptop</th>
                <th>Model</th>
                <th>Price</th>
                <th>OS</th>
                <th>RAM</th>
                <th>ScreenSize</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Dell Vostro</td>
                <td>2520</td>
                <td>39990</td>
                <td>Windows 8</td>
                <td>4GB</td>
                <td>15.6</td>
            </tr>
            <tr>
                <td>HP Pavilion Sleekbook</td>
                <td>14-B104AU</td>
                <td>22800</td>
                <td>Windows 8</td>
                <td>2GB</td>
                <td>14</td>
            </tr>
            <tr>
                <td>Sony Vaio</td>
                <td>E14A15</td>
                <td>42500</td>
                <td>Windows 7 Home Premium</td>
                <td>4GB DDR3 RAM</td>
                <td>14</td>
            </tr>
            <tr>
                <td>Lenovo</td>
                <td>Yoga 13</td>
                <td>57000</td>
                <td>Windows 8 RT</td>
                <td>2GB DDR3 RAM</td>
                <td>11.6</td>
            </tr>
            <tr>
                <td>Toshiba</td>
                <td>L850-Y3110</td>
                <td>57700</td>
                <td>Windows 8 SL</td>
                <td>8GB DDR3 RAM</td>
                <td>15.6</td>
            </tr>
        </tbody>
    </table>
</script>
{% endhighlight %}

The following output is displayed as a result of the above code snippets.
![Html table data source](Data-Binding_images/Data-Binding_img3.png)

## Ways to bind data in Spreadsheet

You can bind data to Spreadsheet in following ways,

* Cell binding
* Range binding
* Sheet binding

### Cell Binding

Spreadsheet can bind data for individual cells in a sheet. The data may contain value, style, format, comment and hyperlink. The individual cell properties are listed below,

<table>
    <tr>
        <th>
            Properties
        </th>
        <th>
            Description
        </th>
    </tr>
    <tr>
        <td>
            Index
        </td>
        <td>
            To specify particular cell
        </td>
    </tr>
    <tr>
        <td>
            Value
        </td>
        <td>
            To specify value. It may be string, integer, formula etc.
        </td>
    </tr>
    <tr>
        <td>
            Style
        </td>
        <td>
            To specify style in the cell
        </td>
    </tr>
    <tr>
        <td>
            Format
        </td>
        <td>
            To specify number format in the cell
        </td>
    </tr>
    <tr>
        <td>
            Comment
        </td>
        <td>
            To specify comment in the cell
        </td>
    </tr>
    <tr>        
        <td>
            Hyperlink
        </td>
        <td>
            To specify hyperlink in the cell
        </td>
    </tr>
</table>

The individual row properties are listed below,

<table>
    <tr>
        <th>
            Properties
        </th>
        <th>
            Description
        </th>
    </tr>
    <tr>
        <td>
            Index
        </td>
        <td>
            To specify particular row
        </td>
    </tr>
    <tr>
        <td>
            Height
        </td>
        <td>
            To specify height in the row
        </td>
    </tr>
</table>

You can specify particular row with `Index` property and its height with `Height` property in the `Rows` property collection. The following code illustrates cell binding in Spreadsheet,

{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .ScrollSettings(scroll =>
    {
        scroll.Height(510);
    })
    .Sheets(sheet =>
    {
        sheet.Rows(rows =>
        {
            rows.Height(30).Cells(cells =>
            {
                cells.Value("Item Name").Style(style =>
                {
                    style.FontWeight("bold").Color("#FFFFFF").BackgroundColor("#428bca");
                }).Add();
                cells.Value("Quantity").Style(style =>
                {
                    style.FontWeight("bold").Color("#FFFFFF").BackgroundColor("#428bca");
                }).Add();
                cells.Value("Price").Style(style =>
                {
                    style.FontWeight("bold").Color("#FFFFFF").BackgroundColor("#428bca");
                }).Add();
                cells.Value("Amount").Style(style =>
                {
                    style.FontWeight("bold").Color("#FFFFFF").BackgroundColor("#428bca");
                }).Add();
                cells.Value("Stock Details").Style(style =>
                {
                    style.FontWeight("bold").Color("#FFFFFF").BackgroundColor("#428bca");
                }).Add();
                cells.Value("Website").Style(style =>
                {
                    style.FontWeight("bold").Color("#FFFFFF").BackgroundColor("#428bca");
                }).Add();
            }).Add();
            rows.Cells(cells =>
            {
                cells.Value("Casual Shoes").Comment(comment =>
                {
                    comment.Value("Casual Footwears with wide variety of colors.");
                }).Add();
                cells.Value("10").Add();
                cells.Value("20").Format(format =>
                {
                    format.Type("currency");
                }).Add();
                cells.Value("=B2*C2").Add();
                cells.Value("OUT OF STOCK").Add();
                cells.Value("Amazon").Hyperlink(hyperlink =>
                {
                    hyperlink.WebAddr("www.amazon.com");
                }).Add();
            }).Add();
            rows.Cells(cells =>
            {
                cells.Value("Sports Shoes").Style(style =>
                {
                    style.BackgroundColor("#E5F3FF");
                }).Add();
                cells.Value("20").Style(style =>
                {
                    style.BackgroundColor("#E5F3FF");
                }).Add();
                cells.Value("30").Format(format =>
                {
                    format.Type("currency");
                }).Style(style =>
                {
                    style.BackgroundColor("#E5F3FF");
                }).Add();
                cells.Value("=B3*C3").Style(style =>
                {
                    style.BackgroundColor("#E5F3FF");
                }).Add();
                cells.Value("IN STOCK").Style(style =>
                {
                    style.BackgroundColor("#E5F3FF");
                }).Add();
                cells.Value("AliExpress").Hyperlink(hyperlink =>
                {
                    hyperlink.WebAddr("www.aliexpress.com");
                }).Style(style =>
                {
                    style.BackgroundColor("#E5F3FF");
                }).Add();
            }).Add();
            rows.Cells(cells =>
            {
                cells.Value("Formal Shoes").Comment(comment =>
                {
                    comment.Value("Formal Footwears with wide range of sizes.");
                }).Add();
                cells.Value("20").Add();
                cells.Value("15").Format(format =>
                {
                    format.Type("currency");
                }).Add();
                cells.Value("=B4*C4").Add();
                cells.Value("IN STOCK").Add();
                cells.Value("Amazon").Hyperlink(hyperlink =>
                {
                    hyperlink.WebAddr("www.amazon.com");
                }).Add();
            }).Add();
            rows.Height(30).Cells(cells =>
            {
                cells.Style(style =>
                {
                    style.BackgroundColor("#428bca");
                }).Add();
                cells.Style(style =>
                {
                    style.BackgroundColor("#428bca");
                }).Add();
                cells.Value("Total Amount").Index(2).Style(style =>
                {
                    style.FontWeight("bold").Color("#FFFFFF").BackgroundColor("#428bca");
                }).Add();
                cells.Value("=Sum(D2:D4)").Style(style =>
                {
                    style.FontWeight("bold").Color("#FFFFFF").BackgroundColor("#428bca");
                }).Add();
                cells.Style(style =>
                {
                    style.BackgroundColor("#428bca");
                }).Add();
                cells.Style(style =>
                {
                    style.BackgroundColor("#428bca");
                }).Add();
            }).Add();
        }).Add();
    })
)

{% endhighlight %}

The following output is displayed as a result of the above code snippets.
![Cell Binding](Data-Binding_images/Data-Binding_img4.png)

### Range Binding

Spreadsheet can bind data for one or more range in a sheet using `RangeSettings`. The individual range properties are listed below,

<table>
    <tr>
        <th>
            Properties
        </th>
        <th>
            Description
        </th>
    </tr>
    <tr>
        <td>
            DataSource
        </td>
        <td>
            To specify JSON or {{'`DataManager`' | markdownify}}
        </td>
    </tr>
    <tr>    
        <td>
            Query
        </td>
        <td>
            To specify query for {{'`DataManager`' | markdownify}}
        </td>
    </tr>
    <tr>
        <td>    
            StartCell
        </td>
        <td>
            To specify start cell of a range
        </td>
    </tr>
    <tr>
        <td>
            PrimaryKey
        </td>
        <td>
            To specify data source primary key
        </td>
    </tr>
    <tr>
        <td>
            ShowHeader
        </td>
        <td>
            To show data source header
        </td>
    </tr>
    <tr>
        <td>
            HeaderStyles
        </td>
        <td>
            To specify header styles
        </td>
    </tr>
</table>

The following code illustrates range binding in Spreadsheet

{% tabs %}
{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.RangeSettings(range =>
        {
            range.Datasource((IEnumerable<object>)ViewBag.Datasource).StartCell("C2").ShowHeader(true).Add();
        }).Add();
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
            List<MarkDetail> lItems = new List<MarkDetail>();
            lItems.Add(new MarkDetail() { Name = "VINET", Average = 90, Grade = "S" });
            lItems.Add(new MarkDetail() { Name = "TOMSP", Average = 83, Grade = "A" });
            lItems.Add(new MarkDetail() { Name = "HANAR", Average = 80, Grade = "A" });
            lItems.Add(new MarkDetail() { Name = "VICTE", Average = 93, Grade = "S" });
            lItems.Add(new MarkDetail() { Name = "SUPRD", Average = 60, Grade = "D" });
            lItems.Add(new MarkDetail() { Name = "CHOPS", Average = 71, Grade = "C" });
            lItems.Add(new MarkDetail() { Name = "WELLI", Average = 88, Grade = "A" });
            lItems.Add(new MarkDetail() { Name = "HILLA", Average = 95, Grade = "S" });
            lItems.Add(new MarkDetail() { Name = "ERNSH", Average = 69, Grade = "D" });
            lItems.Add(new MarkDetail() { Name = "CENTC", Average = 77, Grade = "C" });
            lItems.Add(new MarkDetail() { Name = "OTTIK", Average = 95, Grade = "S" });
            lItems.Add(new MarkDetail() { Name = "RATTC", Average = 85, Grade = "A" });
            lItems.Add(new MarkDetail() { Name = "FOLKO", Average = 90, Grade = "A" });
            lItems.Add(new MarkDetail() { Name = "BLONP", Average = 97, Grade = "S" });
            ViewBag.Datasource = lItems;
            return View();
        }
    }
}

{% endhighlight %}
{% endtabs %}
The following output is displayed as a result of the above code snippets.

![Range binding](Data-Binding_images/Data-Binding_img5.png)

### Sheet Binding

Spreadsheet can bind data for a sheet. The individual sheet properties are listed below,

<table>
    <tr>
        <th>
            Properties
        </th>
        <th>
            Description
        </th>
    </tr>
    <tr>
        <td>
            DataSource
        </td>
        <td>
            To specify JSON or {{'`DataManager`' | markdownify}}
        </td>
    </tr>
    <tr>
        <td>
            Query
        </td>
        <td>
            To specify query for {{'`DataManager`' | markdownify}}
        </td>
    </tr>
    <tr>
        <td>
            StartCell
        </td>
        <td>
            To specify start cell of a range
        </td>
    </tr>
    <tr>
        <td>
            PrimaryKey
        </td>
        <td>
            To specify data source primary key
        </td>
    </tr>
    <tr>
        <td>
            ShowHeader
        </td>
        <td>
            To show data source header
        </td>
    </tr>
    <tr>
        <td>
            HeaderStyles
        </td>
        <td>
            To specify header styles
        </td>
    </tr>
    <tr>
        <td>
            FieldAsColumnHeader
        </td>
        <td>
            To show data source fields in column header
        </td>
    </tr>
</table>

The following code illustrates sheet binding in Spreadsheet

{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Datasource("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders")
        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight'])
        .take(50)").FieldAsColumnHeader(true).PrimaryKey("OrderID").Add();
    })
)
    
{% endhighlight %}

The following output is displayed as a result of the above code snippets. 
![Sheet Binding](Data-Binding_images/Data-Binding_img6.png)

