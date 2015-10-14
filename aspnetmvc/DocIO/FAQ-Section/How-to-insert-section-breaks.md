---
layout: post
title: How to insert section breaks 
description: how to insert section breaks?
platform: ejmvc
control: DocIO
documentation: ug
---

# How to insert section breaks?

Essential DocIO provides direct support to insert section breaks to Word documents. You can insert a section break to a Word document by using the InsertSectionBreak method of WParagraph class.

The following code example illustrates how to insert a section break.

{% highlight c# %}
//Inserts a section break.WSection section = paragraph.InsertSectionBreak();
//Inserts a section break of the specified type.
WSection section = paragraph.InsertSectionBreak(SectionBreakCode.EvenPage);
{% endhighlight  %}
{% highlight vbnet %}
'Inserts a section break.Dim section As WSection = paragraph.InsertSectionBreak()
'Inserts a section break of the specified type.
Dim section As WSection = paragraph.InsertSectionBreak(SectionBreakCode.EvenPage)
{% endhighlight  %}


