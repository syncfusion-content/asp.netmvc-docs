---
layout: post
title: Bullet Graph Caption | BulletGraph | ASP.NET MVC | Syncfusion
description: bullet graph caption
platform: ejmvc
control: BulletGraph	
documentation: ug
---

# Bullet Graph Caption

**Bullet Graph** supports `title` and `subtitle` to convey what is represented in **Bullet Graph**. They are customized using CaptionSettings property.

### Title

**Title** is set to **Bullet Graph** using `Text` property in `CaptionSettings`. Caption settings also include properties like `Location`, `Font`, and `TextAngle` for customizing the caption of Bullet Graph.

### Location

Using `location` option, you can set the `X` and `Y` position of caption text.

### Font

Using `font` property, you can customize `font color`, `font family`, `font style`, `font weight`, `opacity`, `size` options.


{% highlight cshtml %}

@(Html.EJ().BulletGraph("Bullets").QuantitativeScaleSettings( scale=>

		scale.Location( loc=> loc.x(110).y(200))

		.Minimum(0)

		.Maximum(5)

		.Interval(1)

		.FeatureMeasure(measure=>measure.Value(4).ComparativeMeasureValue(3.5)))

	    .Height(700)

	    .Width(600)

	    .CaptionSettings(cs=>

	    cs.Text("Revenue YTD")

	    .Location(loc=>loc.y(220))

	    .Font(font=>font.FontStyle("bold").FontColor(System.Drawing.Color.Gray).FontSize("14px")))

  )

{% endhighlight %}

The following screenshot displays a **Bullet Graph** with customized caption using the above code

![](Bullet-Graph-Caption_images/Bullet-Graph-Caption_img1.png)

Bullet Graph with title
{:.caption}


## Subtitle

**Subtitle** is added to **Bullet Graph** using Text property of `Subtitle` in `CaptionSettings`. Subtitle also provides properties like `Location`, `TextAngle` and `Font` to customize subtitle similar to caption.


### Location

Using `location` option, you can set the `X` and `Y` position of caption text.

### Font

Using `font` property, you can customize `font color`, `font family`, `font style`, `font weight`, `opacity`, `size` options.

{% highlight cshtml %}

@(Html.EJ().BulletGraph("Bullets").QuantitativeScaleSettings( scale=>

	scale.Location( loc=> loc.x(110).y(200))

	.Minimum(0)

	.Maximum(5)

	.Interval(1)

	.FeatureMeasure(measure=>measure.Value(4).ComparativeMeasureValue(3.5)))

	.Height(700)

	.Width(600)

	.CaptionSettings(cs=>

	cs.SubTitle(subtitle=>

	subtitle.Text("Subtitle")

	.Location(loc=>loc.x(20).y(225))

	.Font(font=>font.FontStyle("italic").FontSize("16px")))

	.Text("Revenue YTD")

	.Location(loc=>loc.y(210))

	.Font(font=>font.FontStyle("bold").FontColor(System.Drawing.Color.Gray).FontSize("14px")))
     
	)


{% endhighlight %}
The following screenshot displays **Bullet Graph** with a subtitle

![](Bullet-Graph-Caption_images/Bullet-Graph-Caption_img2.png)

Bullet Graph with subtitle
{:.caption}

## Indicator

You can add **Indicator** to bullet graph by enabling `Visible` and setting `Text` properties of `Indicator` in **CaptionSettings**. Indicator is used to represent whether target is achieved or not with text and symbol by comparing current and target values in bullet graph. 

Indicator displays a `symbol` along with text which is different from caption and subtitle. Images like logos can be used in indicator instead of symbols. Indicator has properties such as `Symbol`, `Text`, `TextSpacing`, `TextAngle`, `Location` and `Font`. 


### Location

Using `location` option, you can set the `X` and `Y` position of caption text.

### Font

Using `font` property, you can customize `font color`, `font family`, `font style`, `font weight`, `opacity`, `size` options.

### Symbol

* Using `symbol` settings, you can customize the following symbol properties.

	* You can customize the symbol border properties border `color` and border `width` using border   	
	  settings.

	* You can specify the color of the symbol using `color` property.

	* You can set the `shape` of the symbol using shape property.

	* Instead of setting shape for symbol, you can use image also. To use image as symbol, you need to   set `image url` for symbol.

	* You can customize the size of the indicator symbol using `width` and `height` properties of    
	  indicator’s symbol size settings.

	* To customize the `opacity` of the indicator symbol, you can use the opacity property of the   
	  symbol.

{% highlight cshtml %}

@(Html.EJ().BulletGraph("Bullets").QuantitativeScaleSettings( scale=>

	scale.Location( loc=> loc.x(110).y(200))

	.Minimum(0)

	.Maximum(5)

	.Interval(1)

	.LabelSettings(ls=>ls.LabelPrefix("$").LabelSuffix("K"))

	.FeatureMeasure(measure=>measure.Value(4).ComparativeMeasureValue(3.5)))

	.Height(700)

	.Width(600)

	.CaptionSettings(cs=>

	cs.Indicator(indicator=>

	indicator.Visible(true)

	.Text("+ $0.5 K")

	.Location(loc=>loc.x(15).y(240))

	.Symbol(symbol=>

	  symbol.Shape(SymbolShape.Triangle)

	  .Color("green")

	  .Border(border=>border.Width(1).Color("green")

	  )))



	.SubTitle(subtitle=>

	subtitle.Text("Subtitle")

	.Location(loc=>loc.x(20).y(225))

	.Font(font=>font.FontStyle("italic").FontSize("16px")))

	.Text("Revenue YTD")

	.Location(loc=>loc.y(210))

	.Font(font=>font.FontStyle("bold").FontColor(System.Drawing.Color.Gray).FontSize("14px")))

	)

