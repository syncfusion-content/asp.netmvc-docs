---
layout: post
title: Customizing-the-appearance
description: customizing the appearance
platform: ejmvc
control: Barcode
documentation: ug
---

## Customizing the appearance

A page or printed media with Barcode often appears colorful in the background and surrounding region with other contents. In such cases the Barcode can also be customized to suit the needs. You can achieve this by changing the darkBarColor property.


{{ '![C:/Users/labuser/Desktop/note.jpg](Customizing-the-appearance_images/Customizing-the-appearance_img1.jpeg)' | markdownify }}
{:.image }
_Note: This color customization is possible only for one dimensional barcodes and it is not supported for two dimensional barcodes._



{% highlight html %}

[CSHTML]



<div>

<div

@Html.EJ().Barcode("barcode")

          .Text("B5330E8278BC4C797C49DD3ED5AD9715")

          .SymbologyType(BarcodeSymbolType.Code39)

          .DisplayText(true)

          .QuietZone(qz => { qz.All(30);})

          .BarcodeToTextGapHeight(10)

          .BarHeight(150)

          .DarkBarColor("blue")

          .EncodeStartStopSymbol(true)

          .LightBarColor("white")

          .NarrowBarWidth(1)

          .TextColor("red")

          .WideBarWidth(3)

          .Render()

</div>

</div>



{% endhighlight %}



Execute the above code to render the following output.



{{ '![](Customizing-the-appearance_images/Customizing-the-appearance_img2.png)' | markdownify }}
{:.image }


_Figure_ _4__: Customized Barcode_

The height of the barcode can be changed using the BarHeight property. The equivalent property to change the block size for two dimensional barcode is XDimension.



{% highlight html %}

[CSHTML]



<div>

<div

@Html.EJ().Barcode("barcode")

          .Text("B5330E8278BC4C797C49DD3ED5AD9715")

          .SymbologyType(BarcodeSymbolType.Code39)

          .DisplayText(false)

          .BarcodeToTextGapHeight(10)

          .BarHeight(45)

          .DarkBarColor("#990099")

          .Render()

</div>

</div>



{% endhighlight %}



Execute the above code to render the following output.


{{ '![](Customizing-the-appearance_images/Customizing-the-appearance_img3.png)' | markdownify }}
{:.image }


_Figure_ _5__: Barcode with customized height_



