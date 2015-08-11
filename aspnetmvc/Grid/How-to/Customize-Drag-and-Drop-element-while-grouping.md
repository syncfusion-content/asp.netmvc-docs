---
layout: post
title: Customize-Drag-and-Drop-element-while-grouping
description: customize drag and drop element while grouping
platform: wpf
control: Grid
documentation: ug
---

### Customize Drag and Drop element while grouping

In this section, you can learn how to customize drag and drop element. This drag and drop element is framed by using CSS classes with default values. When you want to change or customize drag and drop element, then just override default values of CSS class values. e-cloneproperties is the name of drag and drop element in CSS class.



[MVC]



[razor]

<style type="text/css">

        .e-grid .e-cloneproperties {

            background-color: black;

        }

</style>



@(Html.EJ().Grid<EditableOrder>("FlatGrid")

        .Datasource((IEnumerable<object>)ViewBag.datasource)

        .AllowGrouping(true)

        .AllowPaging()

        )



[controller]

namespace MVCSampleBrowser.Controllers

{

    public partial class GridController : Controller

    {

        public ActionResult Default()

        {

            ViewBag.datasource = OrderRepository.GetAllRecords();

            return View();

        }

    }

}







The following output is displayed as a result of the above code example.

![](Customize-Drag-and-Drop-element-while-grouping_images/Customize-Drag-and-Drop-element-while-grouping_img1.png)



