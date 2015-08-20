---
layout: post
title: Template-Support
description: template support
platform: ejmvc
control: Accordion 
documentation: ug
---

# Template Support

The Content template option provided in MVC is used to specify the HTML elements inside the Accordion control. You can use this option to load any HTML elements and display it in the Accordion panels as per your requirement.

The following code example explains how to use content template option in the Accordion control.

{% highlight html %}




<div style="width:500px;">

    @{Html.EJ().Accordion("pizzaMenu").Items(data =>

               {

                   data.Add().Text("GARDEN FRESH (Veg)").ContentTemplate(@<div>

                    <img src="~/Content/accordion/garden-veggie.png" alt="garden-fresh" />

                                        <div class="ingredients">

                        Rate    : $50

                        <br />

                        Ingredients : cheese, onions, green capsicums & tomatoes.

                    </div>

                </div>);

                   data.Add().Text("CORN & SPINACH (Veg)").ContentTemplate(@<div>

                    <img src="~/Content/accordion/corn-and-spinach-05.png" alt="garden-fresh" />

                    <div class="ingredients">

                        Rate    : $70

                        <br />

                        Ingredients : cheese, sweet corn & green capsicums.

                    </div>

                </div>);

                   data.Add().Text("CHICKEN DELITE (Non-veg)").ContentTemplate(@<div>

                    <img src="~/Content/accordion/chicken-delite.png" alt="garden-fresh" />

                    <div class="ingredients">

                        Rate    : $100

                        <br />

                        Ingredients : cheese, chicken chunks, onions & pineapple chunks.

                    </div>

                </div>);

                     data.Add().Text("KEEMA LA JAWAB (Non-veg)").ContentTemplate(@<div>

                    <img src="@Url.Content("~/Images/accordion/chicken-delite.png")" alt="garden-fresh" />

                    <div class="ingredients">

                        Rate    : $95

                        <br />

                        Ingredients : lamb keema, onions, garlic & tandoori seasoning.

                    </div>

                </div>);

               }).EnableMultipleOpen(true).Render();}

</div>

{% endhighlight %}



Output:

![](Template-Support_images/Template-Support_img1.png)






