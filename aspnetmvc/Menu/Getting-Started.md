---
layout: post
title: Getting Started | Menu | ASP.NET MVC | Syncfusion
description: getting started 
platform: ejmvc
control: Menu
documentation: ug
---

# Getting Started 

This section explains briefly about how to create a Menu control in your application with ASP.NET MVC 

## Create Syncfusion Menu in MVC

The Essential ASP.NET MVC Menu control supports displaying a Menu out of list items. The Menu is based on parent and child elements hierarchy, where the child items are rendered as the sub-menu items .The Menu control can also render with local and remote data source. The following section explains you on how to customize the Menu control for a website. 

The following screenshot illustrates the appearance of Syncfusion’s website Menu.

![](Getting-Started_images/Getting-Started_img1.png)

Syncfusion Menu
{:.caption}

The Menu items in the above screenshot allow you to navigate through multiple menus in a page and select an item. It has a hierarchical structure with sub menus. 

## Create a Menu

Essential ASP.NET MVC Menu widget basically renders with built-in features like keyboard navigation, show and hides Menu items with animations and flexible API’s. Refer the following guidelines to render Menu control with Local data source value.

1. You can create a MVC Project and add the necessary Dll’s and scripts using the [MVC-Getting Started](http://help.syncfusion.com/aspnetmvc/menu/getting-started) Documentation.
2. Add the below code in your view page to add the necessary CSS and script files

   ~~~ cshtml

	<head>

	<link href="http://cdn.syncfusion.com/13.1.0.21/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />



		<!--Scripts-->

		<script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js"></script>



		<script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js"></script>



		<script src="http://cdn.syncfusion.com/13.1.0.21/js/web/ej.web.all.min.js"> </script>

	</head>

   ~~~
   

3. Add the following code example to the corresponding view page for Menu rendering.

   ~~~ cshtml

	@Html.EJ().Menu("SyncfusionProducts")

   ~~~
   

4. Execute the above code to render Empty Menu bar.

![](Getting-Started_images/Getting-Started_img2.png)

Essential ASP.NET MVC Menu without menu item
{:.caption}

## Configure Parent Menu items

Each Menu consists of a list of Menu items with list of sub level Menu item. Refer the following guidelines to initialize the root level elements of Menu control with Remote data source value. RootLevelItems data service is created to define the root level Menu items, sub items and InnerItems data services to initialize the sub level and inner sub levels and both can be referred from the following service location. In Menu Widgets mention the RootLevelItem Data Source in the Datasource property. Elements’s properties like Id, Text, URL, and Parent Id can be defined using our menu fields and it explained briefly under the concept and features of Menu control.

[http://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/](http://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/)



To navigate the clicked Menu item to a specific URL, define the navigation URL to each Menu item.

Initialize the Menu with data source value as follows. 

{% highlight CSHTML %}

      @Html.EJ().Menu("syncfusionProducts").Items(items =>
               {
                   items.Add().Url("#").Id("Products").Text("Products");
                   items.Add().Url("").Text("Support");
                   items.Add().Url("").Id("Purchase").Text("Purchase");
                   items.Add().Url("").Id("Downloads").Text("Downloads");
                   items.Add().Id("Resources").Url("").Text("Resources");
                   items.Add().Url("").Id("Company").Text("Company");
               })
			   
{% endhighlight %}

Execute the above code to display the Root level Menu items.



![](Getting-Started_images/Getting-Started_img3.png)

Essential ASP.NET MVC Menu without sub menu item
{:.caption}

## Initialize sub-level Menu items

Each Menu items consist of list of sub level Menu items. Refer the following guidelines to initialize the sub level items of Menu control. The ParentId field property maps root level Menu item to its sub level Menu item. In Menu Widgets mention the RootLevelItems and SubLevelItems Data Source in the Datasource property. The Child field property is used to define sub level Menu items of parent Menu item.							

The following code example explains the initialization of first level sub menu items of Menu control.

{% highlight CSHTML %}

          @Html.EJ().Menu("syncfusionProducts").Items(items =>
               {
                   items.Add().Url("#").Id("Products").Text("Products").Children(child =>
                       {
                           child.Add().Url("").Text("ASP.NET");
                           child.Add().Url("").Text("ASP.NET MVC");
                           child.Add().Url("").Text("Mobile MVC");
                           child.Add().Url("").Text("Silverlight");
                           child.Add().Url("").Text("Windows Forms");
                           child.Add().Url("").Text("Windows Phone");
                           child.Add().Url("").Text("WinRT (XMAL)");
                           child.Add().Url("").Text("WPF");
                           child.Add().Url("").Text("Orubase Studio");
                           child.Add().Url("").Text("Metro Studio");
                           child.Add().Url("").Text("What's New");
                       });
                   items.Add().Url("").Text("Support").Children(child =>
                       {
                           child.Add().Url("").Text("Direct-Trac Support");
                           child.Add().Url("").Text("Community Forums");
                           child.Add().Url("").Text("Knowledge Base");
                           child.Add().Url("").Text("Online Documentation");
                           child.Add().Url("").Text("Services");
                       });
                   items.Add().Url("").Id("Purchase").Text("Purchase");
                   items.Add().Url("").Id("Downloads").Text("Downloads").Children(child =>
                       {
                           child.Add().Url("").Text("Evaluation");
                           child.Add().Url("").Text("Free E-Books");
                           child.Add().Url("").Text("Metro Studio");
                           child.Add().Url("").Text("Latest Version");
                           child.Add().Url("").Text("Version History");
                       });
                   items.Add().Id("Resources").Url("").Text("Resources").Children(child =>
                      {
                          child.Add().Url("").Text("Technology Resource Portal");
                          child.Add().Url("").Text("Case Studies");
                          child.Add().Url("").Text("Bouchers & Datasheets");
                          child.Add().Url("").Text("FAQ");
                      });
                   items.Add().Url("").Id("Company").Text("Company").Children(child =>
                   {
                       child.Add().Url("").Text("About Us");
                       child.Add().Url("").Text("Company Blog");
                       child.Add().Url("").Text("Technical Blog");
                       child.Add().Url("").Text("Newsletter");
                       child.Add().Url("").Text("Partners");
                       child.Add().Url("").Text("Locations");
                       child.Add().Url("").Text("Contact Us");
                       child.Add().Url("").Text("Careers");
                   });

               })
{% endhighlight %}

Execute the above code to render the following output.

![](Getting-Started_images/Getting-Started_img4.png)

Essential ASP.NET MVC Menu with sub menu item
{:.caption}

## Define multiple level Menu items

You can render sub menu item to multiple level in Menu control. In Menu Widgets, mention the InnerItems Data Source in the Datasource property. The Child field property is used to define the sub level Menu item of parent Menu. Specify the ParentId value to render sub level Menu item for the Menu item. Each Level Menu item have Child field to define the child level Menu item. 

The following code example explains the initialization of multiple level sub menu items.

{% highlight CSHTML %}
      
	   @Html.EJ().Menu("syncfusionProducts").Items(items =>
               {
                   items.Add().Url("#").Id("Products").Text("Products").Children(child =>
                       {
                           child.Add().Url("").Text("ASP.NET");
                           child.Add().Url("").Text("ASP.NET MVC");
                           child.Add().Url("").Text("Mobile MVC");
                           child.Add().Url("").Text("Silverlight");
                           child.Add().Url("").Text("Windows Forms");
                           child.Add().Url("").Text("Windows Phone");
                           child.Add().Url("").Text("WinRT (XMAL)");
                           child.Add().Url("").Text("WPF");
                           child.Add().Url("").Text("Orubase Studio");
                           child.Add().Url("").Text("Metro Studio");
                           child.Add().Url("").Text("What's New").Children(child1 =>
                               {
                                   child1.Add().Url("").Text("ASP.NET");
                                   child1.Add().Url("").Text("WPF");
                                   child1.Add().Url("").Text("Silverlight");
                                   child1.Add().Url("").Text("Windows Forms");
                                   child1.Add().Url("").Text("Windows Phone");
                                   child1.Add().Url("").Text("ASP.NET MVC");
                                   child1.Add().Url("").Text("ASP.NET");
                               });
                       });
                   items.Add().Url("").Text("Support").Children(child =>
                       {
                           child.Add().Url("").Text("Direct-Trac Support");
                           child.Add().Url("").Text("Community Forums");
                           child.Add().Url("").Text("Knowledge Base");
                           child.Add().Url("").Text("Online Documentation");
                           child.Add().Url("").Text("Services").Children(child1 =>
                               {
                                   child1.Add().Url("").Text("Consulting");
                                   child1.Add().Url("").Text("Training");
                               });
                       });
                   items.Add().Url("").Id("Purchase").Text("Purchase");
                   items.Add().Url("").Id("Downloads").Text("Downloads").Children(child =>
                       {
                           child.Add().Url("").Text("Evaluation");
                           child.Add().Url("").Text("Free E-Books");
                           child.Add().Url("").Text("Metro Studio");
                           child.Add().Url("").Text("Latest Version");
                           child.Add().Url("").Text("Version History");
                       });
                   items.Add().Id("Resources").Url("").Text("Resources").Children(child =>
                      {
                          child.Add().Url("").Text("Technology Resource Portal").Children(child1 =>
                                      {
                                          child1.Add().Url("").Text("E-Books");
                                          child1.Add().Url("").Text("White Papers");
                                      });
                          child.Add().Url("").Text("Case Studies");
                          child.Add().Url("").Text("Bouchers & Datasheets");
                          child.Add().Url("").Text("FAQ");
                      });
                   items.Add().Url("").Id("Company").Text("Company").Children(child =>
                   {
                       child.Add().Url("").Text("About Us").Children(child1 =>
                           {
                               child1.Add().Url("").Text("More About Us");
                               child1.Add().Url("").Text("Management");
                               child1.Add().Url("").Text("News & Events");
                               child1.Add().Url("").Text("Customer Quotes");
                               child1.Add().Url("").Text("Customer Lists");
                               child1.Add().Url("").Text("Case Studies");
                               child1.Add().Url("").Text("Awards");
                               child1.Add().Url("").Text("Media Kit");
                           });
                       child.Add().Url("").Text("Company Blog");
                       child.Add().Url("").Text("Technical Blog");
                       child.Add().Url("").Text("Newsletter");
                       child.Add().Url("").Text("Partners").Children(child1 =>
                           {
                               child1.Add().Url("").Text("Technology Partners");
                               child1.Add().Url("").Text("Training Partners");
                               child1.Add().Url("").Text("Consulting Partners");
                           });
                       child.Add().Url("").Text("Locations").Children(child1 =>
                       {
                           child1.Add().Url("").Text("RDU");
                           child1.Add().Url("").Text("Chennai");
                       });
                       child.Add().Url("").Text("Contact Us");
                       child.Add().Url("").Text("Careers");
                   });

               })
   

{% endhighlight %}


Execute the above code to render the multiple sub menus in a hierarchy

![](Getting-Started_images/Getting-Started_img5.png)

Essential ASP.NET MVC Menu with multiple level  sub menu item
{:.caption}
