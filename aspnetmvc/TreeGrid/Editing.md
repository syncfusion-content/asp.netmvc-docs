---
layout: post
title: Editing
description: editing
platform: ejmvc
control: TreeGrid
documentation: ug
---

# Editing

The TreeGrid control provides built-in support for Editing cell items. 

## Cell Editing

Update the task details through grid Cell Editing by setting EditMode as CellEditing.

The following code example shows you how to enable CellEditing in TreeGrid control.

{% highlight js %}

@(Html.EJ().TreeGrid("TreeGridContainer")

//...

.EditSettings(edit =>

       {

           edit.AllowEditing(true);

           edit.EditMode(TreeGridEditMode.CellEditing);

       })

)

{% endhighlight %}

The output of TreeGrid with CellEditing is as follows.



![](Editing_images/Editing_img1.png)





