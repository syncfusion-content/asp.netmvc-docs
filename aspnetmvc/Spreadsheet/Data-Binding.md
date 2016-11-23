---
title: Data binding with Spreadsheet widget for Syncfusion Essential ASP.NET MVC
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
        sheet.Datasource((IEnumerable<object>)ViewBag.Datasource).Add();
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
            List<ItemDetail> lItems = new List<ItemDetail>();
            lItems.Add(new ItemDetail() { ItemName = "Casual Shoes", Date = new DateTime(2014, 02, 14), Time = new DateTime(2014, 02, 14, 11, 34, 32), Quantity = 10, Price = 20, Amount = 200, Discount = 1, Profit = 10 });
            lItems.Add(new ItemDetail() { ItemName = "Sports Shoes", Date = new DateTime(2014, 06, 11), Time = new DateTime(2014, 06, 11, 05, 56, 32), Quantity = 20, Price = 30, Amount = 600, Discount = 5, Profit = 50 });
            lItems.Add(new ItemDetail() { ItemName = "Formal Shoes", Date = new DateTime(2014, 07, 27), Time = new DateTime(2014, 07, 27, 03, 32, 44), Quantity = 20, Price = 15, Amount = 300, Discount = 7, Profit = 27 });
            lItems.Add(new ItemDetail() { ItemName = "Sandals & Floaters", Date = new DateTime(2014, 11, 21), Time = new DateTime(2014, 11, 21, 06, 23, 54), Quantity = 15, Price = 20, Amount = 300, Discount = 11, Profit = 67 });
            lItems.Add(new ItemDetail() { ItemName = "Flip- Flops & Slippers", Date = new DateTime(2014, 06, 23), Time = new DateTime(2014, 06, 23, 12, 43, 59), Quantity = 30, Price = 10, Amount = 300, Discount = 10, Profit = 70 });
            ViewBag.Datasource = lItems;
            return View();
        }
    }
}

{% endhighlight %}
{% endtabs %}

The following output is displayed as a result of the above code snippets.
![](Data-Binding_images/Data-Binding_img1.png)

## Remote Data

To bind remote data to the Spreadsheet, you can assign a service data as an instance of `DataManager` to the worksheet `DataSource` property. The following code illustrates how to bind remote data to the Spreadsheet,

{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Datasource("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders")
        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight'])
        .take(5)").Add();
    })
)
    
{% endhighlight %}

The following output is displayed as a result of the above code snippets.
![](Data-Binding_images/Data-Binding_img2.png)

## HTML Table Data

A HTML Table element can also be used as the data source of Spreadsheet. To use HTML Table as data source, the table element should be passed to worksheet `DataSource` property of Spreadsheet as an instance of the `DataManager`. The following code illustrates how to bind HTML Table data to the Spreadsheet,

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
![](Data-Binding_images/Data-Binding_img3.png)

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

@(Html.EJ().Spreadsheet<ItemDetail>("Spreadsheet")
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
![](Data-Binding_images/Data-Binding_img4.png)

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
            List<ItemDetail> lItems = new List<ItemDetail>();
            lItems.Add(new ItemDetail() { ItemName = "Casual Shoes", Date = new DateTime(2014, 02, 14), Time = new DateTime(2014, 02, 14, 11, 34, 32), Quantity = 10, Price = 20, Amount = 200, Discount = 1, Profit = 10 });
            lItems.Add(new ItemDetail() { ItemName = "Sports Shoes", Date = new DateTime(2014, 06, 11), Time = new DateTime(2014, 06, 11, 05, 56, 32), Quantity = 20, Price = 30, Amount = 600, Discount = 5, Profit = 50 });
            lItems.Add(new ItemDetail() { ItemName = "Formal Shoes", Date = new DateTime(2014, 07, 27), Time = new DateTime(2014, 07, 27, 03, 32, 44), Quantity = 20, Price = 15, Amount = 300, Discount = 7, Profit = 27 });
            lItems.Add(new ItemDetail() { ItemName = "Sandals & Floaters", Date = new DateTime(2014, 11, 21), Time = new DateTime(2014, 11, 21, 06, 23, 54), Quantity = 15, Price = 20, Amount = 300, Discount = 11, Profit = 67 });
            lItems.Add(new ItemDetail() { ItemName = "Flip- Flops & Slippers", Date = new DateTime(2014, 06, 23), Time = new DateTime(2014, 06, 23, 12, 43, 59), Quantity = 30, Price = 10, Amount = 300, Discount = 10, Profit = 70 });
            ViewBag.Datasource = lItems;
            return View();
        }
    }
}

{% endhighlight %}
{% endtabs %}
The following output is displayed as a result of the above code snippets.

![](Data-Binding_images/Data-Binding_img5.png)

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
            DataManager
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
        .take(5)").FieldAsColumnHeader(true).PrimaryKey("OrderID").Add();
    })
)
    
{% endhighlight %}

The following output is displayed as a result of the above code snippets. 
![](Data-Binding_images/Data-Binding_img6.png)

