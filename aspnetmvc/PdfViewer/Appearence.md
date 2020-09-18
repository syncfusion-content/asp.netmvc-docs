---
layout: post
title: Altering appearance of Syncfusion Essential ASP.NET MVC PDF viewer.
description: Learn how to apply themes to the Syncfusion Essential ASP.NET MVC (jquery) PDF viewer to match the theme of your application.
platform: ejmvc
control: PDF viewer
documentation: ug
---

# Appearance in PDF Viewer

You can apply themes to the PDF viewer to match the themes of your application.

The following are the available built-in themes:

* Flat-azure
* Flat-lime
* Flat-lime-dark
* Flat-saffron
* Flat-saffron-dark
* Gradient-azure
* Gradient-azure-dark
* Gradient-lime
* Gradient-lime-dark
* Gradient-saffron
* Gradient-saffron-dark
* Bootstrap
* High-contrast-01
* High-contrast-02
* Material
* Office-365

By default, ‘flat-azure’ theme is applied to PDF viewer. You can change the theme by changing the stylesheet reference. Applying ‘gradient-saffron’ theme to PDF viewer is illustrated as follows.

{% highlight javascript %}
<!—style sheet for ‘gradient-saffron’ theme.-->
<link href="https://cdn.syncfusion.com/16.1.0.24/js/web/gradient-saffron/ej.web.all.min.css" rel="stylesheet" />
<script src="https://cdn.syncfusion.com/js/assets/external/jquery-3.1.1.min.js"></script>
<script src="https://cdn.syncfusion.com/16.1.0.24/js/web/ej.web.all.min.js"></script>
{% endhighlight %}

The following screenshot shows the PDF viewer in ‘gradient-saffron’ theme:

![PDF Viewer Appearance](Appearance_images/Appearance_img1.png)

