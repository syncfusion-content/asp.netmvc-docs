---
layout: post
title: Toolbar
description: toolbar
platform: ejmvc
control: TreeGrid
documentation: ug
---

# Toolbar

TreeGrid control contains toolbar options for adding, deleting and editing the records. You can customize the TreeGridToolbar tools by using ToolbarSettings API. 

In TreeGrid by using RowPosition API, the index position for the newly added row can be provided. Default value of the RowPosition property is top. The Enum values for RowPosition API are,

* top
* bottom
* aboveSelectedRow
* belowSelectedRow

You can enable toolbar for TreeGrid, using the following code example.



{% highlight js %}

@(Html.EJ().TreeGrid("TreeGridContainer")



                    //...

.EditSettings(edit =>

               {

                  //...

           edit.RowPosition(TreeGridRowPosition.AboveSelectedRow);



              })

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



                });



              })

.Datasource(ViewBag.datasource)

        )



{% endhighlight %}





The following screenshot displays the toolbar option in TreeGrid control

![](Toolbar_images/Toolbar_img1.png)



