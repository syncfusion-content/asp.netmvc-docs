---
layout: post
title: State Persistence | Grid | ASP.NET MVC | Syncfusion
description: How to persist grid state across page refresh
platform: ejmvc
control: Grid
documentation: ug
---

# State Persistence 

State persistence is to maintain the grid state in browser's [local storage](https://www.w3schools.com/html/html5_webstorage.asp) even if browser refreshes or move to the next page. State persistence stores grid's model object in local storage while defining the `enablePersistence` as true. 

I>  The [localStorage](https://www.w3schools.com/html/html5_webstorage.asp) is not supported below IE9 then grid state persistence technique is fallback to [cookie](https://www.w3schools.com/js/js_cookies.asp).

## List of properties are not persisted by default

The following properties are not included while maintaining the grid state in local storage to keep localStorage compact.

* Query
* isEdit
* toolbarClick
* queryCellInfo
* mergeCellInfo
* currentViewData
* enableAltRow
* enableRTL 
* contextClick 
* contextOpen
* rowDataBound
* rowTemplate
* detailsDataBound
* detailsTemplate
* childGrid 
* summaryRows 
* toolbarSettings
* editSettings
* allowMultiSorting 
* enableAutoSaveOnSelectionChange 
* locale 
* allowScrolling 
* allowCellMerging
* allowTextWrap 
* cssClass 
* dataSource 
* groupSettings.enableDropAreaAnimation 
* enableRowHover 
* showSummary 
* allowGrouping
* enableHeaderHover 
* allowKeyboardNavigation 
* scrollSettings.frozenRows 
* scrollSettings.frozenColumns 
* enableTouch 
* editSettings.rowPosition 
* editSettings.showAddNewRow 
* contextMenuSettings.enableContextMenu

I> The given excluded properties can be included in persist state using the `_ignoreOnPersist` in grid prototype. 



## Accessing currently stored state

The persisted state can be accessed through local storage using the corresponding key name. Key name is the combination of plugin name and control id.

{% highlight js %}
var gridStateString = window.localStorage.ejGridGrid; // grid state as string

var gridStateObject = JSON.parse(window.localStorage.ejGridGrid);//grid state as object

{% endhighlight %}


I> In the above example, the "ejGrid" is plugin name and "Grid" is control id.        

