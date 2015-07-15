---
layout: post
title: Getting-Started
description: getting started
platform: ejmvc
control: RangeNavigator
documentation: ug
---

# Getting Started

This section explains briefly about how to create a RangeNavigator in your ASP.NET MVC application.

## Create your first RangeNavigator in MVC

This section encompasses the details on how to configure the RangeNavigator and update the chart control for RangeNavigator’s selected range. It also helps you to learn how to pass the required data to RangeNavigator and customize the scale and selected range for your requirements. In this example, you will learn how to configure the RangeNavigator to analyse sales of a product for a particular quarter in a year.



{ ![](Getting-Started_images/Getting-Started_img1.png) | markdownify }
{:.image }


Create a simple MVC Application for RangeNavigator

 You can create a new ASP.NET MVC project Razor Application.

1. On the File menu, click New Project. The New Project dialog box opens.

{ ![](Getting-Started_images/Getting-Started_img2.png) | markdownify }
{:.image }


2. On the upper-right corner, select .NET Framework 4.0.
3. In the Installed Templates pane, expand either Visual Basic or Visual C# and then click Web.
4. In the Visual Studio Installed Templates pane, select ASP.NET MVC 4 Web Application.
5. In the Name box, enter MvcSample
6. In the Location box, enter a name for the project folder.
7. If you want the name of the solution to differ from the project name, then enter a name in the Solution name box.
8. Select the Create directory for solution checkbox.
9. Click OK.
10. The New ASP.NET MVC4Project dialog box opens.



{ ![](Getting-Started_images/Getting-Started_img3.png) | markdownify }
{:.image }


11. In the Project Template group, select the Internet Application template for MVC4 project.
12. Check the Create a unit test project checkbox, if you want to create a unit test project.
13.  Click OK. The new MVC application project is generated.

The following screenshot shows the folder structure of the newly created MVC project.



{ ![](Getting-Started_images/Getting-Started_img4.png) | markdownify }
{:.image }




14. Adding Reference Assemblies
* On the Solution Explorer, right-click the References folder and then click Add Reference. The Add Reference dialog box appears.



{ ![](Getting-Started_images/Getting-Started_img5.png) | markdownify }
{:.image }


_Figure 5: Adding Reference Assemblies_

* Add the following Syncfusion assemblies : 
1. Syncfusion.Core
2. Syncfusion.EJ
3. Syncfusion.EJ.MVC



{ ![](Getting-Started_images/Getting-Started_img6.png) | markdownify }
{:.image }




{ ![](Getting-Started_images/Getting-Started_img7.png) | markdownify }
{:.image }


15.  You can add required Scripts and ScriptManger in _Layout page
* Add the script references of the required libraries in the _Layout page as shown in the following code sample



[HTML]



&lt;!DOCTYPE html&gt;

&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;

&lt;head&gt;



&lt;script src="@Url.Content("~/Scripts/jquery-1.10.2.min.js")" type="text/javascript"&gt;&lt;/script&gt;

&lt;script src="@Url.Content("~/Scripts/jquery.globalize.min.js")" type="text/javascript" &gt;&lt;/script&gt;

&lt;script src="@Url.Content("~/Scripts/ej.web.all.min.js")" type="text/javascript"&gt;&lt;/script&gt;

 &lt;script src="@Url.Content("~/Scripts/ej.unobtrusive.min.js")" type="text/javascript"&gt;&lt;/script&gt;



&lt;/head&gt;



* Add the ScriptManager() at the end of &lt;body&gt; tag in _Layout page.

[HTML]

&lt;!DOCTYPE html&gt;

&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;

&lt;head&gt;



&lt;/head&gt;

&lt;body&gt;

    @(Html.EJ().ScriptManager())

&lt;/body&gt;

&lt;/html&gt;



16. Configure web.config files for assemblies
* The following assemblies references are added properly in web.config file (There will be two web.config files. Refer to the one in the root folder.).  

