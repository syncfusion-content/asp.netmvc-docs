---
layout: post
title: How-to-attach-a-Template-to-a-Word-document
description: how to attach a template to a word document?
platform: universal-classic
control: Control Name undefined
documentation: ug
---

### How to attach a Template to a Word document?

You can use the AttachedTemplate property to attach a template to a Word document using DocIO. The following code example illustrates this.

{% highlight c# %}
//Sets the location of the template.document.AttachedTemplate.
Path = @"D:\Test.dot";

//Sets the UpdateStylesOnOpen to ‘true’to automatically update the styles from the attached template each time the document is opened with Microsoft Worddocument.
UpdateStylesOnOpen = true;
{% endhighlight %}
{% highlight vbnet %}
'Sets the location of the template document.document.AttachedTemplate.
Path = @"D:\Test.dot"
'Sets the UpdateStylesOnOpen to ‘true’to automatically update the styles from the attached template each time the document is opened with Microsoft Worddocument.
UpdateStylesOnOpen = True
{% endhighlight %}


