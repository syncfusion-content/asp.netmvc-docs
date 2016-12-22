---
title: Formula support with Spreadsheet widget for Syncfusion Essential ASP.NET MVC
description: How to use formulas in Spreadsheet with cell references, named ranges etc.
platform: ejmvc
control: Spreadsheet
documentation: ug
---
# Formulas

Formulas are used for calculation of data in sheet. You can set formula for a `cell` in following ways,

1. Initial Load
2. Method
3. User Interface

### Initial Load

You can set formula for a cell by specifying `Value` property in cell data binding. The following code example describes the above behavior,

{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Rows(rows =>
        {
            rows.Cells(cells =>
            {
                cells.Value("1").Add();
            }).Add();
            rows.Cells(cells =>
            {
                cells.Value("2").Add();
            }).Add();
            rows.Cells(cells =>
            {
                cells.Value("=SUM(A1,A2)").Add();
            }).Add();
        }).Add();
    })
)

{% endhighlight %}

The following output is displayed as a result of the above code example.
![](Formula_images/Formula_img1.png)

### Method

You can set formula for a cell using [`updateCellValue`](https://help.syncfusion.com/api/js/ejspreadsheet#methods:xledit-updatecellvalue "updateCellValue") method. The following code example describes the above behavior,

{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Rows(rows =>
        {
            rows.Cells(cells =>
            {
                cells.Value("1").Add();
            }).Add();
            rows.Cells(cells =>
            {
                cells.Value("2").Add();
            }).Add();
        }).Add();
    })
    .ClientSideEvents(events => events.LoadComplete("loadComplete"))
)

<script>
    function loadComplete() {
        this.XLEdit.updateCellValue({ rowIndex: 2, colIndex: 0 }, "=SUM(A1,A2)");
    }
</script>

{% endhighlight %}

The following output is displayed as a result of the above code example.
![](Formula_images/Formula_img1.png)

### User Interface

You can set formula for a cell by edit and save a cell through user interface using `Editing` feature. 

The following screenshot describes the above behavior,

{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Rows(rows =>
        {
            rows.Cells(cells =>
            {
                cells.Value("1").Add();
            }).Add();
            rows.Cells(cells =>
            {
                cells.Value("2").Add();
            }).Add();
        }).Add();
    })
)

{% endhighlight %}

![](Formula_images/Formula_img2.png)

The following output is displayed while saving edited cell with above code example.
![](Formula_images/Formula_img1.png)

N> 1. The list of supported formulas can be find in following [`link`](https://help.syncfusion.com/js/calculate/supported-formulas/supported-formulas "link")
N> 2. Constant values, cell references, formulas and named ranges can be passed as argument to formulas
N> 3. Selection can be used to mention cell references within formula

## Named Ranges

To give descriptive name for cell reference or table and it can be used in formula. In Spreadsheet name can be added to cell reference in following ways,
    
1. Method

2. User Interface

### Method

You can add named range to Spreadsheet with [`addNamedRange`](https://help.syncfusion.com/api/js/ejspreadsheet#methods:xlribbon-addnamedrange "addNamedRange") method and it can be removed with [`removeNamedRange`](https://help.syncfusion.com/api/js/ejspreadsheet#methods:xlribbon-removenamedrange "removeNamedRange") method. 

The following code example describes the above behavior,

{% highlight cshtml %}

@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .Sheets(sheet =>
    {
        sheet.Rows(rows =>
        {
            rows.Cells(cells =>
            {
                cells.Value("1").Add();
            }).Add();
            rows.Cells(cells =>
            {
                cells.Value("2").Add();
            }).Add();
        }).Add();
    })
    .ClientSideEvents(events => events.LoadComplete("loadComplete"))
)

<script>
    function loadComplete() {
        this.XLRibbon.addNamedRange("inputrange", "=Sheet1!$A$1:$A$2", "named range demo", this.getActiveSheetIndex());
        this.XLEdit.updateCellValue({rowIndex: 2, colIndex: 0}, "=SUM(inputrange)");            
    }
</script>

{% endhighlight %}

The following output is displayed as a result of the above code example.
![](Formula_images/Formula_img3.png)

### User Interface

You can define name for range of cells through user interface using `Define Name` option in `OTHERS` tab. The following screenshot describes the above behavior,
![](Formula_images/Formula_img4.png)

N> Defining name for cell reference or table will be accessible across all sheets
N> Named Ranges will be displayed in Name Manger dialog box.

## Formula Bar

Formula bar is used to edit or enter cell data in much easier way. To enable formula bar set `AllowFormulaBar` as `true`.

## Auto Sum

To sum a row or column of data, select a cell next to the data you want to sum, click `AutoSum` on the `HOME` tab and press enter. To enable auto sum set `AllowAutoSum` API as `true`.
The auto sum options in ribbon is used to perform basic operations like sum, average, count, minimum, maximum etc.