[Web.config]

  &lt;compilation debug="true" targetFramework="4.0" &gt;

  &lt;assemblies&gt;       

&lt;add assembly="Syncfusion.Core, Version=XX.XXXX.X.X, Culture=neutral, PublicKeyToken=632609B4D040F6B4" /&gt;



&lt;add assembly="Syncfusion.EJ, Version= XX.XXXX.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" /&gt;



&lt;add assembly="Syncfusion.EJ.Mvc, Version= XX.XXXX.X.X, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" /&gt;

&lt;/assemblies&gt;

  &lt;/assemblies&gt;


{ ![](Getting-Started_images/Getting-Started_img8.png) | markdownify }
{:.image }
_Note: Add the following namespaces in web.config file within the Views folder._



[Web.config] – Views folder



&lt;namespaces&gt;

        &lt;add namespace="System.Web.Mvc" /&gt;

        &lt;add namespace="System.Web.Mvc.Ajax" /&gt;

         …….

         …….

        &lt;add namespace="Syncfusion.JavaScript" /&gt;

        &lt;add namespace="Syncfusion.JavaScript.DataVisualization" /&gt;

        &lt;add namespace="Syncfusion.MVC.EJ" /&gt;

        &lt;add namespace="Syncfusion.EJ" /&gt;

&lt;/namespaces&gt;




The above steps are done automatically, if you create your project with the help of MVC Project creation template, which is available once the MVC Extension is installed on your machine.

Configure RangeNavigator

Getting started with your MVC RangeNavigator is simple; all you need to do is initialize the RangeNavigator by setting range values.

1. Create a simple &lt;div&gt; tag.

&lt;div&gt;  &lt;/div&gt;



2. Add the following code in the SimpleRangeNavigator.cshtml file, to create the RangeNavigator control in the View page. 

The following code example renders a RangeNavigator with a range from 2010 January 1st to December 31st.

    &lt;div&gt; 





           @(Html.EJ().RangeNavigator("scrollcontent")



           .RangeSettings(range=>range.Start("2010/1/1").End("2010/12/31"))



           .Render()) 



    &lt;/div&gt;  



     3.   Open ~/Controllers/HomeController.cs.

     4.   Add the SimpleRangeNavigator() action as illustrated in the following code example.



[Controller]

 public ActionResult SimpleRangeNavigator()

{

return View();

}


The following Screen shot displays the RangeNavigator with a range from 2010 January 1st to December 31st.

{ ![](Getting-Started_images/Getting-Started_img9.png) | markdownify }
{:.image }


Add series

To add a series to RangeNavigator, you need to set DataSource property, as given in the following code example. 

You can add JSON data to the RangeNavigator using the Datasource property.

In Controllers/HomeController.cs specify the data for data source.

[cs]



public ArrayList GetData()

        {

            ArrayList dataTable = new ArrayList();



            dataTable.Add(new NavigatorData (new DateTime(2011, 01, 01), 10));

            dataTable.Add(new NavigatorData (new DateTime(2011, 02, 01), 5));

            dataTable.Add(new NavigatorData (new DateTime(2011, 04, 01), 15));

            dataTable.Add(new NavigatorData (new DateTime(2011, 06, 01), 25));

            dataTable.Add(new NavigatorData (new DateTime(2011, 08, 01), 10));

            dataTable.Add(new NavigatorData (new DateTime(2011, 10, 01), 5));

            dataTable.Add(new NavigatorData (new DateTime(2011, 12, 31), 15));   

            return dataTable;

        }



        class NavigatorData

        {



            private DateTime xdate;



            public DateTime xDate

            {

                get { return xdate; }

                set { xdate = value; }

            }



            private double yvalue;



            public double yValue

            {

                get { return yvalue; }

                set { yvalue = value; }

            }



            public NavigatorData(DateTime xdate, double yvalue)

            {



                this.xdate = xdate;



                this.yvalue = yvalue;