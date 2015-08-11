---
layout: post
title: Drag-and-Drop
description: drag and drop
platform: ejmvc
control: TreeView
documentation: ug
---

# Drag and Drop

You can Drag and Drop the nodes within the TreeView control or drag a particular node from one tree to another tree.

To enable or disable this option, set the appropriate value for the AllowDragAndDrop property. When AllowDragAndDrop is enabled, the nodes of a TreeView are dragged and dropped between all levels. 

The following steps explain enabling the AllowDragAndDrop property for TreeView.

1.	In the View page, add TreeView helper as shown below 


{% highlight html %}

\\ To configure TreeView in the CSHTML page

@Html.EJ().TreeView("treeview").Items(items =>

    {

        items.Add().Text("Favorites").Expanded(true).Children(child =>

                   {

                       child.Add().Text("Desktop");

                       child.Add().Text("Downloads");

                       child.Add().Text("Recent places");

                   });

        items.Add().Text("Libraries").Expanded(true).Children(child =>

        {

            child.Add().Text("Documents").Children(child1 =>

                {

                    child1.Add().Text("My Documents");

                    child1.Add().Text("Public Documents");

                });

            child.Add().Text("Pictures").Children(child1 =>

            {

                child1.Add().Text("My Pictures");

                child1.Add().Text("Public Pictures");

            });

            child.Add().Text("Music").Children(child1 =>

            {

                child1.Add().Text("My Music");

                child1.Add().Text("Public Music");

            });

            child.Add().Text("Subversion");



        });

        items.Add().Text("Computer").Children(child =>

        {

            child.Add().Text("Folder(C)");

            child.Add().Text("Folder(D)");

            child.Add().Text("Folder(E)");

        });

}).AllowDragAndDrop(true)


{% endhighlight %}


The output for TreeView when AllowDragAndDrop is set to True.



<table>
<tr>
<td>
{{ ' ![](Drag-and-Drop_images/Drag-and-Drop_img1.png)' | markdownify }}

</td><td>

{{ '![](Drag-and-Drop_images/Drag-and-Drop_img2.png)' | markdownify }}

</td></tr>
</table>

_Figure41: Drag And Drop TreeView_

## Allow Drop Child

We can prevent the TreeNodes from dropping as child. If we specify the value as false for the AllowDropChild property means, then we can only reorder the Tree nodes, we cannot drop the nodes as child element. Refer the below code to disable the AllowDropChild property.

{% highlight html %}

    @Html.EJ().TreeView("treeview").Items(items =>

    {

        items.Add().Text("Favorites").Expanded(true).Children(child =>

                   {

                       child.Add().Text("Desktop");

                       child.Add().Text("Downloads");

                       child.Add().Text("Recent places");

                   });

        items.Add().Text("Libraries").Expanded(true).Children(child =>

        {

            child.Add().Text("Documents").Children(child1 =>

                {

                    child1.Add().Text("My Documents");

                    child1.Add().Text("Public Documents");

                });

            child.Add().Text("Pictures").Children(child1 =>

            {

                child1.Add().Text("My Pictures");

                child1.Add().Text("Public Pictures");

            });

            child.Add().Text("Music").Children(child1 =>

            {

                child1.Add().Text("My Music");

                child1.Add().Text("Public Music");

            });

            child.Add().Text("Subversion");



        });

        items.Add().Text("Computer").Children(child =>

        {

            child.Add().Text("Folder(C)");

            child.Add().Text("Folder(D)");

            child.Add().Text("Folder(E)");

        });



    }).AllowDragAndDrop(true).AllowDropChild(false)

{% endhighlight %}



## Allow Drop Sibling

You can drag the root node and drop it into the same level of node that is a sibling node in TreeView by using the property AllowDropSibling. You can disable this option using the property AllowDropSibling in TreeView control as follows.




{% highlight html %}


   @Html.EJ().TreeView("treeview").Items(items =>

    {

        items.Add().Text("Favorites").Expanded(true).Children(child =>

                   {

                       child.Add().Text("Desktop");

                       child.Add().Text("Downloads");

                       child.Add().Text("Recent places");

                   });

        items.Add().Text("Libraries").Expanded(true).Children(child =>

        {

            child.Add().Text("Documents").Children(child1 =>

                {

                    child1.Add().Text("My Documents");

                    child1.Add().Text("Public Documents");

                });

            child.Add().Text("Pictures").Children(child1 =>

            {

                child1.Add().Text("My Pictures");

                child1.Add().Text("Public Pictures");

            });

            child.Add().Text("Music").Children(child1 =>

            {

                child1.Add().Text("My Music");

                child1.Add().Text("Public Music");

            });

            child.Add().Text("Subversion");



        });

        items.Add().Text("Computer").Children(child =>

        {

            child.Add().Text("Folder(C)");

            child.Add().Text("Folder(D)");

            child.Add().Text("Folder(E)");

        });



    }).AllowDragAndDrop(true).AllowDropSibling(false)



{% endhighlight %}

