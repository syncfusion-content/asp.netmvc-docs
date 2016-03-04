---
layout: post
title: Appearance and Styling | Captcha  | ASP.NET MVC | Syncfusion
description: appearance and styling
platform: ejmvc
control: Captcha
documentation: ug
---

# Appearance and Styling

## Hatch Styles

You can customize the captcha background styles by HatchStyle property. 

The following code example is used to render the Captcha with customized Hatch style.

1. Add the following code example to the corresponding CSHTML page to render Captcha with customized Hatch style.


   ~~~ cshtml

   @Html.EJ().Captcha("captcha").HatchStyle(HatchStyle.Cross)

   ~~~
   

2. The following screenshot illustrates the Captcha with some of customized Hatch styles. 
<table>
<tr>
<td>
<br>HatchStyle(HatchStyle.Cross)</td><td>
{{ '![](Appearance-and-Styling_images/Appearance-and-Styling_img1.png)' | markdownify }}
</td></tr>
<tr>
<td>
HatchStyle(HatchStyle.Percent90)</td><td>
{{ '![](Appearance-and-Styling_images/Appearance-and-Styling_img2.png)' | markdownify }}
</td></tr>
<tr>
<td>
HatchStyle(HatchStyle.Wave)</td><td>
{{ '![](Appearance-and-Styling_images/Appearance-and-Styling_img3.png)' | markdownify }}
</td></tr>
<tr>
<td>
HatchStyle(HatchStyle.WideDownwardDiagonal)</td><td>
{{ '![](Appearance-and-Styling_images/Appearance-and-Styling_img4.png)' | markdownify }}
</td></tr>
<tr>
<td>
HatchStyle(HatchStyle.HorizontalBrick)</td><td>
{{ '![](Appearance-and-Styling_images/Appearance-and-Styling_img5.png)' | markdownify }}
</td></tr>
</table>

Captcha with customized Hatch style
{:.caption}

## Pattern

You can customize the patterns of the Captcha by enabling EnablePattern property to true. When the property is set to true, Captcha characters renders with strikeout. By default the property is set as true.

The following code example is used to render the Captcha with hard visibility mode.

1. Add the following code example to the corresponding CSHTML page to render Captcha with visibility mode.


   ~~~ cshtml


		@Html.EJ().Captcha("captcha").EnablePattern(false)

   ~~~
   

2. The following screenshot illustrates the Captcha with disabled pattern. 

![](Appearance-and-Styling_images/Appearance-and-Styling_img6.png)

Captcha without pattern
{:.caption}

## Background and Font color 

You can customize the appearance of Captcha control by using the following property. PatternForeColor is used to set background pattern color. PatternBackColor is used to set background color for Captcha. ForeColor is used to set Captcha text color.

The following code example is used to render the Captcha with customized appearance.

1. Add the following code example to the corresponding CSHTML page to render Captcha with customized appearance.

   ~~~ cshtml

		@Html.EJ().Captcha("captcha").PatternForeColor(System.Drawing.Color.LightGray).PatternBackColor(System.Drawing.Color.Snow).ForeColor(System.Drawing.Color.LightSeaGreen) 

   ~~~
   

2. The following screenshot illustrates the Captcha with customized appearance. 

![](Appearance-and-Styling_images/Appearance-and-Styling_img7.png)

Captcha with customized appearance
{:.caption}

## Adjusting Captcha Size

### Height and width Customization

The height of the Captcha widget can be customized using “Height” property that accepts only integer values. The width of the Captcha widget can be customized using “Width” property that also accepts only integer values.

The following code example is used to render the Captcha with customized Height and Width.

1. Add the following code example to the corresponding CSHTML page to render Captcha with customized Height and Width.


   ~~~ cshtml


		@Html.EJ().Captcha("captcha").Height(50).Width(150)

   ~~~
   

2. The following screenshot illustrates the Captcha with customized Height and Width. 

![](Appearance-and-Styling_images/Appearance-and-Styling_img8.png)

Captcha with customized Height and Width
{:.caption}

## Theme

You can control the appearance of border color, refresh and audio button styles of the Captcha control based on CSS classes. In order to apply these styles, you can refer to the 2 files, ej.widgets.core.min.css and ej.theme.min.css. When ej.widgets.all.min.css file is referred, it is not necessary to include the files ej.widgets.core.min.css and ej.theme.min.css in your project, as ej.widgets.all.min.css is the combination of these two. 

By default, there are 12 themes support available for Captcha control.

* default-theme
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

### Appearance for gradient-azure,

![](Appearance-and-Styling_images/Appearance-and-Styling_img9.png)

Captcha with gradient-azure theme
{:.caption}

### Appearance for flat-lime,

![](Appearance-and-Styling_images/Appearance-and-Styling_img10.png)

Captcha with flat-lime theme
{:.caption}
