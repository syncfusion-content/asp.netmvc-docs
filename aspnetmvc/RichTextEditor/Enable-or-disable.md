---
layout: post
title: Enable-or-disable
description: enable or disable
platform: ejmvc
control: RichTextEditor
documentation: ug
---

# Enable or disable

You can enable or disable the tool items that are available in the RTE toolbar. Intermittently, it is not possible to allow some tool item actions in the editing area. To avoid mistakes in such a situation, you can disable the unnecessary tool items. Later, you can enable the disabled tool items, and when you are not using the images in your blog, you can disable the image tool item by using the “disableToolbarItem” method. The following example illustrates how to disable the “image” tool. 

You can also enable or disable the entire RTE control by using “enabled” property.

1. Add the following code in your CSHTML page.

{% highlight js %}

	@*Add the following code in your view page.*@
	@{Html.EJ().RTE("rteSample").Width("850px").ContentTemplate(@<p></p>).Render();}

{% endhighlight %}

{% highlight js %}

	\\ Add the following code in your script section to render RTE with disabled image
	
	iconvar rteobj = $("#rteSample").data("ejRTE");
	rteobj.disableToolbarItem("rteSampleimage");

{% endhighlight %}


The following screenshot displays the output.

![](Enable-or-disable_images/Enable-or-disable_img1.png)

You can also enable or disable the entire RTE control by using “enabled” property.

1. Add the following code in your CSHTML page.

{% highlight js %}

	@*Add the following code in your view page.*@

    @{Html.EJ().RTE("rteSample").Width("850px").ContentTemplate(@<p></p>).Enabled(false).Render(); }

{% endhighlight %}

The following screenshot displays the output.

![](Enable-or-disable_images/Enable-or-disable_img2.png)