---
layout: post
title: Appearance-and-Styling
description: appearance and styling
platform: ejmvc
control: Tab Control
documentation: ug
---

## Appearance and Styling

Header Image Customization

 To set the Tab header image for each Tab item you need to specify image in “ImageCssClass” property during the TabItem declaration.

The following code example is used to add the header image for the root Tab header element. 

1. Add the following code in your view page to render Tab with header image.



[CSHTML]

// Add the following code example to the corresponding CSHTML page to render Tab with header image.

 &lt;div id="dishtab" style="width:550px"&gt;

    &lt;ul&gt;

        &lt;li&gt;&lt;span class="dish pizzaImg"&gt;&lt;/span&gt;<a href="#pizzatype">Pizza Type</a>&lt;/li&gt;

        &lt;li&gt;&lt;span class="dish sandwichImg"&gt;&lt;/span&gt;<a href="#sandwichtype">Sandwich Type</a>&lt;/li&gt;

    &lt;/ul&gt;

    &lt;div id="pizzatype" style="background-color: #F5F5F5"&gt;

        <p>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.&lt;/p&gt;

    &lt;/div&gt;	

    &lt;div id="sandwichtype" style="background-color: #F5F5F5"&gt;        

        <p>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.&lt;/p&gt;

    &lt;/div&gt;

    @Html.EJ().Tab("dishtab")

&lt;/div&gt;





2. Add following CSS for header image customization.

[CSS]

&lt;style type="text/css" class="cssStyles"&gt;

        .dish {

            display: inline-block;

            vertical-align: middle;

            margin: 0px -9px 0px 9px;           

        }

        .pizzaImg {

            background: url("http://js.syncfusion.com/UG/Web/Content/rsz_chicken-delite.png") no-repeat;

            height: 25px;

            width: 25px;

        }

        .sandwichImg, .pastaImg {

            height: 25px;

            width: 25px;

        }

        .sandwichImg {

            background: url("http://js.syncfusion.com/UG/Web/Content/rsz_garden-fresh.png") no-repeat;

        }

&lt;/style&gt; 

3. The following screenshot illustrates the Tab with the customized header image. 

{ ![](Appearance-and-Styling_images/Appearance-and-Styling_img1.png) | markdownify }
{:.image }


_Figure 12: Header Image Customization_

Rounded corner

By enabling ‘ShowRoundedCorner’ property, you can customize the shape of the Tab widget from regular rectangular shape to rounded rectangle shape that is set to ‘false’ by default. 

The following code example is used to render the Tab widget with Roundedcorner.

1. Add the following code in your view page to render Tab with rounder corner.



[CSHTML]

// Add the following code example to the corresponding CSHTML page to render Tab with rounded corner.



&lt;div style="width: 550px"&gt;

    @{Html.EJ().Tab("dishtab").Items(data =>

           {

               data.Add().ID("pizzatype").Text("Pizza Type")

                   .ContentTemplate(@<div>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.&lt;/div&gt;);

               data.Add().ID("sandwichtype").Text("Sandwich Type")

                   .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

               &lt;/div&gt;);

           }).ShowRoundedCorner(true).Render();}

&lt;/div&gt;





2. The following screenshot illustrates the Tab with Rounded corner.

{ ![](Appearance-and-Styling_images/Appearance-and-Styling_img2.png) | markdownify }
{:.image }


_Figure 13: Tab with rounded corner_

Enable/Disable

You can enable or disable the Tab widget by ‘Enabled’ property. By default, the property set to ‘true’.

The following code example is used to render the Tab widget with enable/disable.

1. Add the following code in your view page to render Tab with enable/disable.



[CSHTML]

// Add the following code example to the corresponding CSHTML page to render Tab with Enable/Disable format.



&lt;div style="width: 550px"&gt;

    @{Html.EJ().Tab("dishtab").Items(data =>

           {

               data.Add().ID("pizzatype").Text("Pizza Type")

                   .ContentTemplate(@<div>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.&lt;/div&gt;);

               data.Add().ID("sandwichtype").Text("Sandwich Type")

                   .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

               &lt;/div&gt;);

           }).Enabled(false).Render();}

&lt;/div&gt;





2. The following screenshot illustrates the Tab with disabled format.

{ ![](Appearance-and-Styling_images/Appearance-and-Styling_img3.png) | markdownify }
{:.image }


_Figure 14: Tab with disabled format_

Enabling Reload Icon

Without refresh/reload the whole page, you can reload a particular Tab using Reload icon. The Reload icon is appeared at right corner of the Tab by enabling the property ‘ShowReloadIcon’ to ‘true’. When you move cursor over the Tab headers, the Reload icon is displayed. By default the property value is set to ‘false’.   

The following code example is used to render the Tab widget with Reload icon.

1. Add the following code in your view page to render Tab with Reload icon.



[CSHTML]

// Add the following code example to the corresponding CSHTML page to render Tab with reload icon.



&lt;div style="width: 550px"&gt;

    @{Html.EJ().Tab("dishtab").Items(data =>

           {

               data.Add().ID("pizzatype").Text("Pizza Type")

                   .ContentTemplate(@<div>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.&lt;/div&gt;);

               data.Add().ID("sandwichtype").Text("Sandwich Type")

                   .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

               &lt;/div&gt;);

           }).ShowReloadIcon(true).Render();}

&lt;/div&gt;



