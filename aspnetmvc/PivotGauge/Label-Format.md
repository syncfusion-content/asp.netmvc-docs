---
layout: post
title: Label Format | PivotGauge | ASP.NET MVC | Syncfusion
description: label format
platform: ejmvc
control: PivotGauge
documentation: ug
---

# Label Format

You can customize the format of labels displayed in the PivotGauge control using `LabelFormatSettings` property.

Following are the formats that can be applied to labels in PivotGauge:

* `NumberFormats` - Allows the user to change the number format of the label values in PivotGauge.
* `DecimalPlaces` - Allows you to set the number of digits displayed after decimal point.
* `PrefixText` - Allows you to add a text at the beginning of the label.
* `SuffixText` - Allows you to add text at the end of the label.

Number format for the label values can be set to any of the following type:

* Default	
* Currency
* Percentage
* Fraction
* Scientific
* Text
* Notation

{% highlight CSHTML %}

    @Html.EJ().Pivot().PivotGauge("PivotGauge1").LabelFormatSettings(labelFormatSettings=> labelFormatSettings.NumberFormats(NumberFormat.Percentage).DecimalPlaces(2).PrefixText("#*").SuffixText("*#"))

{% endhighlight %}

![](Label-Format_images/labelformat.png) 
