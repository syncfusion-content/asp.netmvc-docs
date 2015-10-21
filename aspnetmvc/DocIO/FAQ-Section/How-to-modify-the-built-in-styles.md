---
layout: post
title: How to modify the built in styles | DocIo | ASP.NET MVC | Syncfusion
description: how to modify the built-in styles?
platform: ejmvc
control: DocIo
documentation: ug
---

# How to modify the built-in styles?

You can use the CreateBuiltinStyle method of the Style class to override the built-in styles.

The following code illustrates how to modify the Heading1 style.
{% tabs %}

{% highlight C# %}
Style style = Style.CreateBuiltinStyle(BuiltinStyle.Heading1, doc) as Style;
style.CharacterFormat.Italic = true;
style.CharacterFormat.UnderlineStyle = UnderlineStyle.DotDash;
doc.Styles.Add(style);para.ApplyStyle(style.Name);
{% endhighlight %}
{% highlight VB %}
Dim style As Style = TryCast(Style.CreateBuiltinStyle(BuiltinStyle.Heading1, doc), Style)
style.CharacterFormat.Italic = Truestyle.CharacterFormat.UnderlineStyle = UnderlineStyle.DotDashdoc.Styles.Add(style)
para.ApplyStyle(style.Name)
{% endhighlight  %}

{% endtabs %} 
