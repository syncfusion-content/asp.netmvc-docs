---
layout: post
title: Miscellaneous
description: miscellaneous
platform: ejmvc
control: TreeView
documentation: ug
---

## Miscellaneous

Enabled

You can enable or disable the TreeView control by using the property Enabled. You can enable the TreeView control by setting the property enabled to “True” and you can specify the property Enabled in the script as follows.





[View]



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



    }).ShowCheckbox(true).Enabled(true)



Expanded Nodes

You can specify the expandednode level in TreeView by using the property ExpandedNodes. Expandednodes index collection is given to integer array. Add the following code in your script section.





[View]



@{List<int> nodes = new List<int>() { 0,4 }; }

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



    }).ExpandedNodes(nodes)





Expand On

Node can be expanded for specified events. You can specify the property ExpandOn in TreeView control in the script as follows.





[View]



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



    }).ExpandOn("dblclick")





