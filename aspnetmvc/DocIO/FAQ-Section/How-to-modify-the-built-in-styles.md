---
layout: post
title: How-to-modify-the-built-in-styles
description: how to modify the built-in styles?
platform: universal-classic
control: Control Name undefined
documentation: ug
---

### How to modify the built-in styles?

You can use the CreateBuiltinStyle method of the Style class to override the built-in styles.

The following code illustrates how to modify the Heading1 style.

{% highlight c# %}
Style style = Style.CreateBuiltinStyle(BuiltinStyle.Heading1, doc) as Style;
style.CharacterFormat.Italic = true;
style.CharacterFormat.UnderlineStyle = UnderlineStyle.DotDash;
doc.Styles.Add(style);para.ApplyStyle(style.Name);
{% endhighlight %}
{% highlight vbnet %}
Dim style As Style = TryCast(Style.CreateBuiltinStyle(BuiltinStyle.Heading1, doc), Style)
style.CharacterFormat.Italic = True
style.CharacterFormat.UnderlineStyle = UnderlineStyle.DotDash
doc.Styles.Add(style)para.ApplyStyle(style.Name)
{% endhighlight %}


