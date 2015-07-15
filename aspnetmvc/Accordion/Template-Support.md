---
layout: post
title: Template-Support
description: template support
platform: ejmvc
control: Accordion 
documentation: ug
---

## Template Support

The Content template option provided in MVC is used to specify the HTML elements inside the Accordion control. You can use this option to load any HTML elements and display it in the Accordion panels as per your requirement.

The following code example explains how to use content template option in the Accordion control.

[CSHTML]



&lt;div style="width:500px;"&gt;

    @{Html.EJ().Accordion("pizzaMenu").Items(data =>

               {

                   data.Add().Text("GARDEN FRESH (Veg)").ContentTemplate(@&lt;div&gt;

                    &lt;img src="~/Content/accordion/garden-veggie.png" alt="garden-fresh" /&gt;

                                        &lt;div class="ingredients"&gt;

                        Rate    : $50

                        &lt;br /&gt;

                        Ingredients : cheese, onions, green capsicums & tomatoes.

                    &lt;/div&gt;

                &lt;/div&gt;);

                   data.Add().Text("CORN & SPINACH (Veg)").ContentTemplate(@&lt;div&gt;

                    &lt;img src="~/Content/accordion/corn-and-spinach-05.png" alt="garden-fresh" /&gt;

                    &lt;div class="ingredients"&gt;

                        Rate    : $70

                        &lt;br /&gt;

                        Ingredients : cheese, sweet corn & green capsicums.

                    &lt;/div&gt;

                &lt;/div&gt;);

                   data.Add().Text("CHICKEN DELITE (Non-veg)").ContentTemplate(@&lt;div&gt;

                    &lt;img src="~/Content/accordion/chicken-delite.png" alt="garden-fresh" /&gt;

                    &lt;div class="ingredients"&gt;

                        Rate    : $100

                        &lt;br /&gt;

                        Ingredients : cheese, chicken chunks, onions & pineapple chunks.

                    &lt;/div&gt;

                &lt;/div&gt;);

                     data.Add().Text("KEEMA LA JAWAB (Non-veg)").ContentTemplate(@&lt;div&gt;

                    &lt;img src="@Url.Content("~/Images/accordion/chicken-delite.png")" alt="garden-fresh" /&gt;

                    &lt;div class="ingredients"&gt;

                        Rate    : $95

                        &lt;br /&gt;

                        Ingredients : lamb keema, onions, garlic & tandoori seasoning.

                    &lt;/div&gt;

                &lt;/div&gt;);

               }).EnableMultipleOpen(true).Render();}

&lt;/div&gt;





Output:

{ ![](Template-Support_images/Template-Support_img1.png) | markdownify }
{:.image }






