---
layout: post
title: Template-Support
description: template support
platform: ejmvc
control: TreeView
documentation: ug
---

## Template Support

TreeView supports Template option to reduce code. We can specify the template structrure in which the TreeView should be rendered. We can define the template using JSRender also. The look of the default tree elements are completely modified by creating a specific template, defining how an element is going to be rendered. 

The following steps explains how to reder the TreeView using Template.

1. In the Controller page, add a class and define the properties (or) in the Models, add a class as shown below



[Model]

// Define local data source elements with  fields            



public class template

{

    public int id { get; set; }

    public int pid { get; set; }

    public string name { get; set; }

    public string city { get; set; }

    public bool hasChild { get; set; }

    public bool expanded { get; set; }

    public string phone { get; set; }

    public int imgId { get; set; }

}



2.  In the controller page, create a List of specified class type and specify the DataSource to render the TreeView.





[Controller]

//Refer the Model in the controller

using <Applicationname>.Models;



        public ActionResult TreeViewFeatures()

        {



            List<template> templateData = new List<template>();

            templateData.Add(new template { id = 1, name = "UK", hasChild = true, expanded = true });

            templateData.Add(new template { id = 2, pid = 1, imgId = 1, name = "Steven John", city = "London", phone = "555-5665-2323" });

            templateData.Add(new template { id = 3, name = "USA", hasChild = true, expanded = true });

            templateData.Add(new template { id = 5, pid = 3, imgId = 2, name = "Andrew", city = "Capital way", phone = "934-8374-2455" });

            templateData.Add(new template { id = 4, pid = 3, imgId = 3, name = "Angelica", city = "Dayton", phone = "988-4243-0806" });



            ViewBag.datasource = templateData;

            return View();



         }





3. In the View page, define the template structure in which the TreeView has to be rendered. 
> 
{{ '![C:/Users/labuser/Desktop/note.jpg](Template-Support_images/Template-Support_img1.jpeg)' | markdownify }}
{:.image }
_Note: We need to include jsrender.js script file to use the following template. Also the images mentioned are available in the samples installed  location, in the Content/Images folder._



[View]

<script id="treeTemplate" type="text/x-jsrender">



{{if hasChild}}

    <div class={{>name}} -style>{{>name}}</div>

{{else}}

    <div class="cont-list">

        <img class="con-img" src="../Content/Images/template-image-{{>imgId}}.png" />

        <div class="cont-del"></div>

        <div class="cont-details">

            <b>{{>name}}</b><br />

            <span>{{>city}}</span>

            <br />

            <span>{{>phone}}</span>

        </div>

        <div class="treeFooter"></div>

    </div>

{{/if}}



</script>





4. Using the TreeView helper, specify the Datasource for the TreeView and map the corresponding fields. In the “Template” property specify the “id” of your template as shown below.

[View]

<div style="width: 280px">

    @Html.EJ().TreeView("tree").TreeViewFields(s => s.Datasource((IEnumerable<template>)ViewBag.datasource).Id("id").ParentId("pid").Text("name").HasChild("hasChild").Expanded("expanded")).Template("#treeTemplate").ClientSideEvents(e => e.Create("oncreate"))

</div>



5. Add the following style to customize the appearance of the Template structure.

[View]

<style>

            #treeview .e-node-hover, #treeview .e-active

        {

            background-color: transparent;

            border-color: transparent;

        }

        #treeview .e-node-hover

        {

            opacity: 0.8;

        }



        .con-img

        {

            float: left;

        }



        .cont-list

        {

            background: none repeat scroll 0 0 white;

            border: 1px solid #BBBCBB;

            height: 85px;

            width: 200px;

            color: #5c5c5c;

            line-height: 17px;

        }



        .cont-details

        {

            margin-top: 12px;

            font-size: 13px;

        }



    .cont-del {

        background-image: url('../../Content/Images/remove-icon.png');

        background-position: -6px -10px;

        background-repeat: no-repeat;

        float: right;

        height: 16px;

        width: 16px;

        cursor: pointer;

    }



        .cont-list .treeFooter

        {

            height: 5px;

            width: 100%;

            background-color: gray;

            margin-top: 17px;

        }

</style>



6. Add the following script to delete the Tree nodes on clicking the delete icon.

[View]

<script type="text/javascript">

    function oncreate(evt) {

        var treeObj = $("#tree").data("ejTreeView");

        $("#tree").find(".cont-del").bind("click", function (e) {

            treeObj.removeNode($(e.target).parents("li").first());

        });

    }

</script>





Output of the TreeView after specifying the Template structure.

{{ '![](Template-Support_images/Template-Support_img2.png)' | markdownify }}
{:.image }


_Figure_ _53__: TreeView with Template_







