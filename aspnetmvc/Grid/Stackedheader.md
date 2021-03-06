---
layout: post
title: Stacked Headers in ASP.NET MVC Grid Control | Syncfusion
description: Learn here about Stacked Headers in Syncfusion Essential ASP.NET MVC Grid Control, its elements, and more.
platform: ejmvc
control: Grid
documentation: ug
---

# Stacked Headers in ASP.NET MVC Grid

The stacked headers helps you to group the logical columns in the Grid. It can be shown by setting the `ShowStackedHeader` as `true` and by defining the `StackedHeaderRows`.

## Adding stacked header columns

To stack the columns in stacked header, you need to define the `Column` property in `StackedHeaderColumns` with field names of visible columns.

{% tabs %}

{% highlight CSHTML %}

@(Html.EJ().Grid<OrdersView>("Grid")
	.Datasource((IEnumerable<object>)ViewBag.datasource)
	 .ShowStackedHeader()
        .StackedHeaderRows(row =>
        {
            row.StackedHeaderColumns(column =>
            {
                column.HeaderText("OrderDetails").Column(col =>
                {
                    col.Add("OrderID");
                    col.Add("OrderDate");
                    col.Add("Freight");
                }).Add();
                column.HeaderText("Ship Details").Column(col =>
                {
                    col.Add("ShipName");
                    col.Add("ShipCity");
                    col.Add("ShipCountry");
                }).Add();
            }).Add();
        })
        .Columns(col =>
        {
            col.Field("OrderID").HeaderText("Order ID").Width(80).Add();
            col.Field("OrderDate").HeaderText("Order Date").Width(80).Format("{0:MM/dd/yyyy}").TextAlign(TextAlign.Right).Add();
            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
            col.Field("ShipName").HeaderText("Ship Name").Width(110).Add();
            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
            col.Field("ShipCountry").HeaderText("Ship Country").Width(110).Add();
        }))


{% endhighlight %}
{% highlight C# %}

namespace SyncfusionMvcApplication3.Controllers

{
    public class HomeController : Controller
    {
        public ActionResult Index()
        {
            var DataSource = new NorthwindDataContext().OrdersViews.ToList();
            ViewBag.datasource = DataSource;
            return View();

        }
    }
}


{% endhighlight  %}
{% endtabs %} 


![ASP.NET MVC Grid stacked header](Stackedheader_images/Stackedheader_img1.png)
