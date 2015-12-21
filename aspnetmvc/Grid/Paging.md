---
layout: post
title: Paging | Grid | ASP.NET MVC | Syncfusion
description: paging
platform: ejmvc
control: Grid
documentation: ug
---
# Paging

 You can display the grid records in paged view, by setting [`allowPaging`](http://help.syncfusion.com/js/api/ejgrid#members:allowpaging "allowPaging") property as `true`.

The code snippet to enable paging is follows.

{% tabs %}
{% highlight CSHTML %}

       @(Html.EJ().Grid<Object>("Paging")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();
            }) )
{% endhighlight  %}
 
{% highlight C# %}

     namespace MVCSampleBrowser.Controllers
    {
       public class GridController : Controller
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
 {% endtabs %} 
 
 The following output is displayed as a result of the above code example.
 
 ![](paging_images/Paging_img1.png)

## Pager with query string


You can pass the current page information as a query string while navigating to other page. To enable query string, set the [`enableQueryString`](http://help.syncfusion.com/js/api/ejgrid#members:pagesettings-enablequerystring "enableQueryString") property of [`pageSettings`](http://help.syncfusion.com/js/api/ejgrid#members:pagesettings "pageSettings") as `true`.

The following code example describes the above behavior.

{% tabs %}
{% highlight CSHTML %}

     @(Html.EJ().Grid<Object>("Paging")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .PageSettings(Page => { Page.EnableQueryString(true); })
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();
            }) )
            
 {% endhighlight  %}
 
 {% highlight C# %} 
        
             namespace MVCSampleBrowser.Controllers
               {
                public class GridController : Controller
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
 {% endtabs %} 

The following output is displayed as a result of the above code example.

 ![](paging_images/PagPaging_img2.png)


## Pager template

Apart from default pager, there is an option to render a specific custom template in a grid pager. To render template in pager, set [`enableTemplates`](http://help.syncfusion.com/js/api/ejgrid#members:pagesettings-enabletemplates "enableTemplates") as true and [`template`](http://help.syncfusion.com/js/api/ejgrid#members:pagesettings-template "template") properties of [`pageSettings`](http://help.syncfusion.com/js/api/ejgrid#members:pagesettings "pageSettings").

 Prevent to show the default pager while enabling the pager [`template`](http://help.syncfusion.com/js/api/ejgrid#members:pagesettings-template "template") by setting [`showDefaults`](http://help.syncfusion.com/js/api/ejgrid#members:pagesettings-showdefaults "showDefaults") property of [`pageSettings`](http://help.syncfusion.com/js/api/ejgrid#members:pagesettings "pageSettings") as `false`.

 N> It's a standard way to enclose the [`template`](http://help.syncfusion.com/js/api/ejgrid#members:pagesettings-template "template") within the `script` tag with `type` as "text/x-jsrender".

The following code example describes the above behavior.

{% tabs %} 
{% highlight html %}

         <script id="template" type="text/x-jsrender">
            <input id="currentPage" type="text" style="text-align: center; width: 32px; height: 21px; background: white;" value="1" />
            <label>of 200</label>
            <button id="btn">Go to</button>
         </script>
          <script>
            function create(args) {
                        $("#btn").ejButton({
                       click : "btnClick"
                       });
                     }

             function btnClick(args) {
                     var val = $("#currentPage").val();
                     var gridObj = $("#Grid").data("ejGrid");
                      gridObj.goToPage(args.val);
                     }
           </script>

{% endhighlight  %}
{% highlight css %}

     .e-grid .e-pager .e-pagercontainer {
	       border-width: 0px;
	       overflow: visible;
         }
         
{% endhighlight  %}      
{% tabs %} 
{% highlight CSHTML %}

        @(Html.EJ().Grid<OrdersView>("Paging")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging() 
            .PageSettings(Page => { Page.EnableTemplates().Template("#template").ShowDefaults(false); })
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Add();
            }).ClientSideEvents(e=>e.Create("create")) 
            )
         
{% endhighlight  %}

{% highlight C# %}

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
 {% endtabs %}  
 
 The following output is displayed as a result of the above code example.

![](paging_images/Paging_img3.png)

 