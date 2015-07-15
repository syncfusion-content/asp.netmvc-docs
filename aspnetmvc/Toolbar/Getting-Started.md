---
layout: post
title: Getting-Started
description: getting started
platform: ejmvc
control: Toolbar
documentation: ug
---

# Getting Started

This section explains briefly about how to create a Toolbar in your ASP.NET MVC application. 

## Create your first Toolbar in MVC

Create Toolbar for PDF Reader

Toolbar control displays a list of tools in a webpage. It is used to customize Toolbar items of any functionality, by using enriched client-side methods. This control consists of a collection of unordered lists, containing text and images into a &lt;div&gt;. From the following section, you can learn how to customize Toolbar control for a PDF Reader scenario. The following screen shot shows the appearance of Toolbar in PDF Reader simulator application.

Here, the Toolbar consists of a Toolbar with title and text area as PDF Reader.

{ ![C:/Users/Rajaveni/Desktop/rte final/toolbar - Copy.PNG](Getting-Started_images/Getting-Started_img1.png) | markdownify }
{:.image }




Create a Toolbar

Using the following steps, you can create a Toolbar control. The basic rendering of ASP.NET MVC Toolbar is achieved with default functionality.



1. You can create an MVC Project and add necessary Dll and script with the help of the given [MVC-Getting Started](http://help.syncfusion.com/ug/js/Documents/gettingstartedwithmv.htm) Documentation.



2. Add the mentioned code to the corresponding view page for Toolbar rendering.



[CSHTML]     

@Html.EJ().Toolbar("ToolbarItem")





The following output is displayed.



{ ![](Getting-Started_images/Getting-Started_img2.png) | markdownify }
{:.image }




_Figure 2: Toolbar without Toolbar items_

Initialize Toolbar Items

Toolbar consists of a list of items. From the following guidelines, you can learn how to initialize the Toolbaritems with &lt;UL&gt; &lt;LI&gt; template. 								

Initialize the Toolbaritems with &lt;UL&gt; &lt;LI&gt; template as follows. 

[CSHTML]

&lt;div id="ToolbarItem"&gt;

    &lt;!--list of toolbar items--&gt;



    &lt;ul&gt;

        &lt;li id="OtherFormat" title="Convert PDF files to Word or Excel Online…"&gt;

            &lt;div class="PdfDocument e-icon convertToOthers "&gt;&lt;/div&gt;

        &lt;/li&gt;

        &lt;li id="PDFOnline" title="Convert files to PDF Online"&gt;

            &lt;div class="PdfDocument e-icon convertToPdf "&gt;&lt;/div&gt;

        &lt;/li&gt;

        &lt;li id="Signature" title="Sign, add text or send a document for signature"&gt;

            &lt;div class=" PdfDocument e-icon signature "&gt;&lt;/div&gt;

        &lt;/li&gt;

        &lt;li id="Save" title="Save file ( Ctrl+S )"&gt;

            &lt;div class=" PdfDocument e-icon save "&gt;&lt;/div&gt;

        &lt;/li&gt;

        &lt;li id="Print" title="Print file ( Ctrl+P ) "&gt;

            &lt;div class=" PdfDocument e-icon print "&gt;&lt;/div&gt;

        &lt;/li&gt;



        &lt;li id="Message" title="Message"&gt;

            &lt;div class=" PdfDocument e-icon msg "&gt;&lt;/div&gt;

        &lt;/li&gt;

    &lt;/ul&gt;

&lt;/div&gt;

    @Html.EJ().Toolbar("ToolbarItem").Width("auto").EnableSeparator(true).Height("33px")





Apply the given styles in the code table to show the Toolbar items as follows. You can refer images from any location. For the following code example, the images have been referred from the given location.

[http://js.syncfusion.com/UG/Web/Content/](http://js.syncfusion.com/UG/Web/Content/)pdf-icon.png

.

[CSS]

&lt;style type="text/css" class="cssStyles"&gt;



    .e-tooltxt .e-icon {

        background-image: url('http://js.syncfusion.com/UG/Web/Content/pdf-icon.png');

        background-repeat: no-repeat;

        display: block;

        height: 30px;

        width: 30px;

    }



    .convertToOthers {

        background-position: -349px 0px;

    }



    .convertToPdf {

        background-position: -527px 0px;

    }



    .signature {

        background-position: 2px 0px;

    }



    .save {

        background-position: -87px 0px;

    }



    .print {

        background-position: -43px 0px;

    }



    .msg {

        background-position: -483px 0px;

    }

&lt;/style&gt;





Execute the code to render a Toolbar with a list of Toolbar items.



{ ![](Getting-Started_images/Getting-Started_img3.png) | markdownify }
{:.image }


_Figure 3: Toolbar with list of toolbar items_



Render remaining Toolbar Items

To achieve the requirements, you need to render all the Toolbar items. You can separate or group the Toolbar items. The separation or grouping of Toolbar items is achieved when you give Toolbar items as a list of &lt;UL&gt; &lt;LI&gt; values inside the toolbar &lt;div&gt; or span element. From the following sections, you can learn how to initialize the remaining Toolbar items with &lt;UL&gt; &lt;LI&gt; template and how to group the toolbar items. 

Initialize the Toolbar items with &lt;UL&gt; &lt;LI&gt; template as follows.





&lt;div id="ToolbarItem"&gt;



    &lt;!--Initialize toolbar items from above code snippet --&gt;



    &lt;!-- Separator will be added at the end of each ul inside the toolbar element--&gt;



    &lt;!-- list of Remaining toolbar items with item separator --&gt;



    &lt;ul&gt;

        &lt;li id="Previous" title="Show previous page ( Left Arrow )"&gt;

            &lt;div class=" PdfDocument e-icon previous "&gt;&lt;/div&gt;

        &lt;/li&gt;

        &lt;li id="Next" title="Show next page ( Right Arrow )"&gt;

            &lt;div class="PdfDocument e-icon next "&gt;&lt;/div&gt;

        &lt;/li&gt;

        &lt;li id="page"&gt;

            &lt;div class="PdfDocument"&gt;

                &lt;input type="text" value="1" /&gt;

            &lt;/div&gt;

        &lt;/li&gt;

        &lt;li id="count"&gt;

            &lt;span&gt;/ 1</span>&lt;/li&gt;

    &lt;/ul&gt;



    &lt;ul&gt;

        &lt;li id="ZoomOut" title="Zoom Out"&gt;

            &lt;div class=" PdfDocument e-icon zoomOut "&gt;&lt;/div&gt;

        &lt;/li&gt;

        &lt;li id="ZoomIn" title="Zoom In"&gt;

            &lt;div class=" PdfDocument e-icon zoomIn "&gt;&lt;/div&gt;

        &lt;/li&gt;

        &lt;li id="ZoomValue"&gt;

            &lt;div id="carlist"&gt;

                &lt;ul&gt;

                    <li>10%&lt;/li&gt;

                    <li>25%&lt;/li&gt;

                    <li>50%&lt;/li&gt;

                    <li>100%&lt;/li&gt;

                    <li>400%&lt;/li&gt;

                    <li>800%&lt;/li&gt;

                    <li>1600%&lt;/li&gt;

                    <li>3200%&lt;/li&gt;

                    <li>6400%&lt;/li&gt;

                &lt;/ul&gt;

            &lt;/div&gt;

            @Html.EJ().DropDownList("car").Width("90").Value("100%").TargetID("carlist")

        &lt;/li&gt;

    &lt;/ul&gt;



    &lt;ul&gt;

        &lt;li id="FitFull" title="Fit one full page to window"&gt;

            &lt;div class=" PdfDocument e-icon fitOne "&gt;&lt;/div&gt;

        &lt;/li&gt;



        &lt;li id="StickyNote" title="Add stick note ( Ctrl+6 ) "&gt;

            &lt;div class=" PdfDocument e-icon sticky "&gt;&lt;/div&gt;

        &lt;/li&gt;

        &lt;li id="ReadMode" title="View File in Read Mode"&gt;

            &lt;div class=" PdfDocument e-icon readMode "&gt;&lt;/div&gt;

        &lt;/li&gt;

    &lt;/ul&gt;



&lt;/div&gt;



Add the following styles in the code table to display the Toolbar items as follows. 





    /*Additional style for Remaining toolbar items*/

&lt;style&gt;

    .zoomIn {

        background-position: -175px 0px;

    }

    .readMode {

         background-position: -307px -1px;

    }

    .zoomOut {

        background-position: -219px 0px;

    }



    .fitOne {

        background-position: -264px 0px;

    }



    .sticky {

        background-position: -131px -1px;

    }



    #ZoomValue.e-tooltxt .e-icon {

        background-image: none;

    }



    #page .PdfDocument input {

        text-align: center;

        width: 20px;

        height: 21px;

    }



    #count span {

        width: 30px;

        height: 30px;

        position: relative;

        top: 2px;

        text-align: center;

        vertical-align: middle;

        background-image: none;

    }



    .PdfDocument.e-icon.previous {

        background-position: -395px 0px;

    }



    .PdfDocument.e-icon.next {

        background-position: -439px 0px;

    }

