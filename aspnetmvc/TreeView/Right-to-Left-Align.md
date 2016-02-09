---
title: Right to Left Align  | TreeView | ASP.NET MVC | Syncfusion
description: Right to Left Align  
platform: ejmvc
control: TreeView
documentation: UG
keywords: TreeView,  Syncfusion, EJ MVC TreeView, UG Document, Right to Left Align 
---

# Right to Left Align

TreeView supports right to left align and it can be applied by specifying ‘**EnableRTL’** as true.
    
    
    
    {% highlight razor %}
    
    @(Html.EJ().TreeView("treeViewDrag")
        .TreeViewFields(field =>
            field.Datasource((IEnumerable<LoadData>)ViewBag.datasource)
            .Id("Id")
            .ParentId("Parent")
            .Text("Text")
        )
        .EnableRTL(true)
    )
    
    {% endhighlight %}
    
    
