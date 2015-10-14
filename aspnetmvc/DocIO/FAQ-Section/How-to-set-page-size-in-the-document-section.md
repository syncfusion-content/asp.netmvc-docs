---
layout: post
title: How to set page size in the document section | DocIo | ASP.NET MVC | Syncfusion
description: how to set page size in the document section?
platform: ejmvc
control: DocIo
documentation: ug
---

# How to set page size in the document section?

The page size of the document section is set by using the PageSize property of the PageSetup class. The following code example illustrates how to set this property.
{% tabs %}

{% highlight C# %}
document.Sections[0].PageSetup.PageSize = PageSize.B6;</td></tr>
{% endhighlight %}
{% highlight VB%}
document.Sections(0).PageSetup.PageSize = PageSize.B6</td></tr>
{% endhighlight %}

{% endtabs %} 
