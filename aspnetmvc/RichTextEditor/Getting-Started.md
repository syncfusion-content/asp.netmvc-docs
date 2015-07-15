---
layout: post
title: Getting-Started
description: getting started
platform: ejmvc
control: RichTextEditor
documentation: ug
---

# Getting Started

This section briefly describes how to create and use RichTextEditor control using MVC in your application.

## Create your first RichTextEditor in MVC

The ASP.NET MVC RichTextEditor (RTE) control allows you to edit contents, insert tables, images and to get the HTML content. In this section you can learn how to use RichTextEditor in order to get Feedback from the user. 

{ ![](Getting-Started_images/Getting-Started_img1.png) | markdownify }
{:.image }
The following screenshot demonstrates how the RTE control is used in Feedback form.

In the above screenshot , the RTE consists of content editable area with Feedback title.In this RTE application, you can click the PostFeedback toolbar item to send the Feedback information.

Create a RichTextEditor 

ASP.NET MVC RTE widget basically renders by using the simple text area element. 

1. You can create a MVC Project and add the necessary Dll’s and scripts with the help of the given [MVC-Getting Started](http://help.syncfusion.com/ug/js/Documents/gettingstartedwithmv.htm) Documentation.
2. Add the following code example to the corresponding view page to render the RichTextEditor.





@Html.EJ().RTE("FeedbackEditor")



{ ![](Getting-Started_images/Getting-Started_img2.png) | markdownify }
{:.image }
The following RTE screenshot renders the output of the above steps.

Configure the Toolbar

The RichTextEditor configures the toolbar items to provide editing and styling functionalities. In this scenario, you can use the default RTE toolbar item to provide Feedback form support. 

Add the Toolbar Item

The additional functionality toolbar item is necessary to perform the required operation. The RTE provides some additional toolbar items that are already predefined, but not rendered in without specifying the toolbar items.  

The following code example renders the additional inbuilt toolbar items to RTE toolbar list.





@{

    List<string> font = new List<string>() { "fontName", "fontSize","fontColor"  };

}



@Html.EJ().RTE("FeedbackEditor").Tools(tool => tool.Font(font)) 



{ ![](Getting-Started_images/Getting-Started_img3.png) | markdownify }
{:.image }
 The following screenshot displays the RTE with inbuilt toolbar item.



Remove the ToolbarItem

Sometimes, an existing toolbar item is not necessary to perform the required operation. You can remove the particular toolbar item by using the remove ToolbarItem method. 

For example, consider ‘create table’ toolbar item is not necessary for the Feedback scenario. You can easily remove the ‘create table’ toolbar item by using the following code example.



[CSHTML]

@Html.EJ().RTE("FeedbackEditor")





&lt;script type="text/javascript"&gt;

    var editorObj;

    $(function () {

        $("#FeedbackEditor").ejRTE();

        editorObj = $("#FeedbackEditor").data('ejRTE');

        //remove the create table toolbar item by specifying the create table toolbar id

        editorObj.removeToolbarItem("FeedbackEditorcreateTable");

    });



&lt;/script&gt;



The following screenshot displays ‘create table’ toolbar item is removed from the toolbar list.



{ ![](Getting-Started_images/Getting-Started_img4.png) | markdownify }
{:.image }


Configure Custom Toolbar item

To post the Feedback directly, you need additional Toolbar item. The RTE control provides support to create the custom toolbar item for custom action. 

The following code example creates the custom toolbar item in the RTE control. 



@Html.EJ().RTE("FeedbackEditor").Width("820px").Tools(tool => tool.CustomTool(custom =>

                    custom.Name("PostFeedback").Tooltip("click to Post Feedback messages").Css("Feedback").Add()))





  Add the following styles for the customtoolbaritem.

&lt;style&gt;

    .Feedback {

        height: 22px;

        width: 100px;

        display: block;

        text-align: center;

        font-weight: bold;

    }

&lt;/style&gt; 



The following screenshot displays RTE with custom toolbar item.

{ ![](Getting-Started_images/Getting-Started_img5.png) | markdownify }
{:.image }


Validate the Content

In some cases, to send the Feedback form without contents you can validate them before submitting the Feedback contents. To achieve this validation, you can use getText() method in RTE control.

When the content area is empty, you can set the notification message displayed in the &lt;div&gt; element area in order to give an alert message. The following HTML code example creates the Feedback form editor with the support of RTE control.

During the Feedback sending time, you can validate whether the content area is empty or not. To achieve this validation, you can use RTE client-side events. RTE provides the ‘action’ function to perform the client-side events to custom tool.

You can specify the custom tool same as previous section with validation operations.





&lt;div class="commentSection" style="width: 810px"&gt;

    &lt;div class="titleSection"&gt;

        <label>Title:&lt;/label&gt;

        &lt;input type="text" class="input ejinput" /&gt;

    &lt;/div&gt;

    &lt;!--RTE element section--&gt;



@Html.EJ().RTE("FeedbackEditor").Width("100%").ClientSideEvents(cs=>cs.Change("change")).Tools(tool => tool.CustomTool(custom =>

                    custom.Name("PostFeedback").Tooltip("click to Post Feedback messages").Css("Feedback").Action("validate").Add()))



&lt;!-- validation message display area--&gt;

        &lt;div class="output"&gt;&lt;/div&gt;

&lt;/div&gt;





&lt;script type="text/javascript"&gt;

function validate() {

        var editorObj = $("#FeedbackEditor").data('ejRTE');

        if (($.trim(editorObj.getText()).length < 1)) {

            //the content area is empty

            $(".output").html("The Feedback content is empty");

        } else {   //the content area contains information

            $(".output").html("");

            //custom code to send the Feedback form contents 

            alert("The Feedback content has been saved");

        }

    }

&lt;/script&gt;





You can add the following styles to achieve the Feedback form editor application.

&lt;style&gt;

    .commentSection {

            width: 60%;

            background: none repeat scroll 0 0 #f9f9f1;

            border: 1px solid #e9e9e1;

            padding: 10px;

        }



        .titleSection {

            text-indent: 20px;

            float: left;

            padding: 20px 0px;

            width: 100%;

            border: 1px solid #bbbcbb;

        }



        .output {

            height: 20px;

            padding: 5px;

            color: red;

        }



        .titleSection .level {

            margin: 15px 0px 5px 0px;

        }



        .input.ejinput {

            text-indent: 5px;

            height: 24px;

            width: 80%;

            margin-left: 5px;

        }

&lt;/style&gt;



The following screenshot displays the Feedback sending without content.






{ ![](Getting-Started_images/Getting-Started_img6.png) | markdownify }
{:.image }


