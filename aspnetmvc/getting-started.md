---
layout: post
title: Getting Started | ASP.NET MVC | Syncfusion
description: Getting Started
platform: ejmvc
control: Common 
documentation: ug
---

# Getting Started

The similar steps are followed for integrating the Syncfusion controls into MVC 3, MVC 4 , MVC 5 & MVC6 applications, the only thing that makes it a little bit different is the reference assemblys version chosen for each of the target MVC application. 

There are two ways for embedding our controls into ASP.NET MVC application:

1. Through Nuget Packages
2. Integration using Project Template

The procedure that are followed in manual integration process is entirely automated, when we create an application using Syncfusion Project template.



## Through Nuget Packages

To add our Syncfusion MVC controls into the new ASP.NET MVC5 application by making use of the **Syncfusion** **Nuget** **Packages**, refer the following steps 

1. The steps to download and configure the required **Syncfusion** **NuGet** **Packages** in Visual Studio is mentioned [here](http://help.syncfusion.com/aspnetmvc/installation-and-deployment#configuring-syncfusion-nuget-packages-in-visual-studio)

2. Once Configured the Packages source, search and install the **Syncfusion.AspNet.Mvc5** from **Package** **Manager** **console** using following commands

   **PM>Install-Package Syncfusion.AspNet.Mvc5**
   
   ![](getting-started_images/getting-started_img1.png)
   
3. The **Unobtrusive** setting is enabled in your applications web.config file by default, while initial creation. You need to change its value to **false** in your application as shown below,   

   ~~~ cshtml

	<appSettings>
		<add key="ClientValidationEnabled" value="true" />
		<add key="UnobtrusiveJavaScriptEnabled" value="false" />
	</appSettings>

   ~~~
	  
4. You need to add the script manager code in the **_Layout.cshtml** file present within the **~/Views/Shared** folder of your application. Add it before the closing body tag in the _Layout.cshtml file

   ~~~ cshtml
	</body>
        @RenderSection("scripts", required: false)
        @Html.EJ().ScriptManager()
    </body>

   ~~~		
	  
	
   N>The main reason for referring the Script manager in _Layout file is that, it can be referred as common by all the View files present within your application. If **unobtrusive** is set to true in the application, then the script manager can be excluded, as the control is initialized using HTML5 attributes. 

5. Syncfusion specific stylesheets are loaded into the **Content** folder of your application, include the below specified theme reference **(default-theme/ej.web.all.min.css)** file in the **~/Views/Shared/_Layout.cshtml** file, within the head section as this file contains the default theme styles applied for all the Syncfusion MVC controls.  

   ~~~ cshtml
   
	<head>
	    <title>@ViewBag.Title</title>
	    @Styles.Render("~/Content/ej/web/bootstrap-theme/ej.web.all.min.css")    
	</head>

   ~~~			

6. It is mandatory to include the reference to the required JavaScript files in your **_Layout.cshtml**, so as to render the Syncfusion MVC controls properly. 	 
   
   ~~~ cshtml
   
	<head>
		<meta charset="utf-8" />
		<title>@ViewBag.Title - My ASP.NET MVC Application</title>
		@Styles.Render("~/Content/ej/web/bootstrap-theme/ej.web.all.min.css")
	</head>

	<body>
		@Scripts.Render("~/bundles/jquery")
		@Scripts.Render("~/bundles/bootstrap")  
		@Scripts.Render("~/Scripts/jquery.easing.1.3.js")
		@Scripts.Render("~/Scripts/jsrender.min.js")
		@Scripts.Render("~/Scripts/ej/web/ej.web.all.min.js")  
		@RenderSection("scripts", required: false)
		@Html.EJ().ScriptManager();
	</body>

   ~~~	
   
	The order of the reference to the script files made in the above section should be maintained in the same manner as mentioned above.  
   
	If your application contains duplicate/multiple references to the jQuery files, remove it as the explicit reference to the **jquery-1.10.2.min.js** script file is added to the application as specified above.  

7. Now you can add the control **DatePicker** in the **Index.cshtml** file present within **~/Views/Home** folder.   
	
   ~~~ cshtml
   
    @Html.EJ().DatePicker("MyFirstDatepicker")

   ~~~	


8. Compile and execute the application. You can able to see the below output in the browser.	

	![](getting-started_images/getting-started_img2.png)

## Using Project Template

The **Project** **Configuration** **Wizard** automates the process of configuring the required Syncfusion assemblies, scripts and their styles within the newly created application. Lets look onto these topics in detail in the below sections.

1. In the Visual Studio 2010, create a New **Syncfusion** **ASP.NET** **MVC** **Application** project from **Syncfusion** **Project** **Template** that you can see in the **New** **Project** pop-up as shown in the below image. Name it as SyncfusionMvcApplication1 and click **OK**

	![](getting-started_images/getting-started_img3.png)

2. Then it opens **Project** **Configuration** **Wizard** as shown below. In this Wizard, select **Target** **MVC** **Version** as **MVC3** and keep the **other** options as default. Click **Next**.

	![](getting-started_images/getting-started_img4.png)
	
3. Next window containing the list of Syncfusion MVC controls will be shown. Choose the required controls and then click **Create**.

	![](getting-started_images/getting-started_img5.png)
	
4. Now you can notice the **Sycfusion** **MVC** **5** **References**, **Scripts** and **Styles** are configured into Scripts and Content folders. Also it configures the **web.config** and **_Layout.cshtml** files

	![](getting-started_images/getting-started_img6.png)
	
5. Now you can add the control **DatePicker** in the **Index.cshtml** file present within **~/Views/Home** folder.

   ~~~ cshtml
		
	@Html.EJ().DatePicker("MyFirstDatepicker")

   ~~~

6. Compile and execute the application. You can able to see the below output in the browser.

	![](getting-started_images/getting-started_img7.png)
	
For more information about Project Configuration Templates and their options details, please visit [here](http://help.syncfusion.com/extension/aspnet-mvc-extension/syncfusion-project-templates)

## Convert to Syncfusion Project

Project conversion wizard helps to convert the existing MVC application into Syncfusion MVC application.  Please find the Steps for conversion from below:

1. Open your existing application in Visual Studio and right click on your project in the solution explorer. In the context Menu , find & select the **Syncfusion** **VS** **Extension** **->** **Convert** **to** **Syncfusion** **MVc** **(Web)** **Application**

	![](getting-started_images/getting-started_img8.png)

2. It opens the **Project** **Conversion** **wizard** as shown below. In this wizard, select your components (here the components are grouped based on usage) from the left panel. Click **Convert**.

	![](getting-started_images/getting-started_img9.png)

3. It will prompt the **Project Backup** dialog to save your current project (with older version) into **Backup** folder of the same project location. Click **Yes** and continue

	![](getting-started_images/getting-started_img10.png)

4. Now you can notice the **Syncfusion MVC assembly references, Scripts and Styles** are configured into your existing application. Also it configures the webconfig files. 

	![](getting-started_images/getting-started_img11.png)

5. Since we are converting our earlier working application, we need to configure the **_Layout.cshtml** file or **your active layout** file manually.Include the **Syncfusion theme (default-theme/ej.web.all.min.css) & Script file** references into your **_Layout.cshtml** file as shown below

   ~~~ cshtml
   
	<head>
		<meta charset="utf-8" />
		<title>@ViewBag.Title - My ASP.NET MVC Application</title>
		… …
		@Styles.Render("~/Content/ej/web/bootstrap-theme/ej.web.all.min.css")
    </head>

	<body>
		… …
		@Scripts.Render("~/bundles/jquery")
		@Scripts.Render("~/bundles/bootstrap")  
		@Scripts.Render("~/Scripts/jquery.easing.1.3.min.js")
		@Scripts.Render("~/Scripts/jsrender.min.js")
		@Scripts.Render("~/Scripts/ej/ej.web.all.min.js")  
		@RenderSection("scripts", required: false)
		@Html.EJ().ScriptManager();
	</body>
		
   ~~~		

6. Change the **Unobtrusive** setting value to **false** in your application as shown below, 

   ~~~ cshtml
   
	<appSettings>
		<add key="ClientValidationEnabled" value="true" />
		<add key="UnobtrusiveJavaScriptEnabled" value="false" />
	</appSettings>

   
   ~~~	   
   
7. Now you can add the Syncfusion control into your target cshtml file.  

   ~~~ cshtml
   
	@Html.EJ().DatePicker("MyFirstDatepicker")
		
   ~~~   
   
8. Compile and execute the application. You can able to see the below output in the browser.   
   
   
   ![](getting-started_images/getting-started_img12.png)
   
   
## Migrate Syncfusion Project into another version

The Migrate Wizard helps to upgrade/downgrade the Syncfusion Project into another version. This is solutions for developer who has multiple version of Essential Studio and want to upgrade/downgrade the project without manually corrections in the csproj, web.config, Content & Scripts. The wizard automated the manual migration steps, so you can switch between difference versions by simple below steps   
   
1. Open your existing application in Visual Studio and right click on your project in the solution explorer. In the context Menu , find & select the **Syncfusion VS Extension -> Migrate the Project to Another Version**   
   
   ![](getting-started_images/getting-started_img13.png)
   
2. Now the migration window opened as shown below. The Essential Studio version dropdown populated with Syncfusion which is installed in your machine. You can choose the required version and click **Migrate** button to downgrade/upgrade purpose.  
   
	![](getting-started_images/getting-started_img14.png)
   
3. It will prompt the **Project Backup** dialog to save your current project (with older version) into **Backup** folder of the same project location.    
   
    ![](getting-started_images/getting-started_img15.png)
   
4. Now the corresponding Syncfusion assembly references, Styles, Scripts and webconfig entries are replaced based on the selected Syncfusion version.   