&lt;/style&gt;



Set Zoom value is one of the items in the Toolbar. You need to render the DropDownList control for select zoom value. DropDownList control is rendered with &lt;UL&gt; &lt;LI&gt; elements. The ASP.NET MVCDropdown control with a list of zoom values is used to render Set Zoom value in the above sample code. Refer to the provided link for Dropdown creation.

[Dropdown – GettingStarted](http://help.syncfusion.com/aspnetmvc/)

Execute the code to render Toolbar items with separator.



{ ![C:/Users/Rajaveni/Desktop/rte final/itemssssssssssssss.PNG](Getting-Started_images/Getting-Started_img4.png) | markdownify }
{:.image }


Add Actions to Toolbar Items

Now that the Toolbar is rendered, you need to render the header and content area to create a PDF Reader. In the following section, you can learn how to render the header (Toolbar), contentsection (PDF viewer area) and how to set the action to Toolbar items.

{ ![C:/Users/labuser/Desktop/note.jpg](Getting-Started_images/Getting-Started_img5.jpeg) | markdownify }
{:.image }
_Note: PDF reading or rendering is not shown here. Simulation of the PDF Reader app to demonstrate the usage of Toolbar control is provided. PDF rendering area is ignored._



Initialize the contentarea and header as specified in the code table.



&lt;!—“control” class used for aligns the pdf reader in center of a page. --&gt;

&lt;div class="control"&gt;



    &lt;div class="ctrllabel"&gt;&lt;/div&gt;

    &lt;div id="ToolbarItem"&gt;



    &lt;!--Add toolbar items from above code snippet --&gt;



    &lt;/div&gt;



    &lt;!-- Here Initialize the Toolbar items as like above code sample --&gt;



    &lt;div id="contentSection"&gt;

        &lt;textarea id="content" rows="10" cols="30"&gt; 

   Description:

   Toolbar control supports displaying a list of tools within a Web page. This control is capable of 

   customizing toolbar items with any functionality by using enriched client-side methods.This control 

   Is composed of collection of unordered lists containing text and images contained into a div.

&lt;/textarea&gt;

    &lt;/div&gt;



&lt;/div&gt; 



You can apply the following styles with the above styles to design the PDF header and content area. 





&lt;style type="text/css" class="cssStyles"&gt;

    #content {

        float: left;

        height: 300px;

        width: 633px;

        position: absolute;

    }



    .control {

        position: relative;

    }



    .ctrllabel {

        background-image: url('http://js.syncfusion.com/UG/Web/Content/pdf-header.png');

        background-repeat: no-repeat;

        width: 638px;

        height: 32px;

    }

