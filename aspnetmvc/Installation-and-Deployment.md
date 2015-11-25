---
layout: post
title: Installation and Deployment | ASP.NET MVC | Syncfusion
description: Installation and Deployment
platform: ejmvc
control: Common 
documentation: ug
---

# Installation and Deployment

## Installation

* Download the setup file (.exe) of Essential Studio for ASP.NET MVC product from this [link](http://www.syncfusion.com/downloads/aspnetmvc) with your Syncfusion account.
* You can now follow the steps mentioned in the [setup guide](http://help.syncfusion.com/common/essential-studio/essential-studio-installer-for-individual-platform) install the specific/entire platform in your machine.

## Deployment

The MVC applications are deployed in the development server by referencing the Syncfusion assemblies appropriately. The steps are as shown below,

* **Mark the Project directory as Application** – Here, the appropriate directory where the project file is usually saved, should be marked as Application in IIS.
* **Reference the Syncfusion Assemblies** – The Syncfusion assemblies can be referenced in the application either from the Global Assembly Cache (GAC) or from the Application’s bin folder.
* **Use any of the two available deployment patterns** – Default or Fast deployment pattern.

### Default Deployment Pattern      

Deploy the application in the development server by referencing the **assemblies** from **GAC**.

* **Web.config** file is configured according to the referenced **dlls**. 

* When you deploy your application, ensure that the above referenced assemblies (in your **web.config** files) are present in the **GAC**. This method supports almost all the features of the control.

N> With this pattern, all our **Syncfusion** assemblies run at full trust.

### Fast Deployment Pattern                

Deploy the application in the development server by referencing Syncfusion assemblies in the application's **bin** folder.

* Delete the **Syncfusion** assembly **GAC** entries in your development machine. Now copy the required reference assemblies to the **bin** folder of your application.

* **Web.config** file is configured according to the referenced **dlls**.

* In this case, the control’s **DeprecateFunctionalityToRunInPartialTrust** property is turned **on** for the control to work properly. In some cases, few features may not be available. You can refer the control's documentation for more information.

N> If you have XML, mdb or other data files in your application, ensure that they have sufficient security permissions. Only the Authenticated Users should have access to the files and directory, so as to permit the ASP.NET code to open the file at run-time.
Also, ensure that the machine.config of the deployed system includes appropriate entries for Mozilla and so on within the <browsercaps> tag. The default entries consider these browsers as downlevel and hence will not render the Syncfusion controls properly.

## Install Location & Samples

Here, the default location on your machine is illustrated where the **Essential Studio package** or the **Essential Studio for ASP.NET MVC** suite gets installed, from where the Syncfusion assemblies and dashboard samples can be accessed.

* The below specified location is the place from where all the assemblies, scripts, css files and samples are available,

  `(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\`

  _**For example**, If you have installed the Essential Studio package within **C:\Program Files(x86),** then navigate to the below location,_
  `C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\`

* The **ASP.NET MVC samples** can be accessed from the below location,

  `(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\Samples`

  _**For example**, If you have installed the Essential Studio package within **C:\Program Files(x86),** then navigate to the below location,_
  `C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\Samples`

* The Dashboard can be opened by running the **Dashboard.exe** file present within the following location,

  `(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\Infrastructure\Dashboard\4.0`

  _**For example**, If you have installed the Essential Studio package within **C:\Program Files(x86),** then navigate to the below location,_
  `C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\Infrastructure\Dashboard\4.0`

To run the local samples from dashboard and other online samples, refer the link [here](http://help.syncfusion.com/ug/common/index.html#!Documents/samples.htm).

## Assemblies Location & Structure

All the Syncfusion assemblies are located in the below specified installed location on your machine,

`(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\precompiledassemblies\{{ site.releaseversion }}`

_**For example**, If you have installed the Essential Studio package within **C:\Program Files(x86),** then navigate to the below location,_
`C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\precompiledassemblies\{{ site.releaseversion }}`

The Syncfusion assemblies are packed in a separate folder on the basis of the following two types,

  * .Net framework version
  * MVC version
  
### .Net framework version-based assemblies

The assemblies based on the version of the .NET framework are packed under the folders namely **3.5**, **4.0**, **4.5** and **4.5.1** available in the above specified location. Some of the important assemblies available based on the .NET frameworks under each folders (3.5, 4.0, 4.5, 4.5.1) are listed below,

<table>
<tr><td>
Syncfusion.Compression.Base.dll<br/>
Syncfusion.EJ.dll<br/>
Syncfusion.EJ.Olap.dll<br/>
Syncfusion.Olap.Base.dll<br/>
Syncfusion.Linq.Base.dll<br/>
Syncfusion.XlsIO.Base.dll
</td></tr>
</table>

### MVC version-based assemblies

The assemblies based on the version of the MVC framework (MVC3, MVC4, MVC5) are packed under the folder namely **MVC** available in the below location,

`(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\precompiledassemblies\ {{ site.releaseversion }}\MVC`

_**For example**, If you have installed the Essential Studio package within **C:\Program Files (x86)**, then navigate to the below location,_
`C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\precompiledassemblies\ {{ site.releaseversion }}\MVC`

Some of the important assemblies available based on the MVC versions (within each folder namely MVC3, MVC4 & MVC5) in the above specified location are listed below,

<table>
<tr><td>
Syncfusion.EJ.Mvc.dll<br/>
Syncfusion.DocIO.Helper.Mvc.dll<br/>
Syncfusion.Pdf.Helper.Mvc.dll<br/>
Syncfusion.XlsIO.Helper.Mvc.dll
</td></tr>
</table>