{% endhighlight %}

The following screenshot displays a **bullet graph** with indicator.

![](Bullet-Graph-Caption_images/Bullet-Graph-Caption_img3.png)

Bullet Graph with indicator
{:.caption}

## Trim

The title, subtitle and indicator text can be overlapped to the scale group. You can avoid the overlapped text by using the `EnableTrim` property of the CaptionSettings. The default value of the EnableTrim is true. 
{% highlight html %}

@(Html.EJ().BulletGraph("BulletGraph1")

.CaptionSettings(title=>title.Text("Bullet Graph Title").EnableTrim (true))

)

{% endhighlight %}

The following screenshot displays the BulletGraph with Trim.

![](Bullet-Graph-Caption_images/Bullet-Graph-Caption_img4.png)

BulletGraph with trim
{:.caption}

## Text Placement

All the caption group elements (caption, subtitle, and indicator) in the **Bullet Graph** support text positioning by using the property **TextPosition** available in all caption group elements. The properties, **TextAlignment** and **TextAnchor** are used to customize text placement further.

### Text Position

The property `TextPosition`, is used to position the text at the `top`, `bottom`, `left`, and `right` side of the quantitative scale. The default value of this property is **Float**. By default, text can be placed at any desired location by using the Location property. 
{% highlight cshtml %}

@(Html.EJ().BulletGraph("BulletGraph1").Width(650).Height(150).Value(8).ComparativeMeasureValue(5)

    .CaptionSettings(title=>title.Text("Bullet Graph Title")

	.TextPosition(BulletTextPosition.Top)

	.Font(font=>

	font.FontSize("20px")

	.FontWeight("bold")

	))

    .QuantitativeScaleSettings(scale=>scale.Location(loc=>loc.x(120).y(40)))

)

{% endhighlight %}

The following screenshot displays the **Bullet Graph** with the title positioned above.

![](Bullet-Graph-Caption_images/Bullet-Graph-Caption_img5.png)

Bullet Graph with title automatically positioned above the scale
{:.caption}


### Text Alignment

**Alignment** of text at different positions with respect to scale can be customized by using the `TextAlignment` property. Text can be aligned in the `near`, `center`, and `far` locations of the scale. Text alignment depends upon TextPosition property and is not applicable when the value of the `TextPosition` property is **Float**. The default value of the `TextAlignment` property is **Near**. 
{% highlight cshtml %}

@(Html.EJ().BulletGraph("BulletGraph1").Width(650).Height(150).Value(8).ComparativeMeasureValue(5)

    .CaptionSettings(title=>title.Text("Revenue")

	.TextPosition(BulletTextPosition.Left)

	.TextAnchor(BulletTextAnchor.Middle)

	.Font(font=>

	font.FontSize("16px")

	.FontWeight("bold")

	)

	.SubTitle(subtitle=>subtitle.Text("$ in thousands")

	.TextPosition(BulletTextPosition.Left)

	.TextAlignment(BulletTextAlignment.Center)

	.Font(font=>

	font.FontSize("12px")

	.FontWeight("bold")

	)))

    .QuantitativeScaleSettings(scale=>scale.Location(loc=>loc.x(120).y(40)))

)

{% endhighlight %}

The following screenshot displays the Bullet Graph with the title and subtitle at different alignments.

![](Bullet-Graph-Caption_images/Bullet-Graph-Caption_img6.png)

Bullet graph with the title aligned at near and sub title aligned at center positions
{:.caption}

### Text Anchor

Text elements aligned at the same position are anchored by using the TextAnchor property. These can be anchored at the Start, Middle, and End. The default value of this property is Start and applicable only when two or more text elements are aligned at the same position. 

{% highlight cshtml %}

@(Html.EJ().BulletGraph("BulletGraph1").Width(650).Height(150).Value(8).ComparativeMeasureValue(5)

	.CaptionSettings(title=>title.Text("Revenue")

	.TextPosition(BulletTextPosition.Left)

	.TextAnchor(BulletTextAnchor.Middle)

	.Font(font=>

	font.FontSize("16px")

	.FontWeight("bold")

	)

	.SubTitle(subtitle=>subtitle.Text("$ in thousands")

	.TextPosition(BulletTextPosition.Left)

	.TextAlignment(BulletTextAlignment.Center)

	.Font(font=>

	font.FontSize("12px")

	.FontWeight("bold")

	)))

    .QuantitativeScaleSettings(scale=>scale.Location(loc=>loc.x(120).y(40)))

)

{% endhighlight %}

![](Bullet-Graph-Caption_images/Bullet-Graph-Caption_img7.png)

Bullet Graph with title text anchored at the center with respect to subtitle text
{:.caption}

### Padding

The space required between text and quantitative scale is customized by using the Padding property. The default value of this property is 5 and not applicable when the value of the TextPosition property is Float. 
{% highlight cshtml %}

@(Html.EJ().BulletGraph("BulletGraph1").Width(650).Height(150).Value(8).ComparativeMeasureValue(5)

	.CaptionSettings(title=>title.Text("Profit in %")

	.TextPosition(BulletTextPosition.Left)

	.TextAlignment(BulletTextAlignment.Center)

	.Padding(10)

	.Font(font=>

	font.FontSize("16px")

	.FontWeight("bold")

	))

	.QuantitativeScaleSettings(scale=>scale.Location(loc=>loc.x(120).y(40)))

	)

{% endhighlight %}

![](Bullet-Graph-Caption_images/Bullet-Graph-Caption_img8.png)

Bullet graph with 10 pixel padding between the title text and quantitative scale
{:.caption}
