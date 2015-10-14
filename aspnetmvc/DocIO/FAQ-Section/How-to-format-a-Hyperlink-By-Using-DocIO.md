---
layout: post
title: How to format a Hyperlink By Using DocIO | DocIO | ASP.NET MVC | Syncfusion
description: how to format a hyperlink by using docio?
platform: ejmvc
control: DocIO
documentation: ug
---

# How to format a Hyperlink By Using DocIO?

## Each field contains:

* Field defines field properties, not formatting.
* FieldMark or FieldSeparator mark.
* Text of the Field, that is, WTextTange.
* FieldMark or FieldEnd mark.

To set CharacterFormat for the field text, you have to find WTextRange between the field separator and field text.

The following code example illustrates how to format the hyperlink text.
{% tabs %}
{% highlight C# %}
doc.LastParagraph.AppendHyperlink("www.google.com", "google",HyperlinkType.WebLink);
 for (int i = 0, cnt = doc.LastParagraph.Items.Count; i < cnt; i++)
 {
     if (doc.LastParagraph.Items[i] is WTextRange)
     {
         WTextRange text = doc.LastParagraph.Items[i] as WTextRange;
         text.CharacterFormat.FontSize = 33f;
     }
 }
{% endhighlight %}
{% highlight VB%}
doc.LastParagraph.AppendHyperlink("www.google.com", "google", HyperlinkType.WebLink)
Dim i As Integer = 0, cnt As Integer = doc.LastParagraph.Items.CountWhile i < cnt
If TypeOf doc.LastParagraph.Items(i) Is WTextRange
 Then
     Dim text As WTextRange = TryCast(doc.LastParagraph.Items(i), WTextRange)
     text.CharacterFormat.FontSize = 33.0F
End If
i += 1
End While
{% endhighlight %}
{% endtabs %} 


