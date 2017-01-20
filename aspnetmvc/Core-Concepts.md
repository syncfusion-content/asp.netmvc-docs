---
layout: post
title: Core Concepts | ASP.NET MVC | Syncfusion
description: Core Concepts 
platform: ejmvc
control: Common 
documentation: ug
---

# Core Concepts

## Basics

### API Configuration

Using fluent helper methods we can set values to Syncfusion Widget properties during or after the creation.

![](core-concepts_images/core-concepts_img1.png)

In the above example, minimum & maximum range defined for DatePicker component. 

### Wiring Client Side Events

Client side events can be wired in the same way as properties. But here all the client side events are grouped into **“ClientSideEvents”** Action method

1. Specify the client side event name in string format.

   For example:
   
   ~~~ cshtml
   
	@(Html.EJ().DatePicker("MyFirstDatepicker")
		.MinDate(new DateTime(2016,5,1))
		.MaxDate(new DateTime(2016,12,31))
		.Value(DateTime.Now.AddDays(1) )
		.ClientSideEvents( events =>
		events.Change("datepicker_change") // To handle datepicker change event
	    .Select("datepicker_select") // To handle datepicker select event
	    )								
     )
   ~~~

2. Declare the client side events in Script sections

   ~~~ cshtml
			
	@section scripts{

		<script>
			function datepicker_change(args) {
			// event handler 
			//args contains entire model of DatePicker to get the value of all properties
			}
            function datepicker_select(args) {
			// event handler 
			//args contains entire model of DatePicker to get the value of all properties
            }
        </script>

	}

   ~~~
   
### Invoking methods

Syncfusion JavaScript widget client side methods can be accessed via their client side object. You can access the client side object via jQuery.data() utility method.   

1. Create server side component in CSHTML

   ~~~ cshtml
   
	@(Html.EJ().DatePicker(“MyFirstDatepicker")
		.MinDate(new DateTime(2016,5,1))
		.MaxDate(new DateTime(2016,12,31))
	    .Value(DateTime.Now.AddDays(1) )                								
	)

   ~~~
   
2. Access the client side object using jQuery.data() as shown below

   ~~~ cshtml
   
	<script>

		$(document).ready(function () {
        var datepickerObject = $("#MyFirstDatepicker").data("ejDatePicker");
	    });
		
    </script>

   
   ~~~

3. Access the method from client side object as like properties access as show below

   ~~~ cshtml
		
	<script>
		$(document).ready(function () {
		var datepickerObject = $("#MyFirstDatepicker").data("ejDatePicker");            
		datepickerObject.disable(); // to disable the datepicker object
		var selectedDate = datepickerObject.getValue(); // to access the selected value            
        });
	</script>
			
   ~~~
   

   
## Localization

Localization is the process of customizing an application for given language and region.

Find the steps to configure the Syncfusion Components to particular language from below

1. Specify the target culture in **web.config** file under **<system.web>** root

   ~~~ xml
   
	<system.web>
	    <globalization uiCulture="fr-FR" culture="fr-FR" enableClientBasedCulture="true"/>
	</system.web>

   ~~~

2. Load the globalize culture file from **i18n** folder dynamically using below codes 


   ~~~ cshtml
   
	@Scripts.Render("~/Scripts/ej/i18n/ej.culture." + System.Globalization.CultureInfo.CurrentCulture.Name.ToString() + ".min.js")

   ~~~
   
   
3. Download and refer the Syncfusion UI component localized text from [ej-global](https://github.com/syncfusion/ej-global/tree/master/localetexts) repository.

   
   ![](core-concepts_images/core-concepts_img1.png)
   
4. Load the Localized text file from **localetexts** folder as like previous step   

   ~~~ cshtml
   
	@Scripts.Render("~/Scripts/ej/localetexts/ej.localetexts." + System.Globalization.CultureInfo.CurrentCulture.Name.ToString() + ".js")

   ~~~	

5. Set the culture to Syncfusion UI components using **Locale** helper method as shown in below
  
  
   ~~~ cshtml
  
	@(Html.EJ().DatePicker("MyFirstDatepicker")
		.MinDate(new DateTime(2016, 5, 1))
		.MaxDate(new DateTime(2016, 12, 31))
		.Locale(System.Threading.Thread.CurrentThread.CurrentCulture.Name) // Specify the UI culture
		.ClientSideEvents(events =>
		events.Change("datepicker_change") // To handle datepicker change event
		.Select("datepicker_select") // To handle datepicker select event
		)
    )
   ~~~
   
6. Compile and execute the application. You can able to see the below output in the browser
