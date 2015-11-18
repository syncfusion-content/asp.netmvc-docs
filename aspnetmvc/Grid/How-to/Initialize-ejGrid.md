---
layout: post
title: Initialize ejGrid | Grid | ASP.NET MVC | Syncfusion
description: initialize ejgrid
platform: ejmvc
control: Grid
documentation: ug
---

# Initialize ejGrid

In this section, you can learn about Grid’s mandatory property to render a simple Grid. To initialize Grid, it needs two important properties. They are columns and its inner property Field. Columns are used to define schema of Grid and Field is mapping a name to the data source.

{% highlight CSHTML %}

@(Html.EJ().Grid<object>("Grid")

.Columns(col =>

{

	col.Field("OrderID).Add();

	col.Field("CustomerID.Add();

	col.Field("EmployeeID").Add();

})

)
{% endhighlight %}
The following output is displayed as a result of the above code example.

![](Initialize-ejGrid_images/Initialize-ejGrid_img1.png)

Empty Grid
{:.caption}
