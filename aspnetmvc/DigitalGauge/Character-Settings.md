---
layout: post
title: Character Settings | DigitalGauge | ASP.NET MVC | Syncfusion
description: character settings
platform: ejmvc
control: DigitalGauge
documentation: ug
---

# Character Settings

## Appearance

The opacity of the character is adjustable with the help of `opacity` property. The space between two characters are adjusted with `spacing` property as like in the segment settings.



{% highlight CSHTML %}

@* For Digital Gauge rendering *@

@(Html.EJ().DigitalGauge("DigitalGauge1")

.Width(800)

.Value("Syncfusion")

.Items(it=>

{ it.CharacterSettings(cs => cs

// For setting character opacity

.Opacity(0.3)

// For setting character spacing

.Spacing(3)).Add();

}))


{% endhighlight %}

Execute the above code examples to render the **DigitalGauge** as follows.


![](Character-Settings_images/Character-Settings_img1.png)

Digital Gauge control with character setting
{:.caption}



## Count and Type

* The number of text to be displayed can be limited by the attribute called `count`. In **Digital Gauge** five different `types` of characters are supported. They are as follows, 
1. EightCrossEightDotMatrix
2. SevenSegment
3. FourteenSegment
4. SixteenSegment 
5. EightCrossEightSquareMatrix.


{% highlight CSHTML %}

@(Html.EJ().DigitalGauge("DigitalGauge1")

.Width(800)

.Value("123456789")

.Items(it=>

{ it.CharacterSettings(cs => cs

// For setting character count

.Count(10)

// For setting character spacing

.Spacing(10)

// For setting character type

.Type(CharacterType.SevenSegment))

.SegmentSettings(ss=>

// For setting segment length

ss.Length(8)

// For setting segment width

.Width(1)).Add();

}))

{% endhighlight %}


Execute the above code examples to render the **DigitalGauge** as follows.



![](Character-Settings_images/Character-Settings_img2.png)

Digital Gauge control with character type as seven segment
{:.caption}

## Text Positioning

The text in the **DigitalGauge** is positioned with position object. This object contains two attributes such as `x` and `y`. The `x` variable positions the text in the horizontal axis and the `y` variable positions the text in the vertical axis.

{% highlight CSHTML %}

@* For Digital Gauge rendering *@

@(Html.EJ().DigitalGauge("DigitalGauge1")

// For setting Width and Height

.Width(800).Height(300)

.Frame(fr=>fr

// For setting frame background image

.BackgroundImageUrl("../Content/images/gauge/Board1.jpg"))

.Items(it=> { it.Value("YELLOW")

// For setting segment color

.SegmentSettings(cs=>cs.Color("Yellow"))

.Position(position=>position

// For setting horizontal position

.X(80)

// For setting Vertical position

.Y(10)).Add();}))


{% endhighlight %}


Execute the above code examples to render the **DigitalGauge** as follows.



![](Character-Settings_images/Character-Settings_img3.png)

Digital Gauge control with position text based on the background image
{:.caption}

## Shadow Effects

* You can add the shadow effects for text using following properties.

    * You can enable/disable the blurring effect for the shadows of the text using `shadow blur` property.

    * You can specify the color of the text shadow using `shadow color` property.

    * You can set the `x-offset` value for the shadow of the text, indicating the location where it needs to be displayed.

    * You can set the `y-offset` value for the shadow of the text, indicating the location where it needs to be displayed.

{% highlight CSHTML %}

@* For Digital Gauge rendering*@

@(Html.EJ().DigitalGauge("DigitalGauge1")

// For setting Width and Height

.Width(800)

.Items(it=> { it.Value("WELCOME")

// For setting Shadow blur

.ShadowBlur(20)



// For setting Shadow color  .ShadowColor("Yellow")



// For setting Shadow horizontal offset     .ShadowOffsetX(15)



// For setting Shadow vertical offset .ShadowOffsetY(15)

// For setting segment length and width

.SegmentSettings(cs=>



cs.Length(3) .Width(3)).Add();}))

{% endhighlight %}


Execute the above code examples to render the **DigitalGauge** as follows.



![](Character-Settings_images/Character-Settings_img4.png)

Digital Gauge control with shadow option
{:.caption}


## Font Customization

You can customize the **font** of the text as per your requirement. To customize the font, you have to set `enableCustomFont`. Following font customization options are available.

**Font-family**- used to set the font-family of the text.

**Font-style**- used to set the font-style of the text.

**Font-size**- used to set the font-size of the text.


{% highlight CSHTML %}

@* For Digital Gauge rendering *@

@(Html.EJ().DigitalGauge("DigitalGauge1")

.Width(800)

.Value("Syncfusion")

.Items(it=>

{ it.CharacterSettings(cs => cs

// For setting character opacity

.EnableCustomFont(true)

// For setting character spacing

.Font(ft=>ft.FontFamily("Segou").FontStyle(FontStyle.Bold).Size("18px")) ).Add();

}))


{% endhighlight %}




