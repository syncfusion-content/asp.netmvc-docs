---
layout: post
title: Template | Rotator | ASP.NET MVC | Syncfusion
description: template 
platform: ejmvc
control: Rotator
documentation: ug
---

# Template 

This Template feature implements in Rotator control. Rotator template will allow you to customize the rendering structure for its li elements. Using template API with data binding can render image, audio or video inside the Rotator control. 

The property template specifies the structure for slide li elements. The default value is null. The value set to this property is string. 


1. Add the below code in your view page to render the Rotator

 
   ~~~ cshtml

	// Add the following code in View page to configure Rotator widget

    <div class="frame">
            @Html.EJ().Rotator("rot").Datasource((IEnumerable<LocalData>)ViewBag.datasource).SlideWidth("100%").SlideHeight("350px").IsResponsive(true)
            .Template("<div class='image'><img src = ${url} title = ${text} class='image'/> </div>")
    </div>          

   ~~~
   
   
   ~~~ csharp

   // Add the following code to add slide image items in the controller page

  
        List<LocalData> localValues = new List<LocalData>();
   
        public ActionResult LocalData()
        {    
           localValues.Add(new LocalData{ text= "Beautiful Bird", url= "../Images/rotator/bird.jpg" });
           localValues.Add(new LocalData { text = "Colorful Night", url = "../Images/rotator/night.jpg" });
           localValues.Add(new LocalData { text = "Technology", url = "../Images/rotator/tablet.jpg" });
           localValues.Add(new LocalData { text = "Nature", url = "../Images/rotator/nature.jpg" });
           localValues.Add(new LocalData { text = "Snow Fall", url = "../Images/rotator/snowfall.jpg" });
           localValues.Add(new LocalData { text = "Credit Card", url = "../Images/rotator/card.jpg" });
           localValues.Add(new LocalData { text = "Amazing Sculptures", url = "../Images/rotator/sculpture.jpg" });
           ViewBag.datasource=localValues;
           return View();
        } 

     ~~~

2. CSS. 

   ~~~ css

   <style type="text/css" class="cssStyles">
        .frame {
            width: 100%;
            box-sizing : border-box;
        }
        #rot > li img {
            width: 100%;
            height: 350px;
        }
    </style>

   ~~~