&lt;/style&gt;

{ ![C:/Users/Rajaveni/Desktop/rte final/edited.PNG](Getting-Started_images/Getting-Started_img6.png) | markdownify }
{:.image }












_Figure 5: PDF Reader Appearance_

So far, you have added the required toolbar items and configured its appearance. When you click on 

Toolbar items, the operation is performed through client-slide click event. The following code example explains how to perform operations, when you click on the Toolbar items.



[View]

&lt;div id="ToolbarItem"&gt;



    &lt;!--Add toolbar items from above code snippet --&gt;



&lt;/div&gt;



&lt;!-- Here Initialize the Toolbar items as shown in above code sample and add Client side Event as follows --&gt;



@Html.EJ().Toolbar("ToolbarItem").ClientSideEvents(e => e.Click("onItemclick")).Width("auto").EnableSeparator(true)







&lt;script type="text/javascript"&gt;



    function onItemclick(args) {





        //Finds Out the Item that was Clicked in Toolbar





        //args.currentTarget returns the clicked Toolbar element





        var option = args.currentTarget.id; /* Find Out the Id of Clicked item. */







        switch (option) {



            case "OtherFormat":



                //writes a code for Convert pdf files to Other format.



            case "PdfOnline":



                //writes a code for Convert files to Pdf online.



            case "Signature":



                //writes a code for Send a document for signature.



            case "Save":



                //writes a code for Save content.



            case "Print":



                //writes a code for Print content.



            case "Message":



                //writes a code for Send a Message.



            case "Previous":



                //writes a code for Show previous page.



            case "Next":



                //writes a code for Show Next page.



            case "ZoomOut":



                //writes a code for Zoom out the page.



            case "ZoomIn":



                //writes a code for Zoom In the page.



            case "FitFull":



                //writes a code for Fit one full page to window.



            case "StickyNote":



                //writes a code for Add Sticky Note.



            case "ReadMode":



                //writes a code for view file in read mode.

        }



    }



&lt;/script&gt;





