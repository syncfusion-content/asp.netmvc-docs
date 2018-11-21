---
layout: post
title: Template Support | Accordion  | ASP.NET MVC | Syncfusion
description: template support
platform: ejmvc
control: Accordion 
documentation: ug
---

# Template Support

## Content Template

The Content template option provided in MVC is used to specify the HTML elements inside the Accordion control. You can use this option to load any HTML elements and display it in the Accordion panels as per your requirement.

The following code example explains how to use content template option in the Accordion control.

{% highlight CSHTML %}

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

## Header Template

The Header template option provided in MVC is used to specify the HTML elements inside the Accordion control.

The following code example explains how to use header template option in the Accordion control.

{% highlight CSHTML %}

@{
    ViewBag.Title = "Accordion";
    Layout = "~/Views/Shared/_Layout.cshtml";
}
@model AccordionIcons.AccordionController.SI_MODULO
<h2>Accordion</h2>
<br/>
<br/>
<div id = "ControlRegion">
    <div style="width: 400px;">
        @{Html.EJ().Accordion("iconAccordion").Items(data =>
        {
            foreach (var m in Model.image)
            {
                var node = data.Add().Text(m.text).HeaderTemplate(@<div>
                <image class='logos' src='http://js.syncfusion.com/demos/web/content/images/Employees/@m.imageID' />
                </div>).ContentTemplate(@<div> This is just a sample text.</div>);
            }
        }).Render();}
    </div>
<style type="text/css">
.logos {
    float: left;
    height: 35px;
    margin: -6px 1px 2px -5px;
    width: 35px;
}
    </style>
</div>

{% endhighlight %}

{% highlight C# %}

List<ImagesID> list = new List<ImagesID>();
public ActionResult AccordionFeatures()
 {
   SI_MODULO model = new SI_MODULO();
   list.Add(new ImagesID { imageID = "6.png", text = "Volkswagen" });
   list.Add(new ImagesID { imageID = "7.png", text = "Mitsubishi" });
   list.Add(new ImagesID { imageID = "8.png", text = "Mercedes-Benz" });
   model.image = list;
   return View(model);
 }
public class ImagesID {
    public string imageID { get; set; }
    public string text { get; set; }
}
public class SI_MODULO {
public List<ImagesID> image { get; set; }
}

{% endhighlight %}
