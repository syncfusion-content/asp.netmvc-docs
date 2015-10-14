---
layout: post
title: Tooltip | CircularGauge | ASP.NET MVC | Syncfusion
description: tooltip
platform: ejmvc
control: CircularGauge
documentation: ug
---

# Tooltip

* Tooltip feature has been added to the Circular Gauge. Circular Gauge has several elements such as pointers, label, customLabel, scales, etc.  
* There is a need for Tooltip feature in the Circular Gauge control because whenever the text hides or overrides with other gauge elements, it may not be fully visible. For resolving those problems Tooltip feature has been implemented in the Circular Gauge control.

## Default Tooltip

* Tooltip has three attributes in it. The first two attributes such as showLabelTooltip and showCustomLabelTooltip are for enabling the Tooltip for label as well as custom label in default appearance. 
* ShowLabelTooltip is to enable the Tooltip for labels and showCustomLabelTooltip is for enabling the Tooltip option for customLabels.



{% highlight CSHTML %}
@(Html.EJ().CircularGauge(“circularGaugeTooltip”)

//Defines the tooltip object.
.Tooltip(ttp=>ttp

// Enables the label tooltip.
.ShowLabelTooltip(true)

// Enables the custom label tooltip.
.ShowCustomLabelTooltip(true))

//Customizes the scale options.
.Scales(SC =>{SC.Radius(130).ShowLabels(true)

//Customizes the custom label options.
.CustomLabels(cl => {cl.Value(“0 9 5 3 4 5”).Font(f =>f.Size("20px").FontFamily("Arial").FontStyle("bold")).Position(pos => pos.X(180).Y(200))
.Add();})

//Customizes the pointers options.
.Pointers(PO =>{PO.Value(60).Length(90)
.Add();})
.Add();
})
)
{% endhighlight %}
{% highlight c# %}
public partial class CircularGaugeController : Controller
{
	//// GET: /ToolTip/
	public ActionResult Tooltip()
	{
		return View();
	}
}


{% endhighlight %}

Execute the above code to render the following output.

![](Tooltip_images/Tooltip_img1.png)

Gauge with Default ToolTip
{:.caption}

## Tooltip Template

In Tooltip option, you can customize the Tooltip window by adding the tooltip template on that page with the help of API TemplateID. Refer to the following code example to know more about Tooltip template.


{% highlight CSHTML %}

@(Html.EJ().CircularGauge(“circularGaugeTooltip”)
//Defines the tooltip object.
.Tooltip(ttp=>ttp

// Enables the label tooltip.
.ShowLabelTooltip(true)

// Enables the custom label tooltip.
.ShowCustomLabelTooltip(true)

// Enables the tooltip template ID.
.TemplateID(“Tooltip”))

// Customizes the scale options.
.Scales(SC =>{SC.Radius(130).ShowLabels(true)

// Customizes the custom label options.
.CustomLabels(cl => {cl.Value(“0 9 5 3 4 5”).Font(f =>f.Size("20px").FontFamily("Arial").FontStyle("bold")).Position(pos => pos.X(180).Y(200)).Add();})

// Customizes the pointers options..pointers(PO =>{PO.Value(60).Length(90).Add();})
.Add();
})
)
{% endhighlight %}
{% highlight c# %}
public partial class CircularGaugeController : Controller
{
	// GET: /ToolTip/
	public ActionResult Tooltip()
	{
		return View();
	}
}


{% endhighlight %}

Execute the above code to render the following output.



![](Tooltip_images/Tooltip_img2.png)

Circular gauge with tooltip template
{:.caption}


