---
layout: post
title: Core Concepts | ASP.NET MVC | Syncfusion
description: Core Concepts 
platform: ejmvc
control: Common 
documentation: ug
---

# Utilities

The Syncfusion MVC Extension provides you quick access, so that you can create or configure the Syncfusion MVC projects. The Syncfusion ASP.NET MVC Extensions has the following features.

* Syncfusion Sample Creator for ASP.NET MVC
* Syncfusion Project Conversion for ASP.NET MVC
* Syncfusion Project Migration for ASP.NET MVC

## Project Conversion

The Project Conversion is a Visual Studio add-in that converts an existing ASP.NET MVC Project into a Syncfusion ASP.NET MVC Project by adding the required assemblies and resource files.

### Convert into Syncfusion ASP.NET MVC (Web) project

The following steps help you to use the Syncfusion Project Conversion in the existing ASP.NET MVC (Web) Project.

1. Open an existing Microsoft MVC Project or create a new Microsoft MVC Project.
2. Right-click the Project and select Syncfusion VS Extensions. Then, choose the Convert to Syncfusion ASP.NET MVC (Web) Application. For more information, refer to the following screenshot.

   ![](Utility_images/ProjectConversion_img1.jpeg)

3. Project Conversion Wizard opens so that you can configure the project.

   ![](Utility_images/ProjectConversion_img2.jpg)

   The following configurations are used in the Project Conversion Wizard.
   
   **Assemblies From:**

   Choose the assembly location:

	1. Added From GAC: Refer to the assemblies from the Global Assembly Cache.
	2. Added from Installed Location: Refer to the assemblies from the Syncfusion Installed locations.
    3. Add Referenced Assemblies to Solution: Copy and refer to the assemblies from project's solution file lib directory.

   ![](Utility_images/Project-Conversion_img3.jpeg)
    
   **Choose the Theme:**
   
   The master page of project will be updated based on the selected theme. The Theme Preview section shows the controls preview before converting to a Syncfusion project.
   
   ![](Utility_images/Project-Conversion_img4.jpeg)
   
   **Choose CDN Support:**

   The master page of the project will be updated based on the required Syncfusion CDN links.
   
   ![](Utility_images/Project-Conversion_img20.jpeg)
   
   **Choose Copy Global Resources:**
    
   The localization culture files will be shipped into Scripts\ej\i18n directory of the project.
   
   ![](Utility_images/Project-Conversion_img21.jpeg)

4. Choose the required controls from Components section and Click the **Convert** button to convert it into a Syncfusion Project.

   ![](Utility_images/ProjectConversion_img5.jpg)
   
5. The **Project Backup** dialog will be opened. Click yes, to backup the current project before converting it to Syncfusion project. Click No to convert the project to Syncfusion project without backup.
   
   ![](Utility_images/Project-Conversion_img6.jpg)


6. The required Syncfusion Reference Assemblies, Scripts and CSS are included in the MVC Project. For more information, refer to the following screenshots.

   ![](Utility_images/ProjectConversion_img7.jpeg)

   ![](Utility_images/ProjectConversion_img8.jpeg)

   ![](Utility_images/ProjectConversion_img9.jpeg)

### Rendering Control after Syncfusion ASP.NET MVC (Web) Conversion:

Once you convert your ASP.NET MVC project to Syncfusion ASP.NET MVC Project, perform the following steps to render the Syncfusion Controls to your project.
1. The CSS, Scripts, Syncfusion References, and required Web.config file entries are added to your project by Syncfusion ASP.NET MVC Conversion.

2. Add the required Script and CSS files references in the master page (_Layout.cshtml/Layout.vbhtml file). For more information, please refer to the following screenshot.

   ![](Utility_images\ProjectConversion_img17.jpeg)

3. Now, include the Syncfusion controls to your project. For more information, refer to the following screenshot.

   ![](Utility_images\ProjectConversion_img18.jpeg)

4. Run the project and the following output will be displayed.

   ![](Utility_images\ProjectConversion_img19.jpeg)

## Project Migration

