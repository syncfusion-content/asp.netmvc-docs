---
layout: post
title: Center-Menu
description: center menu
platform: ejmvc
control: Menu
documentation: ug
---

## Center Menu

You can align the Menu items to center by setting “EnableCenterAlign” property as true. “EnableCenterAlign” property accepts Boolean value. By default, its value is false. When set to true, then the root menu items is aligned in center.

1. Add the following code in your view section.



[CSHTML]  

// Add the following code in CSHTML section.

&lt;div class="imgframe"&gt;

@Html.EJ().Menu("menucontrol").Items(items =>

        {

            items.Add().Id("Home").Text("Home").Children(child =>

                {

                    child.Add().Text("Foundation");

                    child.Add().Text("Launch");

                    child.Add().Text("About").Children(child1 =>

                    {

                        child1.Add().Text("Company");

                        child1.Add().Text("Location");

                    });

                });

            items.Add().Text("Services").Children(child =>

                {

                    child.Add().Text("Consulting");

                    child.Add().Text("Outsourcing");

                });

            items.Add().Text("About");

            items.Add().Id("Contact").Text("Contact Us").Children(child =>

                {

                    child.Add().Text("Contact number");

                    child.Add().Text("E-mail");

                });

            items.Add().Id("Careers").Text("Careers").Children(child =>

                 {



                     child.Add().Text("Position").Children(child1 =>

                             {

                                 child1.Add().Text("Developer");

                                 child1.Add().Text("Manager");

                             });

                     child.Add().Text("Apply online");

                 });



        }).Width("500").EnableCenterAlign(true)&lt;/div&gt;







The following screenshot displays the output of the above code.

{ ![](Center-Menu_images/Center-Menu_img1.png) | markdownify }
{:.image }


_Figure_ _34__: Center Menu_

