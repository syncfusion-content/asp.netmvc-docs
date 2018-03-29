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
* Follow the steps mentioned in the [setup guide](http://help.syncfusion.com/common/essential-studio/essential-studio-installer-for-individual-platform) and install the specific/entire platform in your machine.

## Configuring Syncfusion Bower Packages

### Overview

The [Bower](http://bower.io) is a package manager for the Web. Syncfusion Bower package allows to use the Syncfusion JavaScript Widgets in an efficient way.

I>Syncfusion JavaScript Bower package is available in [public Git Repository](https://github.com/syncfusion/JavaScript-Widgets) and also registered as Syncfusion-JavaScript in the Bower registry.

### Bower Installation

To configure the Bower in your machine you need to install [node, npm](http://nodejs.org) and [git](http://git-scm.org). For more information to configure the Bower package, please refer to the official site for [bower](http://bower.io/#install-bower).
Syncfusion JavaScript Bower package can be configured in the following ways.

1. Using command prompt.

2. Using bower.json file.

3. From local directory.

#### Using command prompt

Perform the following steps to install the Syncfusion Bower Package via command prompt in your web application.

1. Open your web project’s location in a command prompt window.

2. Then run the command Bower install <package name>.

   ~~~
   Bower install syncfusion-javascript
   ~~~
   
   ![](Installation-and-Deployment_images/Installation-and-Deployment_img1.jpeg)

3. The Bower will install the Syncfusion JavaScript files into the project location to develop with Syncfusion controls.

N>To install a particular version of a Bower package, you need to provide the version as suffix of the package name while installing. For instance, run the following command to install the package of version 13.3.0.18.
N>'bower install Syncfusion-javascript#13.3.0.18'

#### Using bower.json file

In another way, you can add the packages to the bower.json file by simply specifying the package name. This will install/restore the packages to your project. Please refer to the following image.
 
![](Installation-and-Deployment_images/Installation-and-Deployment_img2.jpeg)

N>By default, ASP.NET 5 (preview) projects have the bower.json file. If your project doesn’t have bower.json file, run the following command from your project directory by Command prompt.
N>'bower init'

![](Installation-and-Deployment_images/Installation-and-Deployment_img3.jpeg)

#### From local directory

You can install the Syncfusion Bower package from a local directory. To perform this, follow the below steps.

1. Navigate the [Syncfusion JavaScript Bower repository](https://github.com/syncfusion/JavaScript-Widgets/) location on GitHub and download the repository as zip by clicking the “Download ZIP” button, and extract the contents to any of the local directory in your computer.

   ![](Installation-and-Deployment_images/Installation-and-Deployment_img4.jpeg)

2. Then run the install command by providing the package content’s location.

   ![](Installation-and-Deployment_images/Installation-and-Deployment_img5.jpeg)

### Bower Update

To update the installed Bower packages, run the command Bower update <package name>.

~~~
Bower update syncfusion-javascript
~~~

![](Installation-and-Deployment_images/Installation-and-Deployment_img6.jpeg)

## Configuring Syncfusion npm Packages

### Overview

The npm is the Package Manager for JavaScript. It makes easy for JavaScript developers to share and reuse the code, and also easy to update the code that you have shared.

### Syncfusion npm package

Syncfusion JavaScript npm package is available in [public Git Repository](https://github.com/syncfusion/JavaScript-Widgets) and also registered as syncfusion-javaScript in the npm registry.

### Syncfusion npm Installation

To configure the npm,  install the [Nodejs](http://nodejs.org/) and update the npm. For more information to configure the npm packages refer to the official site of [npm](https://docs.npmjs.com/getting-started/installing-node).

The syncfusion-javascript npm package can be configured by the following ways.

1. Using Command prompt.

2. Using package.json file.

3. From local directory.

#### Using command prompt

Follow the below steps to install Syncfusion JavaScript npm package via command prompt in the required web application location.

1. Open the project’s location in command prompt window.

2. Run the installation command for npm.

   ~~~
   npm install syncfusion-javascript
   ~~~

   ![](Installation-and-Deployment_images/npminstallationsteps_img1.jpeg)

3. npm install the Syncfusion JavaScript assets into the project location to develop with Syncfusion controls.

N> As per standard, Syncfusion uses the 3 digit version for npm packages. To install a particular version of npm package, provide the version as suffix to the package name while installing.
N> For instance, the following command installs Syncfusion JavaScript package of version 14.1.0.46.
N> 'npm install Syncfusion-javascript@14.1.46'

#### Using package.json file

Add the Syncfusion JavaScript packages to the package.json by simply specifying the package name. This will install/restore the package to the Visual Studio project. Refer to the following image.

![](Installation-and-Deployment_images/npminstallationsteps_img2.jpeg)

N> By default, ASP.NET 5 (preview) projects have package.json file. If Visual Studio project doesn’t have package.json file, run the following command using the project command prompt.
N> 'npm init'

![](Installation-and-Deployment_images/npminstallationsteps_img3.jpeg)

#### From Local Directory

Install the Syncfusion JavaScript npm package from a local directory.

1. Navigate the [Syncfusion JavaScript repository](https://github.com/syncfusion/JavaScript-Widgets) location on GitHub and download the repository as zip by clicking the “Download ZIP” button, and extract the contents to any of the local directory in your computer.

   ![](Installation-and-Deployment_images/npminstallationsteps_img4.jpeg)

2. Run the installation command by providing the package content location.

   ![](Installation-and-Deployment_images/npminstallationsteps_img5.jpeg)

### npm Update

#### Updating global packages

To update the installed npm packages globally, run the following command.

~~~
npm install g- syncfusion-javascript
~~~

![](Installation-and-Deployment_images/npminstallationsteps_img6.jpeg)

### Updating local packages

To update the installed npm packages locally, run the following command.

~~~
npm update
~~~

![](Installation-and-Deployment_images/npminstallationsteps_img7.jpeg)

## Configuring Syncfusion JSPM Packages

### Overview

JSPM is a package manager for [SystemJS universal module loader](https://github.com/systemjs/systemjs), built on top of the dynamic [ES6 module loader](https://github.com/ModuleLoader/es6-module-loader). This can load any module format (ES6, AMD, CommonJS and globals) directly from any registry such as npm and GitHub with flat versioned dependency management. Any custom registry endpoints can be created through the Registry API.

### Syncfusion JavaScript JSPM

Syncfusion JavaScript JSPM package is available in [public Git Repository](https://github.com/syncfusion/JavaScript-Widgets) and also registered as Syncfusion-JavaScript in the npm registry too.

### Syncfusion JSPM Installation

#### Using Command prompt

Follow the below steps to install Syncfusion JavaScript JSPM package via command prompt in the required web application location.

1. Open the project’s location in command prompt window.

2. A) To install the Syncfusion JavaScript JSPM package via GitHub repository.

   ~~~
   jspm install syncfusion=github:syncfusion/Javascript-Widgets
   ~~~
   
   ![](Installation-and-Deployment_images/jspminstallationsteps_img1.jpeg)

   B) To install the Syncfusion JavaScript JSPM package via npm repository.
   
   ~~~
   jspm install npm:syncfusion-javascript
   ~~~
   
N> As per standard, Syncfusion uses the 3 digit version for JSPM packages. To install a particular version of JSPM package, provide the version as suffix to the package name while installing.
N> For instance, The following command installs Syncfusion JavaScript package of version 14.1.0.46.
N> 'JSPM install syncfusion=github:syncfusion/JavaScript-Widgets@14.1.46'

### JSPM Update

To update all the installed packages, use the following command.

~~~
jspm update
~~~

![](Installation-and-Deployment_images/jspminstallationsteps_img1.jpeg)

To update specific package, use the following commands.

~~~
jspm update npm:syncfusion-javascript
~~~

  (Or)
  
~~~
jspm update syncfusion=github:syncfusion/JavaScript-Widgets
~~~


## Deployment

The MVC applications are deployed in the development server by referencing the Syncfusion assemblies appropriately. The steps are shown in the following:

* **Mark the Project directory as Application**: Here, the appropriate directory where the project file is usually saved, should be marked as Application in IIS.
* **Reference the Syncfusion Assemblies**: The Syncfusion assemblies can be referenced in the application either from the Global Assembly Cache (GAC) or from the Application’s bin folder.
* **Use any of the two available deployment patterns**: Default or Fast deployment pattern.

### Default Deployment Pattern

Deploy the application in the development server by referencing the **assemblies** from **GAC**.

* The **Web.config** file is configured according to the referenced **dll**.

* When you deploy your application, ensure that the above referenced assemblies (in your **web.config** files) are present in the **GAC**. This method supports almost all the features of the control.

N> With this pattern, all our **Syncfusion** assemblies are running with full trust.

### Fast Deployment Pattern

Deploy the application in the development server by referencing Syncfusion assemblies in the application's **bin** folder.

* Delete the **Syncfusion** assembly **GAC** entries in your development machine. Now copy the required reference assemblies to the **bin** folder of your application.

* **Web.config** file is configured according to the referenced **dll**.

* In this case, the control’s **DeprecateFunctionalityToRunInPartialTrust** property is turned **on** for the control to work properly. In some cases, few features may not be available. Refer to the control's documentation for more information.

N> If you have XML, mdb, or other data files in your application, ensure that they have sufficient security permissions. Only the Authenticated Users should have the access to files and directory, so as to permit the ASP.NET code to open the file at run-time.
Also, ensure that the machine.config of the deployed system includes appropriate entries for Mozilla and so on within the <browsercaps> tag. The default entries consider these browsers as down level and hence will not render the Syncfusion controls properly.

## Install Location and Samples

Here, the default location on your machine is illustrated where the **Essential Studio package** or the **Essential Studio for ASP.NET MVC** suite gets installed, from that the Syncfusion assemblies and dashboard samples can be accessed.

* The following specified location is the place where all the assemblies, scripts, CSS files, and samples are available.

  `(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\`

  _**For example**, If you have installed the Essential Studio package within **C:\Program Files(x86),** then navigate to the following location,_
  `C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\`

* The **ASP.NET MVC samples** can be accessed from the following location.

  `(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\Samples`

  _**For example**, If you have installed the Essential Studio package within **C:\Program Files(x86),** then navigate to the following location._
  `C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\Samples`

* The Dashboard can be opened by running the **Dashboard.exe** file present within the following location.

  `(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\Infrastructure\Dashboard\4.0`

  _**For example**, If you have installed the Essential Studio package within **C:\Program Files(x86),** navigate to the following location._
  `C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\Infrastructure\Dashboard\4.0`

To run the local samples from dashboard and other online samples, refer to the link [here](http://help.syncfusion.com/ug/common/index.html#!Documents/samples.htm).

## Assemblies Location and Structure

All the Syncfusion assemblies are located in the following specified installed location on your machine.

`(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\precompiledassemblies\{{ site.releaseversion }}`

_**For example**, If you have installed the Essential Studio package within **C:\Program Files(x86),** navigate to the following location._
`C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\precompiledassemblies\{{ site.releaseversion }}`

The Syncfusion assemblies are packed in a separate folder on the basis of the following two types:

  * .NET Framework version
  * MVC version
  
### .NET Framework version-based assemblies

The assemblies based on the version of the .NET Framework are packed under the folders namely **3.5**, **4.0**, **4.5**, and **4.5.1** that are available in the above specified location. Some of the important assemblies available based on the .NET frameworks under each folders (3.5, 4.0, 4.5, 4.5.1) are listed in the following.

<table>
<tr><td>
Syncfusion.Compression.Base.dll</td></tr><tr><td>
Syncfusion.EJ.dll</td></tr><tr><td>
Syncfusion.EJ.Export.dll</td></tr><tr><td>
Syncfusion.EJ.Olap.dll</td></tr><tr><td>
Syncfusion.EJ.PdfViewer.dll</td></tr><tr><td>
Syncfusion.EJ.ReportViewer.dll</td></tr><tr><td>
Syncfusion.Olap.Base.dll</td></tr><tr><td>
Syncfusion.Linq.Base.dll</td></tr><tr><td>
Syncfusion.XlsIO.Base.dll</td></tr><tr><td>
Syncfusion.Pdf.Base.dll</td></tr><tr><td>
Syncfusion.DocIO.Base.dll
</td></tr>
</table>

### MVC version-based assemblies

The assemblies based on the version of the MVC Framework (MVC3, MVC4, and MVC5) are packed under the folder name **MVC** that is available in the following location.

`(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\precompiledassemblies\ {{ site.releaseversion }}\MVC`

_**For example**, If you have installed the Essential Studio package within **C:\Program Files (x86)**, navigate to the below location._
`C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\precompiledassemblies\ {{ site.releaseversion }}\MVC`

Some of the important assemblies available based on the MVC versions (within each folder namely MVC3, MVC4, and MVC5) in the above specified location are listed in the following.

<table>
<tr><td>
Syncfusion.EJ.Mvc.dll</td></tr><tr><td>
Syncfusion.DocIO.Helper.Mvc.dll</td></tr><tr><td>
Syncfusion.Pdf.Helper.Mvc.dll</td></tr><tr><td>
Syncfusion.XlsIO.Helper.Mvc.dll</td></tr><tr><td>
Syncfusion.PdfViewer.Mvc.dll
</td></tr>
</table>

## NuGet Packages Structure

The following structure is maintained for ASP.NET MVC platform NuGet packages from 2015 Volume 2(v13.2.0.29). The latest package cannot be updated, because of the installed Syncfusion NuGet packages prior version of 2015 Volume 2(V13.2.0.29). To update the Syncfusion NuGet packages latest or above version of 2015 Volume 1 Service Pack-2(v13.1.0.30), uninstall the existing packages and install the following required package manually.

<table>
   <tr>
		<td colspan="1" rowspan="2">
			Categories/Package Name<br/>
		</td>
		<td colspan="1" rowspan="2">
			Supported Controls<br/>
		</td>
		<td colspan="1" rowspan="2">
			Assemblies<br/>
		</td>
		<td colspan="2" rowspan="1">
			Assets<br/>
		</td>
		<td>
			Dependencies<br/>
		</td>
	</tr>
    <tr>
		<td>
			Scripts<br/>
		</td>
		<td>
			CSS<br/>
		</td>
		<td>
			<br/>
		</td>
	</tr>
    <tr>
		  <td>
			    Syncfusion.AspNet.Mvc<br/>
		  </td>
		  <td>
			    Grid<br/>Data Visualization<br/>Layout<br/>Editors<br/>Navigation<br/>Notification<br/>To know more information about the controls for above categories navigate to the following link.<br/>{{'<http://www.syncfusion.com/products/aspnetmvc>'| markdownify }}<br/>
		  </td>
		  <td>
			    EJ.MVC<br/>
		  </td>
		  <td>
			   -<br/>
		  </td>
		  <td>
			   -<br/>
		  </td>
		<td>
			Syncfusion.Web.Base<br/>
            Syncfusion.AspNet.Mvc.FileFormats<br/>
		</td>
	</tr>
		<tr>
		<td>
			Syncfusion.AspNet.Mvc.PdfViewer<br/>
		</td>
		<td>
			Pdf Viewer<br/>
		</td>
		<td>
			EJ.PdfViewer<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			Syncfusion.AspNet.Mvc<br/>
		</td>
	</tr>
	<tr>
		<td>
			Syncfusion.AspNet.Mvc.FileFormats<br/>
		</td>
		<td>
			DocIO<br/>XlsIO<br/>PDF<br/>PDF Viewer<br/>Power Point(Preview)<br/><br/>
		</td>
		<td>
			DocToPDFConverter.Base<br/>ExcelToPDFConverter.Base<br/>PresentationToPDFConverter.Base<br/>HtmlConverter.Base<br/>OfficeChartToImageConverter.WPF<br/>ExcelChartToImageConverter.WPF<br/>SfChart.WPF<br/>Shared.WPF<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			Syncfusion.Web.FileFormatsBase<br/>
		</td>
	</tr>
	<tr>
		<td>
			Syncfusion.AspNet.Mvc.FileFormatsHelper<br/>
		</td>
		<td>
			DocIO.Helper.Mvc<br/>Pdf.Helper.Mvc<br/>XlsIO.Helper.Mvc<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			Syncfusion.AspNet.Mvc.FileFormats<br/>
		</td>
	</tr>
	<tr>
		<td>
			Syncfusion.AspNet.Mvc.Pivot<br/>
		</td>
		<td>
			Pivot Grid<br/>Pivot Chart<br/>Pivot Client<br/>Pivot Gauge<br/>
		</td>
		<td>
			Olap.Base<br/>EJ.Pivot<br/>PivotAnalysis.Base <br/>EJ.MVC<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			Syncfusion.Web.Base<br/>Syncfusion.Web.FileFormatsBase<br/><br/>
		</td>
	</tr>
	<tr>
		<td>
			Syncfusion.AspNet.Mvc.ReportViewer<br/>
		</td>
		<td>
			Report Viewer<br/>
		</td>
		<td>
			Shared.WPF<br/>RichTextBoxAdv.WPF<br/>Chart.WPF<br/>GridCommon.WPF<br/>Grid.WPF<br/>SfMaps.WPF<br/>ReportControls.WPF<br/>ReportWriter.Base<br/>EJ.ReportViewer<br/>Gauge.WPF<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			Syncfusion.Web.FileFormatsBase<br/>Syncfusion.Web.Base<br/>Syncfusion.AspNet.Mvc<br/>
		</td>
	</tr>
  <tr>
		<td>
			Syncfusion.Web.Base<br/>
		</td>
    <td>
			-<br/>
		</td>
		<td>
			Linq.Base<br/>EJ<br/>EJ.Export<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			Syncfusion.JavaScript<br/>
		</td>
	</tr>
	<tr>
		<td>
			Syncfusion.Web.FileFormatsBase<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			Compression.Base<br/>XlsIO.Base<br/>Pdf.Base<br/>DocIO.Base<br/>OfficeChart.Base<br/>Presentation.Base<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			-<br/>
		</td>
		<td>
			-<br/>
		</td>
	</tr>
</table>