2. The following screenshot illustrates the Tab with Reload icon.

{ ![](Appearance-and-Styling_images/Appearance-and-Styling_img4.png) | markdownify }
{:.image }


_Figure 15: Tab with reload icon_



Collapsible Tabs

You can collapse the Tab content by enabling the ‘Collapsible’ property to ‘true’. When the property is set to ‘true’ then click the active Tab header, the Tab contents are hided. By default, the property value is set to ‘false’.

The following code example is used to render the Tab widget with customized collapsible mode.

1. Add the following code in your view page to render Tab with customized collapsible mode.



[CSHTML]

// Add the following code example to the corresponding CSHTML page to render Tab with collapsible mode.

&lt;div style="width: 550px"&gt;

    @{Html.EJ().Tab("dishtab").Items(data =>

           {

               data.Add().ID("pizzatype").Text("Pizza Type")

                   .ContentTemplate(@<div>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.&lt;/div&gt;);

               data.Add().ID("sandwichtype").Text("Sandwich Type")

                   .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

               &lt;/div&gt;);

           }).Collapsible(true).Render();}

&lt;/div&gt;





2. The following screenshot illustrates the Tab with customized collapsible mode.

{ ![](Appearance-and-Styling_images/Appearance-and-Styling_img5.png) | markdownify }
{:.image }


_Figure 16: Tab with customized collapsible mode_

Adjusting Tab Size

Height Adjust Mode and Height

The height of the Tab widget is customized by ‘height’ property. The Tab widget height depends on ‘HeightAdjustMode’ property. Using the HeightAdjustMode property, you can adjust height by “Content”, “Auto”, “Fill”. By default the HeightAdjustMode is set as content.

The following code example is used to render the Tab widget with customized height and height adjust mode.

1. Add the following code in your view page to render Tab with customized height and height adjust mode.



[CSHTML]

// Add the following code example to the corresponding CSHTML page to render Tab with customized height and height adjust mode.



&lt;div style="width: 550px"&gt;

    @{Html.EJ().Tab("dishtab").Items(data =>

           {

               data.Add().ID("pizzatype").Text("Pizza Type")

                   .ContentTemplate(@<div>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.&lt;/div&gt;);

              data.Add().ID("sandwichtype").Text("Sandwich Type")

                  .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

               &lt;/div&gt;);

           }).HeightAdjustMode(HeightAdjustMode.Fill).Height("300px").Render();}

&lt;/div&gt;





2. The following screenshot illustrates the Tab with customized height and height adjust mode.

{ ![](Appearance-and-Styling_images/Appearance-and-Styling_img6.png) | markdownify }
{:.image }


_Figure 17: Tab with customized height and height adjust mode_



Width

The width of the Tab widget is customized by using ‘Width’ property that accepts only the pixel values.

The following code example is used to render the Tab widget with customized width.

1. Add the following code in your view page to render Tab with customized width.



[CSHTML]

// Add the following code example to the corresponding CSHTML page to render Tab with customized width.



&lt;div&gt;

    @{Html.EJ().Tab("dishtab").Items(data =>

           {

               data.Add().ID("pizzatype").Text("Pizza Type")

                   .ContentTemplate(@<div>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.&lt;/div&gt;);

               data.Add().ID("sandwichtype").Text("Sandwich Type")

                   .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

               &lt;/div&gt;);

           }).Width("450").Render();}

&lt;/div&gt;





2. The following screenshot illustrates the Tab with customized width.

{ ![](Appearance-and-Styling_images/Appearance-and-Styling_img7.png) | markdownify }
{:.image }


_Figure 18: Tab with customized width_

Theme

Tab control’s style and appearance are controlled based on CSS classes. In order to apply styles to the Tab control, you can refer 2 files namely, ej.widgets.core.min.css and ej.theme.min.css. When the file ej.widgets.all.min.css is referred, then it is not necessary to include the files ej.widgets.core.min.css and ej.theme.min.css in your project, as ej.widgets.all.min.css is the combination of these two. 

By default, there are 13 themes support available for Tab control namely

* default-theme
* bootstrap-theme
* flat-azure-dark
* fat-lime
* flat-lime-dark
* flat-saffron
* flat-saffron-dark
* gradient-azure
* gradient-azure-dark
* gradient-lime
* gradient-lime-dark
* gradient-saffron
* gradient-saffron-dark

Custom styles

The style of the Tab widget is customized by ‘CssClass’ property. 

The following code example is used to render the Tab widget with customized style.

1. Add the following code in your view page to render Tab with customized style.



[CSHTML]

// Add the following code example to the corresponding CSHTML page to render Tab with customized style.



&lt;div&gt;

    @{Html.EJ().Tab("dishtab").Items(data =>

           {

               data.Add().ID("pizzatype").Text("Pizza Type")

                   .ContentTemplate(@<div>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.&lt;/div&gt;);

               data.Add().ID("sandwichtype").Text("Sandwich Type")

                   .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

               &lt;/div&gt;);

           }).CssClass("custom").Render();}

&lt;/div&gt;







2. Add the following styles

[CSS]

&lt;style type="text/css"&gt;

        .custom {

            width:650px;

        }

    &lt;/style&gt;

3. The following screenshot illustrates the Tab with customized style.

{ ![](Appearance-and-Styling_images/Appearance-and-Styling_img8.png) | markdownify }
{:.image }


_Figure 19: Tab with customized style_

