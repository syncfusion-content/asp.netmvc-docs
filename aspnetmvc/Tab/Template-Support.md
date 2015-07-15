---
layout: post
title: Template-Support
description: template support
platform: ejmvc
control: Tab Control
documentation: ug
---

## Template Support

ASP.NET MVC

The Content template option provided in MVC is used to specify the HTML elements inside the Tab control. We can use this option to load any HTML elements and showcase it in the Tab panels as per our requirement.

The following code block showcases how to use content template option in the Tab control.



[CSHTML]



&lt;div style="width:650px"&gt;

    @{Html.EJ().Tab("pizzaMenu").Items(data =>

           {

               data.Add().ID("gardenfresh").Text("GARDEN FRESH (Veg)")

                   .ContentTemplate(@&lt;div&gt;

                    &lt;img src="~/Content/accordion/garden-veggie.png" alt="garden-fresh" /&gt;

                    &lt;div class="ingredients"&gt;

                        Rate    : $50

                        &lt;br /&gt;

                        Ingredients : cheese, onions, green capsicums & tomatoes.

                    &lt;/div&gt;

                &lt;/div&gt;);

               data.Add().ID("cornandspinach").Text("CORN & SPINACH (Veg)")

                   .ContentTemplate(@&lt;div&gt;

                    &lt;img src="~/Content/accordion/corn-and-spinach-05.png" alt="garden-fresh" /&gt;

                    &lt;div class="ingredients"&gt;

                        Rate    : $70

                        &lt;br /&gt;

                        Ingredients : cheese, sweet corn & green capsicums.

                    &lt;/div&gt;

                &lt;/div&gt;);

               data.Add().ID("chickendelite").Text("CHICKEN DELITE (Non-veg)")

                   .ContentTemplate(@&lt;div&gt;

                    &lt;img src="~/Content/accordion/chicken-delite.png" alt="garden-fresh" /&gt;

                    &lt;div class="ingredients"&gt;

                        Rate    : $100

                        &lt;br /&gt;

                        Ingredients : cheese, chicken chunks, onions & pineapple chunks.

                    &lt;/div&gt;

                &lt;/div&gt;);

           }).Render();}

&lt;/div&gt;







Output:

{ ![](Template-Support_images/Template-Support_img1.png) | markdownify }
{:.image }


_Figure 25: Tab control with template support_



