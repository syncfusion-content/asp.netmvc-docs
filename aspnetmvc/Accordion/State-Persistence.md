---
layout: post
title: State Persistence in ASP.NET MVC Accordion | Syncfusion
description: Learn here all about state persistence in Syncfusion Essential ASP.NET MVC Accordion control, its elements, and more.
platform: ejmvc
control: Accordion 
documentation: ug
---

# State Persistence in ASP.NET MVC Accordion

Accordion widget can store the model value in the browser cookies and on every time after initial rendering, the control get the model from the cookie only. Using EnablePersistence property you can store the model value in cookies. Thus when any changes are made dynamically then those values are updated in cookie. On refreshing the page the past state of the Accordion control is maintained in cookie and control is rendered from it.

## Configure state persistence of Accordion panel

The following code explains to enable state maintenance for Accordion.

{% highlight CSHTML %}

// In the View page, configure Accordion with corresponding data and enable the state persistence.

<div style="width: 400px">

@{Html.EJ().Accordion("accordion").Items(data =>

	{

		data.Add().Text("Essential Chart").ContentTemplate(@<div>

			Essential Chart for ASP.NET MVC is a visually stunning, high-performance charting component that is easy to use. It includes 35 chart types ranging from simple column charts to specialized financial charts. The charts are highly customizable and have a powerful data model that makes data binding simple.

		</div>);

		data.Add().Text("Essential Schedule").ContentTemplate(@<div>

			Essential Schedule for ASP.NET MVC is an Outlook Calendar-like scheduler control that lets you add rich scheduling capabilities to your web applications. It includes an advanced set of features including data binding, multiple resource views, rich interactivity, support for AJAX, client-side events, and much more.

		</div>);

		data.Add().Text("Essential Grid").ContentTemplate(@<div>

			Essential Grid for ASP.NET MVC is a feature-rich control that provides extensive appearance customization options with support for grouped records. With Essential Grid for ASP.NET MVC, you can create a grid with a highly customizable look and feel. This grid is very useful for generating complex grid-based reports with rich formatting. It supports paging, sorting, grouping, filtering, and editing features. It also supports a JSON mode in which you can handle all the operations like paging and sorting. The performance of these operations in the JSON mode will be much faster than if the grid were to handle them. Essential Grid generates clean HTML in compliance with XHTML 1.0. It supports any kind of IEnumerable data source. It uses LINQ data retrieval techniques for handling data sources, and offers high performance.</div>);

	}).EnablePersistence(true).Render();}

</div>

{% endhighlight %}

Output after page refresh maintaining the previous state of Accordion widget is as follows.



   ![ASP.NET MVC State Persistence](State-Persistence_images/aspnet-mvc-state-persistence.png)





1. Accordion Selected Item changed

   ![ASP.NET MVC Configure State Persistence](State-Persistence_images/aspnet-mvc-configure-state-persistence.png)




2. Accordion state persisted after page refresh
