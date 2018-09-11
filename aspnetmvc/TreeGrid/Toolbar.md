---
layout: post
title: Toolbar | TreeGrid | ASP.NET MVC | Syncfusion
description: toolbar
platform: ejmvc
control: TreeGrid
documentation: ug
---

# Toolbar

In TreeGrid we can show/hide the Toolbar by using `ShowToolbar` property.We can add default toolbar items by `ToolbarItems`. User can also create a custom toolbar items by using `CustomToolbarItems`.

## Default Toolbar Items
Using TreeGrid default toolbar items we can perform below operations.

* **Add**- To add new task.

* **Edit**-To edit a selected task.

* **Delete**- To delete a selected task.
		   
* **Cancel**- To cancel the edited changes in a task.
		   
* **Update**- To save the edited changes in a task.
		   
* **ExpandAll**- To expand all the TreeGrid rows.
		   
* **CollapseAll**- To collapse all the TreeGrid rows.
		   
* **PdfExport**- To export TreeGrid in PDF format.
		   
* **ExcelExport**- To export TreeGrid in Excel format.

We can enable TreeGrid toolbar by using below code example:
{% highlight CSHTML %}
     @(Html.EJ().TreeGrid("TreeGridContainer")             
             .ToolbarSettings(tool =>
             {
                 tool.ShowToolbar(true);
                 tool.ToolbarItems(new List<TreeGridToolBarItems>()
                {
                    TreeGridToolBarItems.Add,
                    TreeGridToolBarItems.Edit,
                    TreeGridToolBarItems.Delete,
                    TreeGridToolBarItems.Update,
                    TreeGridToolBarItems.Cancel,
                    TreeGridToolBarItems.ExpandAll,
                    TreeGridToolBarItems.CollapseAll,
                    TreeGridToolBarItems.ExcelExport,
                    TreeGridToolBarItems.PdfExport                                    
                });
             })      
        )
{% endhighlight %}
The following screenshot displays the toolbar option in TreeGrid control.
![](Toolbar_images/Toolbar_img1.png)

N> To perform add,edit,delete,cancel,update using Toolbar items we need to enable add/edit/delete using `EditSettings`.
  
## Custom Toolbar Items

CustomToolbarItems allows us to insert custom icons and custom template in TreeGrid toolbar. By using below properties we can customize TreeGrid toolbar as per our requirement.

* **Text**- To insert the custom icons in toolbar using CSS class name selector.

* **TemplateID**-To insert the custom icons in toolbar using script templates. Using this property we can bind HTML elements and other EJ controls to TreeGrid toolbar.

* **TooltipText**-Displays tooltip text for the custom icons. 

To insert EJ Controls in TreeGrid toolbar we need to initiate the control in `Create` client side event.In `ToolbarClick` client side event we can bind actions to the custom toolbar items.

{% highlight CSHTML %}
     @(Html.EJ().TreeGrid("TreeGridContainer")              
            .ToolbarSettings(tool =>
            {
                tool.ShowToolbar(true);
                tool.CustomToolbarItems(ct =>
                  {                  
                    ct.TemplateID("#ColumnVisibility").TooltipText("Column Visibility").Add();
                    ct.Text("Reset").TooltipText("Reset").Add();  
                  });                    
            })
            .ClientSideEvents(cs =>
            {
                cs.Create("create");
                cs.ToolbarClick("toolbarClick");
            })       
    )        
    <script id="ColumnVisibility" type="text/x-jsrender">
        <input id="dropdownContainer" />
    </script>
    <script type="text/javascript">     
        function toolbarClick(args) {
            if (args.itemName == "Reset") {
               //we can bind the custom actions here
            }
        }
	//Here we can append custom EJ controls
        function create(args) {            
            $("#dropdownContainer").ejDropDownList({});
        }
    </script>
     <style type="text/css" class="cssStyles">
     	#TreeGridContainer_ColumnVisibility {
            padding-top: 2px;
            padding-bottom: 0px;
        }

        .Reset:before {
            content: "\e677";
        }
    </style>
	{% endhighlight %}
   ![](Toolbar_images/Toolbar_img2.png)

   [Click](http://mvc.syncfusion.com/demos/web/treegrid/treeGridtoolbartemplate) here to view the demo sample for custom toolbar item



