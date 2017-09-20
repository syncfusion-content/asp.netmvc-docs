---
layout: post
title: Localization | Captcha  | ASP.NET MVC | Syncfusion
description:  Localization in Captcha control for Syncfusion ASP.NET MVC
platform: ejmvc
control: Captcha
documentation: ug
---
# Localization

The Captcha provides option to localize the place holder string to a particular local language. By default, the Captcha place holder text will use the US English (en-US) as its language.

N> The culture name has to be specified in a standard format such as [Language Code]-[County/Region Code].

To localize the Captcha's strings with your own localization, copy the default language informations and localize the strings in the values column. For example, to localize the Captcha in French language (“fr-FR”).

{% highlight javascript %}

    ej.Captcha.Locale["fr-FR"] =  {
            placeHolderText: "Entrer le code indiqué",
          };
    
{% endhighlight %}

Set the locale property of the Captcha to the new language.


{% highlight html %}

    @(Html.EJ().Captcha("captcha").EnableAutoValidation(true).RequestMapper("Refresh").Locale("fr-FR"))

{% endhighlight %}

![](Localization_images/Locale.jpg)
