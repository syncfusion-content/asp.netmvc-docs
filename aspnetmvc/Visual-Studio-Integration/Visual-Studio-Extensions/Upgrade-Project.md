---
layout: post
title: Upgrade Project | ASP.NET MVC (Essential JS 1) | Syncfusion
description: Project Migration is a add-in that helps migrate existing Syncfusion Essential JS 1 ASP.NET MVC project from one Syncfusion version to another version
platform: ejmvc
control: Syncfusion Extensions
documentation: ug
---

# Upgrade Project

Syncfusion Project Migration is a Visual Studio add-in that allows you to migrate the existing Syncfusion ASP.NET MVC Web Application from one Essential Studio version to another version.

Use the following steps to migrate your existing Syncfusion ASP.NET MVC Web Application:

1. To open Migration Wizard, follow either one of the options below: 

   **Option 1**  
   Click **Syncfusion Menu** and choose **Essential Studio for ASP.NET MVC (EJ1) > Migrate Project…** in **Visual Studio**.

   ![Syncfusion Essential JS 1 ASP.NET MVC Project Migration via Syncfusion menu](Migrate-Syncfusion-Project_images/SyncfusionMenu_ProjectMigration_img.png)

   N> In Visual Studio 2019, Syncfusion menu is available under Extensions in Visual Studio menu.

   **Option 2**  
   Right-click the **Syncfusion ASP.NET MVC Application** from Solution Explorer and select **Syncfusion Essential JS 1**. Choose **Migrate the Essential JS 1 Project to Another Version...**

   ![Syncfusion Essential JS 1 ASP.NET MVC Project Migration add-in](Migrate-Syncfusion-Project_images/ProjectMigration_img1.png)

2. The **Project Migration** window appears. You can choose the required Essential Studio version that is installed in the machine.

   ![Syncfusion Essential JS 1 ASP.NET MVC Project Migration wizard](Migrate-Syncfusion-Project_images/ProjectMigration_img2.png)

3. The Project Migration window allows you to configure the following options.

   **i. Essential Studio Version:** Select a version from the list of installed Syncfusion versions.
	  
   **ii. Assemblies From:** Choose the assembly location, from where the assembly is added to the project.
	  
   ![Choose the assembly location from where the assembly is added to the project](Migrate-Syncfusion-Project_images/ProjectMigration_img3.jpeg) 

4. Click the **Migrate** Button. The **Project Backup** dialog appears. In the dialog, if click **Yes**, it will backup the current project before migrating the Syncfusion project. If click **No**, it will migrate the project to required Syncfusion version without backup. 

     ![Syncfusion Essential JS 1 ASP.NET MVC Project Migration backup dialog](Migrate-Syncfusion-Project_images/ProjectMigration_img4.png)
      
5. The Syncfusion reference assemblies, Scripts, CSS, and Web.Config entries are updated to the corresponding version in the project.
