---
layout: post
title: Paging
description: paging
platform: ejmvc
control: Grid
documentation: ug
---

# Paging

Paging is a powerful technique in Grid that is used to navigate from one page to another. Using this pager, you can implement load on demand concept that loads only required data to Grid. To enable paging in Grid set AllowPaging as True at Grid Initialize.

## Default Paging

When the AllowPaging property is set as True, the properties in the pagesettings take the following default values.

* PageSize-12
* PageCount – 8
* CurrentPage-1

The following code example is for the Grid with default options.



{% highlight js %}


@(Html.EJ().Grid<OrdersView>("Grid")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

.AllowPaging()        

        )



{% endhighlight  %}
{% highlight c# %}



namespace MVCSampleBrowser.Controllers

{

    public partial class GridController : Controller

    {

        public ActionResult Paging()

        {

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            ViewBag.datasource = DataSource;

            return View();

        }

     }

}






{% endhighlight  %}
The following output is displayed as a result of the above code example.

![](Paging_images/Paging_img1.png)

_Figure : Paging_

## External Paging

In this section, you can see how to use external paging. The following code example is for external paging.

{% highlight js %}

@(Html.EJ().Grid<OrdersView>("Paging")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

        .AllowPaging()

       )



    <div class="row">

        <div class="col-md-1"></div>

        <div class="col-md-1">

            goto

        </div>

        <div class="col-md-2">

            @(Html.EJ().NumericTextbox("goto")

            .Value("1")

            .MinValue(1)

            .MaxValue(10)

            .ClientSideEvents(eve => { eve.Change("pageChange"); })

            )

        </div>

        </div>
{% endhighlight  %}

{% highlight js %}
<script type="text/javascript">

    function pageChange(args) {

        var gridobj = $("#Paging").data("ejGrid");

        gridobj.goToPage(args.value);

    }

</script>   


{% endhighlight  %}

{% highlight c# %}

namespace MVCSampleBrowser.Controllers

{

    public partial class GridController : Controller

    {

        public ActionResult PagingAPI()

        {

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            ViewBag.datasource = DataSource;

            return View();

        }

    }

}    

{% endhighlight  %}



The following output is displayed as a result of the above code example.



![](Paging_images/Paging_img2.png)

_Figure : External Paging_

## Pager Templates

Pager Templates feature provide support to render a specific custom template to a Grid pager using EnableTemplates and Template properties of PageSettings. ShowDefaults property is used to show/hide default pager for Grid.

{% highlight js %}

@(Html.EJ().Grid<OrdersView>("Paging")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

        .PageSettings(page=>page.EnableTemplates().Template("#template"))

        .Columns(col =>

        {

            col.Field("OrderID").HeaderText("Order ID"). TextAlign(TextAlign.Right). Add();

            col.Field("CustomerID").HeaderText("Customer ID"). Add();

            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Add();

            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right). Add();

            col.Field("ShipCity").HeaderText("Ship City").Add();

            col.Field("ShipCountry").HeaderText("Ship Country").Add();

        })

    ) 

{% endhighlight  %}

{% highlight js %}

 <script type="text/x-jsrender" id="template">

        <a id="prev" value="Prev">Prev</a>

        <input type="text"/>

        <input type="button" value="Go"/>

        <a>Next</a>

   </script>   
{% endhighlight  %}
{% highlight c# %}
 



public partial class GridController : Controller

    {

        //

        // GET: /PrintGrid/



        public ActionResult PrintGrid()

        {

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            ViewBag.datasource = DataSource;

            return View();

        }



    }





{% endhighlight  %}

![](Paging_images/Paging_img3.png)

_Figure : Pager Template_

## Methods

The following are the public methods of pager.

* goto
* refreshPager

In this section, you can see how to use paging methods in Grid control. The following code example is for paging methods. 


{% highlight js %}

 @(Html.EJ().Grid<OrdersView>("Paging")

     .Datasource((IEnumerable<object>)ViewBag.datasource)

     .AllowPaging()

     .PageSettings(page => page.PageSize(5))



)

<div class="row">

    <br />

    <div class="col-md-1"></div>

    <div class="col-md-1">

        goto

    </div>

    <div class="col-md-2">

        @(Html.EJ().NumericTextbox("goto")

            .Value("1")

            .MinValue(1)

            .ClientSideEvents(eve => { eve.Change("pageChange"); })

            )

    </div>

    <div class="col-md-1">

        Page Count

    </div>

    <div class="col-md-2">

        @(Html.EJ().NumericTextbox("pageCount")

            .Value("1")

            .MinValue(1)

            .MaxValue(10)

            .ClientSideEvents(eve => { eve.Change("pageCountChange"); })

            )

    </div>

    <div class="col-md-1">

        pageSize

    </div>

    <div class="col-md-1">

        @(Html.EJ().NumericTextbox("pageSize")

            .Value("12")

            .MinValue(1)

            .MaxValue(10)

            .ClientSideEvents(eve => { eve.Change("pageSizeChange"); })

            )

    </div>

</div>

<script type="text/javascript">

    function pageChange(args) {

        $("#Paging").ejGrid("getPager").ejPager("goToPage", args.value);

    }

    function pageCountChange(args) {

        $("#Paging").ejGrid({ "pageSettings": { pageCount: parseInt(args.value) } });

    }

    function pageSizeChange(args) {

        $("#Paging").ejGrid({ "pageSettings": { pageSize: parseInt(args.value) } });

    }

</script>


{% endhighlight  %}
{% highlight c# %}
  

namespace MVCSampleBrowser.Controllers

{

    public partial class GridController : Controller

    {

        public ActionResult PagingAPI()

        {

       var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            ViewBag.datasource = DataSource;

            return View();

        }

    }

}



{% endhighlight  %}

The following output is displayed as a result of the above code example.



![](Paging_images/Paging_img4.png)

_Figure : Paging Methods_


## Localization for paging

Localization is the process of customizing the user interface (UI) as locale-specific, inorder to display regional data. With this feature, data can be displayed in a language and culture specific to a particular country or region. The JavaScript Grid control provides inherent support to localize its UI.

The following UIs are provided to localize based on culture. The default English localization UIs are as follows.

{% highlight js %}

pagerInfo: "{0} of {1} pages ({2} items)",

firstPageTooltip: "Go to first page",

lastPageTooltip: "Go to last page",

nextPageTooltip: "Go to next page",

previousPageTooltip: "Go to previous page ",

nextPagerTooltip: "Go to next pager",

previousPagerTooltip: "Go to previous pager "

{% endhighlight  %}

In this section, you can see how to use Globilzation in Grid pager. The following code example is for pager localization in German and Spanish. 



{% highlight js %}

  
@(Html.EJ().Grid<OrdersView>("Localization")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

        .AllowPaging()

        .PageSettings(page => page.PageSize(5))

        .Locale("de-DE")

        )



    <div id="ddl">

        <ul>

            <li>English</li>

            <li>German</li>

            <li>Spanish</li>

        </ul>

    </div>

    <div class="row">

        <div class="col-md-3">

            Selection Type

        </div>

        <div class="col-md-3">

            @(Html.EJ().DropDownList("language")

                .TargetID("ddl")

                .SelectedItemIndex(1)

                .ClientSideEvents(eve => eve.Change("onChange"))

                .Width("120px")

                )

        </div>

    </div>

    <script type="text/javascript">

        $(function () {

            $("#sampleProperties").ejPropertiesPanel();

        });

        function onChange(args) {

            if (args.itemId == 0)

                $("#Localization").ejGrid("model.locale", "en-US");

            else if (args.itemId == 1)

                $("#Localization").ejGrid("model.locale", "de-DE");

            else

                $("#Localization").ejGrid("model.locale", "es-ES");

        }

        ej.Grid.locale["es-ES"] = {



        };

ej.Pager.locale["es-ES"] = {

            pagerInfo: "{0} de {1} páginas ({2} artículos)",

            firstPageTooltip: "Ir a la primera página",

            lastPageTooltip: "Ir a la última páginas",

            nextPageTooltip: "Ir a la página siguiente",

            previousPageTooltip: "Ir a la página anterior",

            nextPagerTooltip: "Ir a la siguiente pager",

            previousPagerTooltip: "Ir al localizador anterior"

        };

        ej.Grid.locale["de-DE"] = {



        };

        ej.Pager.locale["de-DE"] = {

            pagerInfo: "{0} von {1} Seiten ({2} Beiträge)",

            firstPageTooltip: "Zur ersten Seite",

            lastPageTooltip: "gehen Zur letZten Seite",

            nextPageTooltip: "Zur nächsten Seite",

            previousPageTooltip: "Zuruck Zur letZten Seite",

            nextPagerTooltip: "genhen Sie Zum nächsten pager ",

            previousPagerTooltip: "Zur vorherigen pager"

        };

    </script>


{% endhighlight  %}
{% highlight c# %}

namespace MVCSampleBrowser.Controllers

{

    public partial class GridController : Controller

    {

        //

        // GET: /PagingAPI/



        public ActionResult PagingAPI()

        {

            var DataSource = new NorthwindDataContext().OrdersViews.ToList();

            ViewBag.datasource = DataSource;

            return View();

        }

    }

}

{% endhighlight  %}



The following output is displayed as a result of the above code example.



![](Paging_images/Paging_img5.png)

_Figure : Pager Localization_

