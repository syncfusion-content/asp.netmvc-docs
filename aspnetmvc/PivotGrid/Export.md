---
layout: post
title: Export | PivotGrid | ASP.NET MVC | Syncfusion
description: export
platform: ejmvc
control: PivotGrid
documentation: ug
---

# Export

N> This feature is applicable only for OLAP datasource.

The PivotGrid is exported from cell mode to a worksheet of an Excel Workbook. The Excel Workbook is saved from the browser to the local disk drive.

The following code example illustrates how to save the document to Excel via service.

For PivotGrid

{% tabs %}
 
{% highlight C# %} 

public void ExportOptions(Stream stream)

{

	PivotGrid pivotGridHelper = new PivotGrid();

	OlapDataManager DataManager=new OlapDataManager(connectionString);

	pivotGridHelper.ExportToExcel(DataManager, newStreamReader(stream).ReadToEnd(), "Sample.xls",HttpContext.Current.Response);

}

{% endhighlight %}


{% highlight CSHTML %}


@section ScriptSection{

<script type="text/javascript">

        function btnClick(e) {

         pgridObj = $('#PivotGrid').data("ejPivotGrid");

         pgridObj.exportToExcel();

        }

</script>

}



@section ControlsSection{

@Html.EJ().Button("Button1").Size(ButtonSize.Normal).Text("Export Grid").ShowRoundedCorner(true).ClientSideEvents(events=>events.Click("btnClick"))

@Html.EJ().Pivot().PivotGrid("PivotGrid1").Url("../wcf/PivotGridService.svc") 

}

{% endhighlight %}
{% endtabs %} 
![](Export_images/Export_img1.png)



