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

There are three ways for embedding our controls into ASP.NET MVC application:

1. Through Syncfusion Nuget Packages
2. Integration using Syncfusion Project Template

The procedure that are followed in manual integration process is entirely automated, when we create an application using Syncfusion Project template.



## Through Syncfusion Nuget Packages

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

## Using Syncfusion Project Template

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


## MVC 6 Application


### System Requirements:



To work with ASP.NET MVC 6, you need to make sure is whether you have installed the following software on your machine



*  Visual Studio 2015 Update 1 and above.

*  Microsoft ASP.NET Web Tools 2015 (RC1).



### Installation



Refer the following steps to configure ASP.NET MVC 6 on your system



*  Open the [GitHub ASP.NET](https://github.com/aspnet/home) page that guides you to configure the ASP.NET MVC 6.

*  Copy the below mentioned command for Upgrading **DNVM** from that page.

{% highlight text %}


@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&{$Branch='dev';$wc=New-Object System.Net.WebClient;$wc.Proxy=[System.Net.WebRequest]::DefaultWebProxy;$wc.Proxy.Credentials=[System.Net.CredentialCache]::DefaultNetworkCredentials;Invoke-Expression ($wc.DownloadString('https://raw.githubusercontent.com/aspnet/Home/dev/dnvminstall.ps1'))}"



{% endhighlight %}

*  Open the command prompt with [Administrator mode](https://technet.microsoft.com/en-in/library/cc947813(v=ws.10).aspx) and run the above command,which will download the **DNVM (.NET Version Manager)**as mentioned in the below screenshotand place it in your user profile. The DNVM works manipulate from this installed path.

![](getting-started_images/getting-started_img100.jpeg)



*  Now you check with the existing location of **DNVM** by executing the following command in a command prompt.



{% highlight text %}


C:\Users> where dnvm



{% endhighlight %}



*  After the DNVM installation, execute the following command to know about the current DNVM version.

{% highlight text %}


C:\Users> dnvm



{% endhighlight %}



![](getting-started_images/getting-started_img101.jpeg)

*  Download the **DNX (.NET Execution Environment)** to your local machine with the help of already installed **DNVM** by executing the following command as given below.

{% highlight text %}


C:\Users> dnvm upgrade



{% endhighlight %}



![](getting-started_images/getting-started_img102.jpeg)

*  After this installation is completed, run the below command which will list out the DNX version installed in your local machine. 

N> The default version is marked with asterisk (*) symbol.

{% highlight text %}


C:\Users> dnvm list



{% endhighlight %}



![](getting-started_images/getting-started_img103.jpeg)

*  If the asterisk symbol is not marked to any specific installed DNX version, you need to update the default one to latest DNX version by execute the following command in prompt window.

{% highlight text %}


C:\Users> dnvm use 1.0.0-rc1-update2 -p



{% endhighlight %}



![](getting-started_images/getting-started_img104.jpeg)

*  Execute the **dnvm list** command to identify the modified active DNX version.

{% highlight text %}


C:\Users> dnvm list



{% endhighlight %}

*  Please ensure whether the changes are got reflected in your local machine by checking the **default.txt** file which is available in the following location. This should contain the version same as the default active version that you have selected.

{% highlight text %}


C:\Users\{user name}\.dnx\alias



{% endhighlight %}





### Deploying the ASP.NET MVC 6 Sample

 The following steps helps to know how to run the ASP.NET MVC 6 sample.

*  Open the **Visual Studio 2015**.

*  Select **File - > New Project**.

*  Choose **Templates -> Visual C# -> ASP.NET Web Application**.

*  Specify the name and location for the project.

*  Select the **Web Application** option from an **ASP.NET 5 Template**.

![](getting-started_images/getting-started_img105.jpeg)

*  Click OK to create the ASP.NET MVC 6 application.

*  In Solution Explorer window, right click the project name and choose the “**Properties**” option.

*  In that property window, open the application tab and choose the latest DNX version (list out the existing configured version) from the Solution SDK DNX Version combo box, then save the project.

*  Select the **Tools -> NuGet Package Manager -> Package Manger Settings -> Package Manager**.

*  In this Package Sources window, you need to add the MVC 6 related online feed link and click OK button to complete the configuration. (This online feed will helps to download an unavailable packages in local machine that may be used in your application)

![](getting-started_images/getting-started_img106.jpeg)



*  Press F5 or click the **IIS Express** option to deploy and run your web application project.



![](getting-started_images/getting-started_img107.jpeg)





### Deploying Syncfusion components into ASP.NET MVC 6 Application

After successfully configured ASP.NET MVC 6 to your local machine, refer the below steps to deploy our Syncfusion components into ASP.NET MVC 6 Web applications. Before follow the below guidelines, please make sure that you have installed our latest [Essential Studio ASP.NET MVC](http://www.syncfusion.com/downloads/aspnetmvc) setup in your machine.



[Follow the steps which is mentioned in “**Deploying the ASP.NET MVC 6 Sample**” to create and configure the MVC 6 application]

*  Open the **project.json** file from the solution explorer window and type our **Syncfusion NuGet** Packages as mentioned below,

![](getting-started_images/getting-started_img108.jpeg)



*  After this NuGet package references, save the **project.json** file to include the two Syncfusion packages to your application.

![](getting-started_images/getting-started_img109.jpeg)



*  Now open **_viewImports.cshtml** file from the views folder and add the following namespace for components references and Tag Helper support.



{% highlight text %}


@using Syncfusion.JavaScript

@addTagHelper "*, Syncfusion.EJ"



{% endhighlight %}




* To render the Syncfusion MVC controls with its unique style and theme, it is necessary to refer the required CSS files into your application. You need to copy all the required CSS files into your application from the following location,

`(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\MVC\samples\web\content`


_**For** **example**, If you have installed the Essential Studio package within **C:\Program Files (x86),** then navigate to the below location,_
`C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\MVC\samples\web\content`



When you navigate to the above location, you can find the folder “**ejthemes**” shown in the below image, which you need to copy entirely and paste it into your root application.



![](getting-started_images/getting-started_img110.jpeg)

Before pasting it into your application, you need to traversal within the **wwwroot\css** folder of your application and place all the copied files into it as shown below,

![](getting-started_images/getting-started_img111.jpeg)

To refer the below CSS stylesheet in your application in **layout.cshtml** page to render our components properly.

{% highlight razor %}


<html>
<head>
    <link href="@Url.Content("~/css/ejthemes/default-theme/ej.widgets.all.min.css")" rel="stylesheet"/>
</head>
</html>


{% endhighlight %}



* Adding the required JavaScript files into your application plays an important role, without which the Syncfusion controls cannot be created. It requires the following mandatory common script files,

    *   jQuery-1.10.2.min.js

    *   jquery.easing.1.3.min.js

    *   jsrender.min.js

Apart from the above common scripts, it is also necessary to refer the **ej.web.all.min.js** file in your application, which contains all JavaScript components scripts in minified format.

You need to copy the above specified 4 external script files into your application from the following location,

`(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\MVC\samples\web\content`

_**For example**, If you have installed the Essential Studio package within **C:\Program Files (x86),** then navigate to the below location,_
`C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\MVC\samples\web\scripts`

![](getting-started_images/getting-started_img112.jpeg)



Before pasting it into your application, now you need to traversal within the **wwwroot** folder and create a folder named “**scripts**” of your application and place all the copied files into it as shown below,

![](getting-started_images/getting-started_img113.jpeg)



Refer the below mandatory Script files in the **layout.cshtml** page to render our components properly. 



{% highlight razor %}


<head>
    <link href="@Url.Content("~/css/ejthemes/flat-saffron/ej.widgets.all.min.css")" rel="stylesheet"/>
    <script src="@Url.Content("~/Scripts/jquery-1.11.3.min.js")"></script>
    <script src="@Url.Content("~/scripts/jsrender.js")"></script>
    <script src="@Url.Content("~/scripts/jquery.easing-1.3.min.js")"></script>
    <script src="@Url.Content("~/scripts/ej.web.all.min.js")"></script>
</head>


{% endhighlight %}



N> Also completely remove the already referred scripts and themes within the **environment** tag. The order of the reference to the script files made in the above section should be maintained in the same manner as mentioned above.

I> Since the **jquery-1.11.3.min.js** file is referred explicitly in the application, therefore make sure that your application doesn’t refer to any other jQuery versions multiple times, which will cause the script error. Make sure that the jQuery scripts are not again referred through bundles in **_Layout.cshtml** file.

*  Add **ScriptManager** to the bottom of the **layout.cshtml** page. The ScriptManager used to place our control initialization script in the page. 



{% highlight c# %}


<ej-script-manager></ej-script-manager> 



{% endhighlight %}



*  Open your view page to render Syncfusion components with ASP.NET MVC 6 Tag Helper syntax.



{% highlight c# %}


<ej-rating id="DefaultRating" value="3" />



{% endhighlight %}



*  Finally compile your project, after successful compilation then press F5 key to deploy your project.



![](getting-started_images/getting-started_img114.jpeg)



## Integration of Syncfusion MVC components into an existing MVC Application using Project Conversion Wizard

In order to achieve the conversion of normal MVC application into Syncfusion MVC application, it is mandatory that you need to install the MVC extension in your machine as mentioned in the **Project** **Template** topic. To add the Syncfusion MVC controls into an existing ASP.NET MVC application, refer the below steps,

Open your existing MVC application from **File** -> **Open** -> **Project/Solution** and right click on your project in the Solution Explorer.

In the context menu that pops up, select the option **Syncfusion** **VS** **Extensions** -> **Convert** **to** **Syncfusion** **MVC** **Application**. Now the **Project** **Conversion** **Wizard** pops up as shown below,

![](getting-started_images/getting-started_img94.jpeg)

Make appropriate selection in it and click **Next** button, which again opens the next options to be chosen as shown below,

![](getting-started_images/getting-started_img95.jpeg)

Select your required control in it and click **Create**, so that all the required assemblies, scripts & CSS references needed to render the control will get automatically added to your existing project and also the configurations in web.config will also be done automatically. 

Ensure whether the **Unobtrusive** setting is enabled in your application’s web.config file. If it is enabled, then you need to change its value to **false** in your application as shown below,

{% highlight html %}

<appSettings>
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="false" />
</appSettings>

{% endhighlight %}

N> If suppose, you require the Unobtrusive to set to **true** in your application, then you need to include the **ej.unobtrusive.min.js** file as a reference to your application.

Since, the Unobtrusive setting in the web.config file is disabled now, therefore it is necessary to add the script manager in your application to render the controls properly. Add the below script manager code in the **_Layout.cshtml** file present within the **~/Views/Shared** folder of your application as shown below,

{% highlight razor %}

<body>
    … 
    … 
    @RenderSection("scripts", required: false) 
    @Html.EJ().ScriptManager()
</body>

{% endhighlight %}

N> The main reason for referring the Script manager in _Layout file is that, it can be referred as common by all the View files present within your application. If **unobtrusive** is set to true in the application, then the script manager can be excluded, as the control is initialized using HTML5 attributes.

In the next step, the script and CSS files has to be explicitly referred in the head section of the **_Layout.cshtml** page of your existing application as shown below,

{% highlight razor %}

<head>
    <meta charset="utf-8" />
    <title>@ViewBag.Title - My ASP.NET MVC Application</title>
    … 
    …
    <link href="@Url.Content("~/Content/ej/web/default-theme/ej.web.all.min.css")" rel="stylesheet" />
</head>

<body>
    … 
    …
    <script src="@Url.Content("~/Scripts/jquery-1.10.2.min.js")"></script>
    <script src="@Url.Content("~/Scripts/jquery.easing.1.3.min.js")"></script>
    <script src="@Url.Content("~/Scripts/jsrender.min.js")"></script>
    <script src="@Url.Content("~/Scripts/ej/ej.web.all.min.js")"></script>
    @Html.EJ().ScriptManager() 
    @RenderSection("scripts", required: false)
</body>

{% endhighlight %}

N> The order of the reference to the script files made in the above section should be maintained in the same manner as mentioned above.

I> Since the **jquery-1.10.2.min.js** file is referred explicitly in the application, therefore make sure that your application doesn’t refer to any other jQuery versions multiple times, which will cause the script error. Make sure that the jQuery scripts are not again referred through bundles in **_Layout.cshtml** file.

Now you can add the below **DatePicker** code in the **Index.cshtml** file present within **~/Views/Home** folder.

{% highlight razor %}

    @Html.EJ().DatePicker("MyFirstDatePicker")

{% endhighlight %}

Simply build and run the project by pressing F5, so that you can now see the output similar to the below screenshot in your web browser,

![](getting-started_images/getting-started_img96.jpeg)

Thus the **DatePicker** control is rendered successfully with its default appearance.

## Upgrading Syncfusion MVC Project to newer Syncfusion Essential Studio Version using MVC Project Migration Wizard

The existing Syncfusion MVC project can be migrated to the newer Essential Studio versions using **MVC** **Project** **Migration** **Wizard**. In order to achieve this, it is mandatory that you need to install the MVC extension in your machine as mentioned in the **Project** **Template** topic. Follow the below steps to upgrade your existing Syncfusion MVC project to newer versions,

Open your existing **Syncfusion** **MVC** **Project** (For example, the MVC Project created with the older Syncfusion version 12.4.0.24) from **File** -> **Open** -> **Project/Solution** and right click on your project in the Solution Explorer.

In the context menu that pops up, select the option **Syncfusion** **VS** **Extensions** -> **Migrate** **the** **Project** **to** **Another** **Version** as shown in the below option,

![](getting-started_images/getting-started_img97.jpeg)

Now the Migration window titled **MVC** **Project** **Migration** **wizard** will gets opened as shown below, to choose the required Syncfusion version which is installed in your machine and click **Migrate** button.

![](getting-started_images/getting-started_img98.jpeg)

The option **Backup** in the above window will copy the original project (with older version) into the **Backup** folder of the same project location where the newly migrated project is placed.

Now the corresponding Syncfusion assembly version references, CSS, Script files and also the web.config version changes will be added and reflected automatically in the newly migrated project. You can simply build and run your migrated project by pressing **F5**.

N> i. Since we are migrating the older **Syncfusion** **MVC** **project** here, therefore we assume that all the required script and CSS references are already configured in the _Layout.cshtml page of your old project.
N> ii. Also, we assume that the Unobtrusive setting is set to **false** and also other assembly configurations & namespace reference are already present within the web.config file.
N> iii. Also, ensure the presence of **ScriptManager** code in the _Layout.cshtml page of your old project. 

In case, if the above specified settings are not present in your MVC project, then include in into the project by following the steps mentioned in the **Project** **Conversion** **Wizard** topic.

## To Enable Unobtrusive option in your Application

We have already seen that the unobtrusive option is enabled by default during the initial MVC application creation. When this option is set to **true** in the web.config file, the control usually renders with the HTML5 attributes and also the reference to the **ej.unobtrusive.js** file needs to be included in the application.

If you explicitly set this option to **false**, then the control rendering takes place through scripts, which requires the usage of script manager in your application.

Normally, the unobtrusive option is set in the application’s root web.config file as shown below,

{% highlight html %}

<appSettings>
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
</appSettings>

{% endhighlight %}

To include the **ej.unobtrusive.min.js** file in your application, with unobtrusive option set to true in the web.config - refer the following steps,

Navigate to the below specified installed location,

`(installed location)\ Syncfusion\Essential Studio\{{ site.releaseversion }}\JavaScript\assets\scripts\common`

_**For** **example**, If you have installed the Essential Studio package within **C:\Program Files (x86),** then navigate to the below location,_ 
`C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\JavaScript\assets\scripts\common`

Copy the **ej.unobtrusive.min.js** file from that location as shown in the below image and paste it into the `ej/web` folder present within the `Scripts` folder of your application.

![](getting-started_images/getting-started_img99.jpeg)

Include the reference to the added **ej.unobtrusive.min.js** file in the **_Layout.cshtml** page as shown below,

{% highlight razor %}

<head>
    <meta charset="utf-8" />
    <title>@ViewBag.Title - My ASP.NET MVC Application</title>
    … 
    …
    <link href="@Url.Content("~/Content/ej/web/default-theme/ej.web.all.min.css")" rel="stylesheet" />
</head>

<body>
    … 
    …
    <script src="@Url.Content("~/Scripts/jquery-1.10.2.min.js")"></script>
    <script src="@Url.Content("~/Scripts/jquery.easing.1.3.min.js")"></script>
    <script src="@Url.Content("~/Scripts/jsrender.min.js")"></script>
    <script src="@Url.Content("~/Scripts/ej/web/ej.web.all.min.js")"></script>
    <script src="@Url.Content("~/Scripts/ej/web/ej.unobtrusive.min.js")"></script>
    @Html.EJ().ScriptManager() 
    @RenderSection("scripts", required: false)
</body>

{% endhighlight %}

N> The **ej.unobtrusive.min.js** script reference should be included after the reference of **ej.web.all.min.js** file in _Layout.cshtml file. The order should be maintained the same as we have specified above.

## Convert to Synctusion Project

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