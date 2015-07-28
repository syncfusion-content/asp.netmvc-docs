---
layout: post
title: Filtering
description: filtering
platform: ejmvc
control: Grid
documentation: ug
---

# Filtering

Filtering is used to filter particular or related records in Grid to review details of records. To enable filtering behavior in Grid you can add AllowFiltering property at Grid initialize. There are three types of filtering features in grid. They are

* Filter menu
* Filter Bar
* Excel styled menu
## Filter Menu 


After you enable Filter Menu in Grid, it shows filter menu to filter records. This menu contains filtering options based on column type.

##Filter menu types

* String menu filtering 
* Numeric menu filtering
* Date menu filtering
* Boolean menu filtering

Filter menus are a good UI based filtering option. It visibly denotes filtering option and is flexible to filter records. In String menu filtering, AutoComplete is used as default control to filter; in Numeric menu filtering, NumericTextbox is used as default control to filter. In Date menu filtering, DatePicker control is used as default control to filter and in Boolean menu filtering, CheckBox is used for filtering. 




{% highlight html %}



@(Html.EJ().Grid<EditableOrder>("Grid")

      .Datasource((IEnumerable<object>)ViewBag.datasource)

      .AllowPaging()

.AllowFiltering()

      .FilterSettings(filter => { filter.FilterType(FilterType.Menu); })

    )

{% endhighlight %}

