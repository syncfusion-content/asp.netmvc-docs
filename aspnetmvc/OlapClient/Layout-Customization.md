---
layout: post
title: Layout Customization | OLAPClient | ASP.NET MVC | Syncfusion
description: layout customization
platform: ejmvc
control: OLAPClient
documentation: ug
---

# Layout Customization

## Display View

### Tab View

In Tab View representation, both Grid and Chart will be displayed in a separate tab.  This could be set using the `ControlPlacement` property under the `DisplaySettings` option.  By default, **Tab** value is set.

{% highlight C# %}

    @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title( "OLAP Browser").DisplaySettings(displaySettings=>displaySettings.ControlPlacement( OlapClientControlPlacement.Tab))

{% endhighlight %}

![](Layout-Customization_images/tabview.png)

### Tile View

In Tile View representation, both Grid and Chart will be displayed one over the other, in the same layout.  Tile view can be set by using the `ControlPlacement` property under the `DisplaySettings` option.

{% highlight C# %}

    @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title("OLAP Browser").DisplaySettings(displaySettings=>displaySettings.ControlPlacement(OlapClientControlPlacement.Tile))

{% endhighlight %}

![](Layout-Customization_images/tileview.png)

## Default View

### Grid View

To display Grid control by default, set `DefaultView` property under `DisplaySettings` option to **Grid**, which is the default value of the property.

{% highlight C# %}

    @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title( "OLAP Browser").DisplaySettings(displaySettings=>displaySettings.DefaultView( OlapClientDefaultView.Grid))

{% endhighlight %}

![](Layout-Customization_images/gridview.png)

### Chart View

To display Chart control by default, set the property `DefaultView` property to **Chart**.

{% highlight C# %}

    @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title( "OLAP Browser").DisplaySettings(displaySettings=>displaySettings.DefaultView( OlapClientDefaultView.Chart))

{% endhighlight %}

![](Layout-Customization_images/chartview.png)

## Display Mode

### Grid Only

After setting the `Mode` property under `DisplaySettings` option to **GridOnly**, the Chart is hidden and the data is displayed only in the Grid.

{% highlight C# %}

   @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title( "OLAP Browser").DisplaySettings(displaySettings=>displaySettings.Mode( OlapClientDisplayMode.GridOnly))

{% endhighlight %}

![](Layout-Customization_images/gridonlyview.png)

### Chart Only

After setting the `Mode` property under `DisplaySettings` option to **ChartOnly**, the Grid is hidden and data is displayed only in the Chart.

{% highlight C# %}

   @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title( "OLAP Browser").DisplaySettings(displaySettings=>displaySettings.Mode( OlapClientDisplayMode.ChartOnly))

{% endhighlight %}

![](Layout-Customization_images/chartonlyview.png)

### Both Chart and Grid

After setting the `Mode` property under `DisplaySettings` option to **ChartAndGrid**, data is displayed in both Grid and Chart.  This is the default value of the property.

{% highlight C# %}

   @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title( "OLAP Browser").DisplaySettings(displaySettings=>displaySettings.Mode( OlapClientDisplayMode.ChartAndGrid))

{% endhighlight %}

![](Layout-Customization_images/chartandgridview.png)

## Toggle Panel

Toggle panel option lets the user to toggle the visibility of Axis Element Builder and Cube Dimension Browser panels in OlapClient with a use of a button. The button could be added to the control by using the `EnableTogglePanel` property under `DisplaySettings` option.  This property is disabled by default.

{% highlight C# %}

  @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title("OLAP Browser").DisplaySettings(displaySettings=>displaySettings.EnableTogglePanel(true))

{% endhighlight %}

![](Layout-Customization_images/toggleview.png)

## Maximized/Full Screen View

Full screen view helps to visualize the PivotGrid and OlapChart controls inside OlapClient precisely according to the browser window size.  By selecting full screen icon in the toolbar, PivotGrid/OlapChart is maximized depending on the selected tab.  Drilldown action can also be performed in both PivotGrid and OlapChart in the maximized view.  This option is enabled by setting the `EnableFullScreen` property under `DisplaySettings` option to true.  The value is false by default.

{% highlight C# %}

  @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title("OLAP Browser").DisplaySettings(displaySettings=>displaySettings.EnableFullScreen(true))

{% endhighlight %}

![](Layout-Customization_images/maximizeicon.png)

The following screenshot shows the maximized view of PivotGrid.

![](Layout-Customization_images/maximizedview.png)

## Grid Layout

PivotGrid inside OlapClient control can be rendered in any of the following layouts.

* Normal
* NormalTopSummary
* NoSummaries
* ExcelLikeLayout

The layout is set using the `GridLayout` property. By default, normal layout is set.

{% highlight C# %}

  @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title("OLAP Browser").GridLayout(PivotGridLayout.NoSummaries)

{% endhighlight %}

![](Layout-Customization_images/gridlayout.png)

## Chart Types

While loading the OlapClient initially, the OlapChart widget can be rendered in any one of the available chart types using the `ChartType` property.

{% highlight C# %}

  @Html.EJ().Olap().OlapClient("OlapClient1").Url(Url.Content("~/OlapClient")).Title("OLAP Browser").ChartType(OlapChartType.Column)

{% endhighlight %}

The `ChartType` property takes Column Chart by default. The types available are Column, Stacking Column, Bar, Stacking Bar, Line, Spline, Step Line, Area, Spline Area, Step Area, Stacking Area, Pie, Funnel and Pyramid.

The Chart Type can also be changed dynamically through the toolbar icon.

![](Layout-Customization_images/charttypes.png)

![](Layout-Customization_images/linechart.png) 




