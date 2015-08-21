---
layout: post
title: How-to-set-page-size-in-the-document-section
description: how to set page size in the document section?
platform: universal-classic
control: Control Name undefined
documentation: ug
---

### How to set page size in the document section?

The page size of the document section is set by using the PageSize property of the PageSetup class. The following code example illustrates how to set this property.

{% highlight c# %}
document.Sections[0].PageSetup.PageSize = PageSize.B6;</td></tr>
{% endhighlight %}
{% highlight vbnet %}
document.Sections(0).PageSetup.PageSize = PageSize.B6</td></tr>
{% endhighlight %}