{% highlight C# %}

namespace MVCSampleBrowser.Controllers

{

    public partial class GridController : Controller

    {

        public ActionResult FilteringMenu()

        {

            var DataSource = OrderRepository.GetAllRecords();

            ViewBag.datasource = DataSource;

            return View();

        }



    }

}

{% endhighlight %}



The following output is displayed as a result of the above code example.



![](Filtering_images/Filtering_img1.png)



### Filter Bar

Filter bar is one of the types of filtering. It is otherwise called text filtering as filter bar working is based on text boxes. Through this you can filter records. Filter bars have expression to filter records. They are based on type of column. 

_Table 2 : List of Filter Bar Expressions_
{% highlight html %}
<table>
<tr>
<td rowspan = "4">
Numeric column</td><td>
> value</td><td rowspan = "4">
To filter numeric column. You can use these expressions.</td></tr>
<tr>
<td>
< value</td></tr>
<tr>
<td>
= value</td></tr>
<tr>
<td>
!= value</td></tr>
<tr>
<td>
String</td><td>
startsWith</td><td>
By default, string filtering works starts with operator</td></tr>
<tr>
<td>
Date</td><td>
Equal</td><td>
By default, date filter bar matches records with same date value</td></tr>
<tr>
<td>
Boolean</td><td>
Equal</td><td>
Boolean filter bar works with either true or false.</td></tr>
</table>

{% endhighlight %}


{% highlight html %}

@(Html.EJ().Grid<EditableOrder>("Grid")

      .Datasource((IEnumerable<object>)ViewBag.datasource)

      .AllowPaging()

.AllowFiltering()

      .FilterSettings(filter => { filter.FilterType(FilterType.FilterBar); })

    )

{% endhighlight %}

{% highlight C# %}

namespace MVCSampleBrowser.Controllers

{

    public partial class GridController : Controller

    {

        public ActionResult Filtering()

        {

            var DataSource = OrderRepository.GetAllRecords();

            ViewBag.datasource = DataSource;

            return View();

        }



    }

}


{% endhighlight %}






The following output is displayed as a result of the above code example.



![](Filtering_images/Filtering_img2.png)



### Excel styled menu

You can enable the Excel like filter menu by setting the FilterType as 'excel' of the FilterSettings property. The Filter menu is displayed after clicking the filter icon in the column headers. 

The filter menu contains options such as Sorting, Clear filter, submenu for the advanced filter options, 

#### Checkbox list

The Checkbox list is available in the menu that contains the possible filter value for the column. It shows the list of possible filter values with the checkbox. The filter value can be selected by clicking the checkbox corresponding to that value. By clicking the Ok button, the column is filtered based on the values checked in the checkbox list. The SelectAll checkbox is also present in the checkbox list that allows either select or deselect all the checkboxes.

![](Filtering_images/Filtering_img3.png)



A Search box is available at the top of the check box list that is used to search the possible filter choices. The number of possible filter choices are restricted by the setting the MaxFilterChoices property of the FilterSettings. 

#### Advanced Filter

The Submenu items in the filter menu provide the advanced filtering options for end users. When selecting a sub menu item, a separate dialog box opens and displays an advanced filter drop-down that lists the available filter operators for the respective filtering column. The filtering is performed by clicking the Ok button.



![](Filtering_images/Filtering_img4.png)



![](Filtering_images/Filtering_img5.png)







{% highlight C# %}



using MVCSampleBrowser.Models;

using System;

using System.Collections.Generic;

using System.Linq;

using System.Web;

using System.Web.Mvc;



namespace MVCSampleBrowser.Controllers

{

    public partial class GridController : Controller

    {

        //

        // GET: /FilteringMenu/



        public ActionResult FilteringMenu()

        {

            var DataSource = OrderRepository.GetAllRecords();

            ViewBag.datasource = DataSource;

            return View();

        }



    }

}

{% endhighlight %}



{% highlight html %}

@(Html.EJ().Grid<EditableOrder>("Grid")

      .Datasource((IEnumerable<object>)ViewBag.datasource)

      .AllowPaging()

.AllowSorting()

.AllowFiltering()

      .FilterSettings(filter => { filter.FilterType(FilterType.Excel). MaxFilterChoices(100).EnableCaseSensitivity(false); })

      .Columns(col =>

       {

         col.Field("OrderID").HeaderText("Order ID").TextAlign(TextAlign.Right).Add();

         col.Field("CustomerID").HeaderText("Customer ID").Add();

         col.Field("OrderDate").HeaderText("Order Date"). Format("{0:MM/dd/yyyy}").Add();

          col.Field("EmployeeID").HeaderText("Employee ID")

             .TextAlign(TextAlign.Right).Add();

          col.Field("ShipCity").HeaderText("Ship City").Add();

          col.Field("Verified").HeaderText("Verified").Add();

        })

    .Render())


{% endhighlight %}




### Filter operators

Grid uses filter operators from ejDataManager, that are used at the time of filtering. Filter operators are used to denote filtering type.

_Table 3 : List of Column type and Filter operators_
{% highlight html %}
<table>
<tr>
<td>
Column type</td><td>
Filter operators</td></tr>
<tr>
<td>
Number</td><td>
ej.FilterOperators.greaterThanej.FilterOperators.greaterThanOrEqualej.FilterOperators.lessThanej.FilterOperators.lessThanOrEqualej.FilterOperators.equal</td></tr>
<tr>
<td>
String</td><td>
ej.FilterOperators.startsWithej.FilterOperators.endsWithej.FilterOperators.containsej.FilterOperators.equalej.FilterOperators.notEqual</td></tr>
<tr>
<td>
Boolean</td><td>
ej.FilterOperators.equalej.FilterOperators.notEqual</td></tr>
<tr>
<td>
Date</td><td>
ej.FilterOperators.greaterThanej.FilterOperators.greaterThanOrEqualej.FilterOperators.lessThanej.FilterOperators.lessThanOrEqualej.FilterOperators.equal</td></tr>
</table>

{% endhighlight %}
### External Filtering

Grid contains an API to do filtering dynamically after Grid initialize, without the use of User Interaction. It is useful to do filtering dynamically.



{% highlight html %}



<div>

    <div class="row">

        <div class="col-md-1">

            Columns

        </div>

        <div class="col-md-1">

            <select id="columns">

                <option value="OrderID">Order ID</option>

                <option value="CustomerID">Customer ID</option>

                <option value="EmployeeID">Employee ID</option>

                <option value="ShipCity">Ship City</option>

                <option value="Verified">Verified</option>

            </select>

        </div>

    </div>

    <br />

    <div class="row">

        <div class="col-md-1">

            Operator

        </div>

        <div class="col-md-1">

            <select id="operator">

                <option value="contains">Contains</option>

                <option value="endswith">Endswith</option>

                <option value="equal">Equal</option>

                <option value="greaterthan">Greaterthan</option>

                <option value="greaterthanorequal">GreaterThanOrEqual</option>

                <option value="lessthan">LessThan</option>

                <option value="lessthanorequal">LessThanOrEqual</option>

                <option value="notequal">NotEqual</option>

                <option value="startswith">StartsWith</option>

            </select>

        </div>

    </div>

    <br />

    <div class="row">

        <div class="col-md-1">

            Value

        </div>

        <div class="col-md-1">

            <input type="text" class="e-ejinputtext" id="value" style="width: 143px;height:26px" />

        </div>

    </div>

    <br />

    <div class="row">

        <div class="col-md-2">

            <input type="button" id="filter" value="filter" />

        </div>

    </div>



</div>




@(Html.EJ().Grid<EditableOrder>("Grid")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

        .AllowPaging()

        .AllowFiltering()

        .FilterSettings(filter => { filter.FilterType(FilterType.Menu); })

    )

    }



@(Html.EJ().DropDownList("operator"))

@(Html.EJ().DropDownList("columns"))

@(Html.EJ().Button("filter"))

{% endhighlight %}

{% highlight js %}

<script>

    $("#filter").ejButton({

        click: function (args) {

            $("#Grid").ejGrid("filterColumn", $("#columns").ejDropDownList("getSelectedValue"), $("#operator").ejDropDownList("getSelectedValue"), $("#value").val(), "and");

        }

    });



</script>
{% endhighlight %}

{% highlight C# %}

namespace MVCSampleBrowser.Controllers

{

    public partial class GridController : Controller

    {

        //

        // GET: /Filtering/



        public ActionResult Filtering()

        {

            var DataSource = OrderRepository.GetAllRecords();

            ViewBag.datasource = DataSource;

            return View();

        }



    }

}

{% endhighlight %}



The following output is displayed as a result of the above code example.



![](Filtering_images/Filtering_img6.png)



