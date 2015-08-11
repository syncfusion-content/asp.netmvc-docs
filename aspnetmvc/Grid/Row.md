---
layout: post
title: Row
description: row
platform: wpf
control: Grid
documentation: ug
---

# Row

## Details Template

Details Template feature provides a detailed view about additional information of each row. If you want to view the detailed information, you can expand a row. To enable Details Template, used DetailsTemplate property of Grid as follows:


{% highlight js %}
[MVC]

[razor]



<script id="tabGridContents" type="text/x-jsrender">

    <div id="contact{{:EmployeeID}}" style="font-weight:bold; padding:5px;">

        <div id="cont">

            contact:{{:Address}}<br />

            city:{{:City}}<br />

            Country:{{:Country}}<br />

            phone:{{:HomePhone}}<br />

        </div>

    </div>

</script>
{% endhighlight  %}
{% highlight html %}
@(Html.EJ().Grid<EmployeeView>("DetailTemplate")

.Datasource((IEnumerable<object>)ViewBag.datasource)

.AllowPaging()

   .DetailsTemplate("#tabGridContents") // detail template

 )


{% endhighlight  %}
{% highlight c# %}
[controller]



namespace MVCSampleBrowser.Controllers

{

    public partial class GridController : Controller

    {



        public ActionResult DetailTemplate()

        {

            var DataSource = new NorthwindDataContext().EmployeeViews.Take(9).ToList();

            ViewBag.datasource = DataSource;

            return View();

        }

    }

}


{% endhighlight  %}




The following output is displayed as a result of the above code example.



![](Row_images/Row_img1.png)





## Hierarchy



In this section, you can learn how to use the Hierachytree in GridView. The following code example is of HierachyGrid.


{% highlight html %}
[MVC]

[razor]



@(Html.EJ().Grid<EmployeeView>("DetailTemplate")

.Datasource((IEnumerable<object>)ViewBag.datasource)

.DetailsTemplate("#tabGridContents")

.ClientSideEvents(eve => { eve.DetailsDataBound ("detailGridData"); })

)

{% endhighlight  %}
{% highlight js %}

<script src="~/Scripts/jsondata.min.js"></script>

<script id="tabGridContents" type="text/x-jsrender">

<div class="tabcontrol" id="Test">

<div id="detailGrid">

</div>

<label id="employeeDet" style="display: none">{{:EmployeeID}}</label>

</div>

</script>

<script type="text/javascript">

function detailGridData(e) {

var filteredData = e.detailsElement.find("#employeeDet").text();

// the datasource "window.ordersView" is referred from jsondata.min.js

var data = ej.DataManager(window.ordersView).executeLocal(ej.Query().where("EmployeeID", "equal", parseInt(filteredData), true));

e.detailsElement.find("#detailGrid").ejGrid({

dataSource: data,



});



}

</script>


{% endhighlight  %}
{% highlight c# %}
[controller]





namespace MVCSampleBrowser.Controllers

{

public partial class GridController : Controller

{

//

// GET: /DetailTemplate/



public ActionResult DetailTemplate()

{

var DataSource = new NorthwindDataContext().EmployeeViews.Take(9).ToList();

ViewBag.datasource = DataSource;

return View();

}



}

}



{% endhighlight  %}

The following output is displayed as a result of the above code example.



![](Row_images/Row_img2.png)



## Row Template

RowTemplate is used to render your template in every row. It is used to place elements inside Grid rows. This feature makes it easier to customise Grid rows with HTML elements.


{% highlight html %}
[MVC]

[razor]



<script id="templateData" type="text/x-jsrender">

<tr>

<td class="photo">

<img style="width:130px;height: 160px" src="http://js.syncfusion.com/demos/web/themes/images/Employees//{{:EmployeeID}}.png" alt="{{:EmployeeID}}" />

</td>

<td class="details">

<table class="CardTable" cellpadding="3" cellspacing="6">

<colgroup>

<col width="50%">

<col width="50%">

</colgroup>

<tbody>

<tr>

<td class="CardHeader">First Name: </td>

<td style="padding:20px">{{:FirstName}} </td>

</tr>

<tr>



<td class="CardHeader">

Birth Date:

</td>

<td style="padding:20px">

{{:BirthDate.toLocaleDateString()}}

</td>

</tr>

<tr>



<td class="CardHeader">

Hire Date:

</td>

<td style="padding:20px">

{{:HireDate.toLocaleDateString()}}

</td>

</tr>

</tbody>

</table>

</td>

</tr>

</script>

<style>

.CardHeader {

font-weight:bold;

font-size:14px;

padding:20px;

}

</style>



@(Html.EJ().Grid<EmployeeView>("RowTemplate")

.Datasource((IEnumerable<object>)ViewBag.datasource)

.ScrollSettings(scroll => scroll.Height(480).Width(500))

.Columns(col =>

{

col.HeaderText("photo").TextAlign(TextAlign.Center).Width(30).Add();

col.HeaderText("Employee Details").TextAlign(TextAlign.Left).Width(70).Add();

})

.RowTemplate("#templateData")    // row template

)

{% endhighlight  %}
{% highlight c# %}
[controller]





namespace MVCSampleBrowser.Controllers

{

public partial class GridController : Controller

{



public ActionResult RowTemplate()

{

var DataSource = new NorthwindDataContext().EmployeeViews.ToList();

ViewBag.datasource = DataSource;

return View();

}



}

}



{% endhighlight  %}

The following output is displayed as a result of the above code example.



![](Row_images/Row_img3.png)



## Customize Hover and AltRow 

EnableAltRow and EnableRowHover are graphical features in Grid that are used to enable alternate row color in Grid and enable hover effects while hovering over row cells. By default, these two features are enabled in Grid. In this section, you can learn how to cutomize alternative rows color and hover color in the ejGrid controls.



{% highlight html %}

[MVC]

[razor]



@*custom style*@

<style>

.e-grid .e-alt_row {

        background-color: lightgreen !important;

    }



.e-grid .e-hover {

        background: black !important;

    }

</style>



@(Html.EJ().Grid<OrdersView>("FlatGrid")

.Datasource((IEnumerable<object>)ViewBag.datasource)

    .AllowPaging()

    .PageSettings(page => page.PageSize(5))

.EnableAltRow (true)

    .EnableRowHover(true)

    )


{% endhighlight  %}
{% highlight c# %}
[controller]



namespace MVCSampleBrowser.Controllers

{

    public partial class GridController : Controller

    {

        public ActionResult Default()

        {

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            ViewBag.datasource = DataSource;

            return View();

        }

    }

}


{% endhighlight  %}


The following output is displayed as a result of the above code example.



![](Row_images/Row_img4.png)