The Project Migration is a Visual Studio add-in that helps to migrate the existing Syncfusion ASP.NET MVC (Web) project from one Syncfusion version to another Syncfusion version.

The following steps help you to migrate from one version to another version of your existing Syncfusion ASP.NET MVC(web) application.

1. Right-click the Syncfusion ASP.NET MVC Project and select Syncfusion VS Extensions. Choose Migrate the project to another version.

   ![](Utility_images/ProjectMigration_img1.jpeg)

2. The Project Migration window appears. You can choose the required Syncfusion version that is installed in the machine, that can be either Syncfusion ASP.NET MVC.

   ![](Utility_images/ProjectMigration_img2.jpeg)

3. The Project Migration window allows you to configure the following options:

   * Essential Studio Version: Select any version from the list of Installed Versions.
	  
   * Assemblies From: Add the assembly to project from the following locations.
	  
	    1. Added From GAC: Refer the assemblies from the Global Assembly Cache.
		  2. Added from Installed Location: Refer to the assemblies from the Syncfusion Installed locations.
      3. Add Referenced Assemblies to Solution: Copy and refer to the assemblies from project's solution file lib directory.

4. Click the Migrate Button and the **Project Backup** dialog will be opened. Click Yes to backup the current project before migrating the Syncfusion project. Click No to migrate the project to required Syncfusion version without backup.

     ![](Utility_images/ProjectMigration_img3.jpeg)
      
5. The Syncfusion Reference Assemblies, Scripts and CSS are updated to the corresponding version in the project.


## Sample Creator

Sample Creator is the utility that allows you to create Syncfusion ASP.NET MVC Projects along with the samples based on Controls and Features selection.

### Create Syncfusion MVC Project from Sample Creator

Sample Creator can be download from the Syncfusion Dashboard. After installing the complete Essential Studio suite or ASP.NET MVC setup, follow the given steps:

1. Launch the Syncfusion Essential Studio Dashboard and select the ASP.NET MVC platform. Select the **Sample Creator** button to launch the Sample Creator Wizard. For more information, refer to the following screenshot.

   ![](Utility_images/Sample-Creator_img1.jpeg)

2. Syncfusion Sample Creator Wizard displays the **Controls and its Feature Selection** section.

   ![](Utility_images/Sample-Creator_img2.jpeg)

#### Controls Selection

 The Syncfusion ASP.NET MVC controls are listed here and you can choose the required controls. The controls are grouped product wise.

 ![](Utility_images/Sample-Creator_img3.png)

#### Feature Selection

Based on the controls, the Feature is enabled to choose the features of the corresponding controls.

![](Utility_images/Sample-Creator_img4.png)

#### Project Configuration

You can configure the following project details in the Sample Creator.

* MVC Version: Choose the required MVC Version.
* Language: Select the language, either C# or VB.
* VS Version: Choose the Project version.
* .NET Framework: Choose the .NET Framework version.
* View Engine: Select either Razor or ASPX. By default, Syncfusion supports only Razor view engine for ASP.NET MVC projects.
* Compress Style Sheets: Option to compress style sheets.
* Compress Scripts: Option to compress the scripts.
* Name: Name your Syncfusion MVC Application.
* Location: Choose the target location of your project.
* Theme Selection: Choose the required theme. The Theme Preview section shows the controls preview before creating the Syncfusion project.

![](Utility_images/Sample-Creator_img6.jpeg)

When you click the Create button, the new Syncfusion ASP.NET MVC project is created. The following is added in the project:

* Added the required Controller and View files in the project.
  
  ![](Utility_images/Sample-Creator_img7.png)

* Included the required Syncfusion ASP.NET MVC scripts and themes files.
  
  ![](Utility_images/Sample-Creator_img8.png)

* The required Syncfusion assemblies are added for selected controls under Project Reference.
 
  ![](Utility_images/Sample-Creator_img9.png)

* Configure the Web.Config file by adding the Syncfusion reference assemblies.

  ![](Utility_images/Sample-Creator_img10.jpeg)

* Once the project is created you can open the project by clicking the Yes button. Refer to the following screenshot for more information.

  ![](Utility_images/Sample-Creator_img11.jpeg)