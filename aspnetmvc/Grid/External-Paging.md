---
layout: post
title: External-Paging
description: external paging
platform: ejmvc
control: Grid
documentation: ug
---

## External Paging

In this section, you can see how to use external paging. The following code example is for external paging.





[MVC]

[razor]



@(Html.EJ().Grid<OrdersView>("Paging")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

        .AllowPaging()

       )



    &lt;div class="row"&gt;

        &lt;div class="col-md-1"&gt;&lt;/div&gt;

        &lt;div class="col-md-1"&gt;

            goto

        &lt;/div&gt;

        &lt;div class="col-md-2"&gt;

            @(Html.EJ().NumericTextbox("goto")

            .Value("1")

            .MinValue(1)

            .MaxValue(10)

            .ClientSideEvents(eve => { eve.Change("pageChange"); })

            )

        &lt;/div&gt;

        &lt;/div&gt;

&lt;script type="text/javascript"&gt;

    function pageChange(args) {

        var gridobj = $("#Paging").data("ejGrid");

        gridobj.goToPage(args.value);

    }

&lt;/script&gt;   





[controller]

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





The following output is displayed as a result of the above code example.



{ ![](External-Paging_images/External-Paging_img1.png) | markdownify }
{:.image }


### Pager Templates

Pager Templates feature provide support to render a specific custom template to a Grid pager using EnableTemplates and Template properties of PageSettings. ShowDefaults property is used to show/hide default pager for Grid.



[MVC]

[razor]



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



 &lt;script type="text/x-jsrender" id="template"&gt;

        <a id="prev" value="Prev">Prev</a>

        &lt;input type="text"/&gt;

        &lt;input type="button" value="Go"/&gt;

        <a>Next</a>

   &lt;/script&gt;   

 [Controller]



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







{ ![](External-Paging_images/External-Paging_img2.png) | markdownify }
{:.image }


### Methods

The following are the public methods of pager.

* goto
* refreshPager

In this section, you can see how to use paging methods in Grid control. The following code example is for paging methods. 



[MVC]



[razor]





 @(Html.EJ().Grid<OrdersView>("Paging")

     .Datasource((IEnumerable<object>)ViewBag.datasource)

     .AllowPaging()

     .PageSettings(page => page.PageSize(5))



)

&lt;div class="row"&gt;

    &lt;br /&gt;

    &lt;div class="col-md-1"&gt;&lt;/div&gt;

    &lt;div class="col-md-1"&gt;

        goto

    &lt;/div&gt;

    &lt;div class="col-md-2"&gt;

        @(Html.EJ().NumericTextbox("goto")

            .Value("1")

            .MinValue(1)

            .ClientSideEvents(eve => { eve.Change("pageChange"); })

            )

    &lt;/div&gt;

    &lt;div class="col-md-1"&gt;

        Page Count

    &lt;/div&gt;

    &lt;div class="col-md-2"&gt;

        @(Html.EJ().NumericTextbox("pageCount")

            .Value("1")

            .MinValue(1)

            .MaxValue(10)

            .ClientSideEvents(eve => { eve.Change("pageCountChange"); })

            )

    &lt;/div&gt;

    &lt;div class="col-md-1"&gt;

        pageSize

    &lt;/div&gt;

    &lt;div class="col-md-1"&gt;

        @(Html.EJ().NumericTextbox("pageSize")

            .Value("12")

            .MinValue(1)

            .MaxValue(10)

            .ClientSideEvents(eve => { eve.Change("pageSizeChange"); })

            )

    &lt;/div&gt;

&lt;/div&gt;



&lt;script type="text/javascript"&gt;

    function pageChange(args) {

        $("#Paging").ejGrid("getPager").ejPager("goToPage", args.value);

    }

    function pageCountChange(args) {

        $("#Paging").ejGrid({ "pageSettings": { pageCount: parseInt(args.value) } });

    }

    function pageSizeChange(args) {

        $("#Paging").ejGrid({ "pageSettings": { pageSize: parseInt(args.value) } });

    }

&lt;/script&gt;



  [controller]

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





The following output is displayed as a result of the above code example.



{ ![](External-Paging_images/External-Paging_img3.png) | markdownify }
{:.image }


### Localization for paging

Localization is the process of customizing the user interface (UI) as locale-specific, inorder to display regional data. With this feature, data can be displayed in a language and culture specific to a particular country or region. The JavaScript Grid control provides inherent support to localize its UI.

The following UIs are provided to localize based on culture. The default English localization UIs are as follows.



pagerInfo: "{0} of {1} pages ({2} items)",

firstPageTooltip: "Go to first page",

lastPageTooltip: "Go to last page",

nextPageTooltip: "Go to next page",

previousPageTooltip: "Go to previous page ",

nextPagerTooltip: "Go to next pager",

previousPagerTooltip: "Go to previous pager "



In this section, you can see how to use Globilzation in Grid pager. The following code example is for pager localization in German and Spanish. 





  [MVC]

[razor]



@(Html.EJ().Grid<OrdersView>("Localization")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

        .AllowPaging()

        .PageSettings(page => page.PageSize(5))

        .Locale("de-DE")

        )



    &lt;div id="ddl"&gt;

        &lt;ul&gt;

            <li>English</li>

            <li>German</li>

            <li>Spanish</li>

        &lt;/ul&gt;

    &lt;/div&gt;

    &lt;div class="row"&gt;

        &lt;div class="col-md-3"&gt;

            Selection Type

        &lt;/div&gt;

        &lt;div class="col-md-3"&gt;

            @(Html.EJ().DropDownList("language")

                .TargetID("ddl")

                .SelectedItemIndex(1)

                .ClientSideEvents(eve => eve.Change("onChange"))

                .Width("120px")

                )

        &lt;/div&gt;

    &lt;/div&gt;



    &lt;script type="text/javascript"&gt;

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

    &lt;/script&gt;



[controller]



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





The following output is displayed as a result of the above code example.



{ ![](External-Paging_images/External-Paging_img4.png) | markdownify }
{:.image }


