---
layout: post
title: Hierarchical-data-with-Editingcutpaste-support
description: hierarchical data with editing,cut,paste support
platform: ejmvc
control: TreeView
documentation: ug
---

## Hierarchical data with Editing,cut,paste support

The TreeView control permits you to edit a node and also allows you to cut, copy and paste the node. You can edit the tree node name when it is required. This is achieved by using the AllowEditing property. By setting the property as “True”, you can select a node and press F2 or double click the node to initiate editing.

The following steps explain how to enable the AllowEditing property for TreeView.

1. In the View page, add TreeView helper as shown below. It will render the TreeView with specified items and with allow editing, cut and paste options enabled. Cut and paste options will be enabled only when drag and drop option is enabled.







[View]

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



    }).AllowEditing(true).AllowDragAndDrop(true)









2. The following screenshot displays the appearance of Editing-cut-copy-paste the node in TreeView component.



{ ![](Hierarchical-data-with-Editingcutpaste-support_images/Hierarchical-data-with-Editingcutpaste-support_img1.png) | markdownify }
{:.image }


_Figure_ _40__: Node Editing-cut-copy-paste_

