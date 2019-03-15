---
title: Formula support with Spreadsheet widget for Syncfusion Essential ASP.NET MVC
description: How to use formulas in Spreadsheet with cell references, named ranges etc.
platform: ejmvc
control: Spreadsheet
documentation: ug
---
# Formulas

Formulas are used for calculation of data in sheet. You can refer the formula cell reference in following ways,

1. Cell reference from same sheet
2. Cell reference from different sheets

You can set formula for a `cell` in following ways,

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
        sheet.Rows(rows =>
        {
            rows.Cells(cells =>
            {
                cells.Value("=Sheet1!A1:A2").Add();
            }).Add();
        }).Add();
    })
)

{% endhighlight %}

The following output is displayed as a result of the above code example.
![](Formulas_images/Formula_img6.png)

Cell Reference from Same sheet
{:.caption}

![Formula](Formulas_images/Formula_img7.png)

Cell Reference from different sheets
{:.caption}

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
![](Formulas_images/Formula_img1.png)

### User Interface

You can set formula for a cell by edit and save a cell through user interface using `Editing` feature. 

The following code example and screenshot describes the above behavior,

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

![](Formulas_images/Formula_img2.png)

The following output is displayed while saving edited cell with above code example.
![](Formulas_images/Formula_img1.png)

N> 1. The list of supported formulas can be find in following [`link`](https://help.syncfusion.com/js/calculate/supported-formulas/supported-formulas "link")
N> 2. Constant values, cell references, formulas and named ranges can be passed as argument to formulas
N> 3. Selection can be used to mention cell references within formula

## User Defined Functions

The list of formulas supported in Spreadsheet is sufficient for most of your calculations. If not, you can create and use your own function using user defined function option. You can add user defined function to Spreadsheet in following ways,

1. Initial Load

2. Method

### Initial Load

You can add your own function to Spreadsheet at initial load with `CustomFormulas` property. The following code example describes the above behavior,

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
                cells.Value("=CUSTOMTOTAL(A1,A2,3)").Add();
            }).Add();
        }).Add();
    })
    .CustomFormulas(formula => { formula.FormulaName("CUSTOMTOTAL").FunctionName("customTotal").Add(); })
    )

<script>
function customTotal(args) {
     var param1, param2, param3, value, excelObj = $('#Spreadsheet').data("ejSpreadsheet"),
     argument = excelObj.getValueFromFormulaArg(args);
     param1 = argument["arg1"];
     param2 = argument["arg2"];
     param3 = argument["arg3"];
     value = param1 * param2 + param3;
    return value;
}
</script>
 
{% endhighlight %}

The following output is displayed as a result of the above code example.
![](Formulas_images/Formula_img5.png)

### Method

You can add your own function to Spreadsheet using [`addCustomFormula`](https://help.syncfusion.com/js/api/ejspreadsheet#methods:addcustomformula "addCustomFormula") method. The following code example describes the above behavior,

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
        this.addCustomFormula("CUSTOMTOTAL", "customTotal");
        this.XLEdit.updateCellValue({ rowIndex: 2, colIndex: 0 }, "=CUSTOMTOTAL(A1,A2,3)");
    }
    function customTotal(args) {
        var param1, param2, param3, value, excelObj = $('#Spreadsheet').data("ejSpreadsheet"),
        argument = excelObj.getValueFromFormulaArg(args);
        param1 = argument["arg1"];
        param2 = argument["arg2"];
        param3 = argument["arg3"];
        value = param1 * param2 + param3;
        return value;
    }
</script>

{% endhighlight %}

The following output is displayed as a result of the above code example.
![](Formulas_images/Formula_img5.png)

To remove user defined function from Spreadsheet use [`removeCustomFormula`](https://help.syncfusion.com/js/api/ejspreadsheet#methods:removecustomformula "removeCustomFormula") method.

## Named Ranges

To understand the purpose of cell reference or table, you can define a meaningful name using named ranges support. By using names, you can make your formula much easier to understand and maintain. You can add named ranges to Spreadsheet in following ways,
    
1. Initial Load
    
2. Method

3. User Interface

### Initial Load

To add named ranges at initial load by using [`nameManager`](https://help.syncfusion.com/api/js/ejspreadsheet#members:namemanager "nameManager") API, and also you can specify the name and address of the range by using [`name`](https://help.syncfusion.com/api/js/ejspreadsheet#members:namemanager-name "name") and [`refersto`](https://help.syncfusion.com/api/js/ejspreadsheet#members:namemanager-refersto "refersto") API. You can find the added named range list collection in Spreadsheet by accessing [`nameManager`](https://help.syncfusion.com/api/js/ejspreadsheet#members:namemanager "nameManager") API.

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
        rows.Cells(cells =>
        {
            cells.Value("=SUM(inputRange)").Add();
        }).Add();
    }).Add();
})
    .NameManager(manager => { manager.Name("inputRange").RefersTo("=Sheet1!$A$1:$A$2").Add(); })
)

{% endhighlight %}

The following output is displayed as a result of the above code example.
![](Formulas_images/Formula_img3.png)

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
        this.XLRibbon.addNamedRange("inputRange", "=Sheet1!$A$1:$A$2", "named range demo", this.getActiveSheetIndex());
        this.XLEdit.updateCellValue({rowIndex: 2, colIndex: 0}, "=SUM(inputRange)");            
    }
</script>

{% endhighlight %}

The following output is displayed as a result of the above code example.
![](Formulas_images/Formula_img3.png)

### User Interface

You can define name for range of cells through user interface using `Define Name` option in `OTHERS` tab. The following screenshot describes the above behavior,
![](Formulas_images/Formula_img4.png)

N> 1. Defining name for cell reference or table will be accessible across all sheets.
N> 2. Named Ranges will be displayed in Name Manger dialog box.

## Formula Bar

Formula bar is used to edit or enter cell data in much easier way. To enable formula bar set `AllowFormulaBar` as `true`.

## Auto Sum

To sum a row or column of data, select a cell next to the data you want to sum, click `AutoSum` on the `HOME` tab and press enter. To enable auto sum set `AllowAutoSum` API as `true`.
The auto sum options in ribbon is used to perform basic operations like sum, average, count, minimum, maximum etc.