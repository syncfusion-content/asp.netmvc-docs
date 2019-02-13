---
layout: post
title: Layout Customization | PivotClient | ASP.NET MVC | Syncfusion
description: layout customization
platform: ejmvc
control: PivotClient
documentation: ug
---

# Layout Customization

## Size

Allows you to render PivotClient in different sizes. You can set height and width under `size` property.

### Set size in Pixels

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).size(siz => { siz.Height("685px"); siz.Width("1000px"); })

{% endhighlight %}

PivotClient with decreased size from default size.

![ASP NET MVC pivot client control with reduced size](Layout-Customization_images/small-size.png)

### Set size in percentage

You can set the PivotClient size in percentage also.

N> Size of the parent container should be set in Pixels.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).size(siz => { siz.Height("80%"); siz.Width("50%"); })

{% endhighlight %}

## Control Placement

### Tab View

In Tab view representation, both Grid and Chart will be displayed in separate tabs.  This could be set by using the `ControlPlacement` property under the `DisplaySettings` option.  By default, **Tab** value is set.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).DisplaySettings(displaySettings=>displaySettings.ControlPlacement( PivotClientControlPlacement.Tab))

{% endhighlight %}

![ASP NET MVC pivot client control with tab view](Layout-Customization_images/tabview.png)

### Tile View

In Tile View representation, both Grid and Chart will be displayed one above the other, in the same layout. Tile view can be set by using the `ControlPlacement` property under the `DisplaySettings` option.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).DisplaySettings(displaySettings=>displaySettings.ControlPlacement(PivotClientControlPlacement.Tile))

{% endhighlight %}

![ASP NET MVC pivot client control with tile view](Layout-Customization_images/tileview.png)

## Default View

### Grid View

To display Grid control by default, set `DefaultView` property under `DisplaySettings` option to **Grid**, which is the default value of the property.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).DisplaySettings(displaySettings=>displaySettings.DefaultView( PivotClientDefaultView.Grid))

{% endhighlight %}

![ASP NET MVC pivot client control with grid view as default](Layout-Customization_images/gridview.png)

### Chart View

To display Chart control by default, set the `DefaultView` property to **Chart**.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).DisplaySettings(displaySettings=>displaySettings.DefaultView( PivotClientDefaultView.Chart))

{% endhighlight %}

![ASP NET MVC pivot client control with chart view as default](Layout-Customization_images/chartview.png)

## Display Mode

### Grid Only

By the `Mode` property under `DisplaySettings` option to **GridOnly**, PivotGrid component alone will get rendered and PivotChart will not be rendered.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).DisplaySettings(displaySettings=>displaySettings.Mode( PivotClientDisplayMode.GridOnly))

{% endhighlight %}

![ASP NET MVC pivot client control with grid only view](Layout-Customization_images/gridonlyview.png)

### Chart Only

By the `Mode` property under `DisplaySettings` option to **ChartOnly**, PivotChart component alone will get rendered and PivotGrid will not be rendered.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).DisplaySettings(displaySettings=>displaySettings.Mode( PivotClientDisplayMode.ChartOnly))

{% endhighlight %}

![ASP NET MVC pivot client control with chart only view](Layout-Customization_images/chartonlyview.png)

### Both Chart and Grid

By the `Mode` property under `DisplaySettings` option to **ChartAndGrid**, data is displayed in both Grid and Chart.  This is the default value of the property.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).DisplaySettings(displaySettings=>displaySettings.Mode( PivotClientDisplayMode.ChartAndGrid))

{% endhighlight %}

![ASP NET MVC pivot client control with grid and chart view](Layout-Customization_images/tileview.png)

## Toggle Panel

Toggle panel option lets the user to toggle the visibility of Axis Element Builder and Cube Dimension Browser panels in PivotClient with a use of a button. The button could be added to the control by enabling the `EnableTogglePanel` property under `DisplaySettings` option.  This property is disabled by default.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).DisplaySettings(displaySettings=>displaySettings.EnableTogglePanel(true))

{% endhighlight %}

![ASP NET MVC pivot client control with toggle panel](Layout-Customization_images/toggleview.png)

## Collapse Toggle Panel By Default

Allows the user to hide “Cube Browser” and “Axis Element Builder” panels while initiating the widget. You can enable this option in PivotClient by setting the `CollapseCubeBrowserByDefault` property to true.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).CollapseCubeBrowserByDefault(true)

{% endhighlight %}

![ASP NET MVC pivot client control with toggle panel by default](Layout-Customization_images/collapse-cube-browser-by-default.png)

## Maximized/Full Screen View

Full screen view helps to visualize the PivotGrid and PivotChart controls inside PivotClient precisely according to the browser window size.  By selecting full screen icon in the toolbar, the control which is in the view gets maximized.  Drilldown action can also be performed in both PivotGrid and PivotChart in the maximized view.  This option is enabled by setting the `EnableFullScreen` property under `DisplaySettings` option to true.  The value is false by default.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).DisplaySettings(displaySettings=>displaySettings.EnableFullScreen(true))

{% endhighlight %}

![Full screen icon in ASP NET MVC pivot client control](Layout-Customization_images/maximizeicon.png)

The following screenshot shows the maximized view of PivotGrid.

![Full screen view of ASP NET MVC pivot client control](Layout-Customization_images/maximizedview.png)


## Chart Types

While loading the PivotClient initially, the PivotChart widget can be rendered in any one of the available chart types using the `ChartType` property.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).ChartType(PivotChartType.Column)

{% endhighlight %}

The `ChartType` property takes Column Chart by default. The types available are Column, Stacking Column, Bar, Stacking Bar, Line, Spline, Step Line, Area, Spline Area, Step Area, Stacking Area, Pie, Funnel and Pyramid.

The Chart Type can also be changed dynamically through the toolbar icon.

![Chart types in ASP NET MVC pivot client control](Layout-Customization_images/charttypes.png)

![ASP NET MVC pivot client control with line chart type](Layout-Customization_images/linechart.png)

### PivotTreeMap

I> This feature is applicable only for OLAP data source bound from server-side.

You can include the PivotTreeMap component as one of the chart types by setting `EnablePivotTreeMap` property to true.

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1").ClientSideEvents(clientSideEvents => clientSideEvents.Load("onLoad")).DataSource(dataSource => dataSource.Rows(rows => { rows.FieldName("Country").FieldCaption("Country").Add(); }).Columns(columns => { columns.FieldName("Product").FieldCaption("Product").Add(); }).Values(values => { values.FieldName("Amount").Format("currency").Add(); })).EnablePivotTreeMap(true)

{% endhighlight %}

![Treemap icon in chart types panel of ASP NET MVC pivot client control](Layout-Customization_images/TreeMap1.png)

![Treemap in ASP NET MVC pivot client control](Layout-Customization_images/TreeMap2.png)


## Report Toolbar

You can customize the display of toolbar by enabling/disabling the visibility of each of the icons. This can be achieved by setting the properties under `ToolbarIconSettings` option to false. The values are true by default.​​​

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotClient("PivotClient1”).ToolbarIconSettings(toolbaricon => { toolbaricon.EnableAddReport(false).EnableNewReport(false).EnableRemoveReport(false); })

{% endhighlight %}

![Report toolbar of ASP NET MVC pivot client control](Layout-Customization_images/toolbarIconSettings1.png)

The following screenshot shows after disabling the toolbar icons.

![Hiding report icons from toolbar of ASP NET MVC pivot client control](Layout-Customization_images/toolbarIconSettings2.png)
