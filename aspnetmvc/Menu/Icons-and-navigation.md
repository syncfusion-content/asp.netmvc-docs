---
layout: post
title: Icons-and-navigation
description: icons and navigation
platform: ejmvc
control: Menu
documentation: ug
---

## Icons and navigation

Icons are the images that is displayed in the Menu control. To specify the menu with icons you can use SpriteCssClass property to display the icons. 

1. Add the following code in your View page.





<table>
<tr>
<td>
[CSHTML]// Add the following code in your CSHTML page       @Html.EJ().Menu("menujson").MenuFields(f => f.Datasource((IEnumerable<Check.Controllers.CheckController.icons>)ViewBag.datasource).Id("pid").Text("mtext").ParentId("parent").SpriteCssClass("sprite"))</td></tr>
<tr>
<td>
[CS]// In the controller page add the codeusing System;using System.Collections.Generic;using System.Linq;using System.Web;using System.Web.Mvc;using Check.Models;namespace Check.Controllers{    public class CheckController : Controller    {        public class icons        {            public string mtext { get; set; }            public string sprite { get; set; }            public int pid { get; set; }            public string parent { get; set; }        }                List<icons> menu = new List<icons>();        public ActionResult DataBindingJson()        {menu.Add(new MenuJson { pid = 1, mtext = "Group A", parent = null });            menu.Add(new MenuJson { pid = 2, mtext = "Group B", parent = null });            menu.Add(new MenuJson { pid = 3, mtext = "Group C", parent = null });            menu.Add(new MenuJson { pid = 4, mtext = "Group D", parent = null });            menu.Add(new MenuJson { pid = 5, mtext = "Group E", parent = null });            menu.Add(new MenuJson { pid = 11, parent = "1", mtext = "Algeria", sprite = "flag-dz" });            menu.Add(new MenuJson { pid = 12, parent = "1", mtext = "Armenia", sprite = "flag-am" });            menu.Add(new MenuJson { pid = 13, parent = "1", mtext = "Bangladesh", sprite = "flag-bd" });            menu.Add(new MenuJson { pid = 14, parent = "1", mtext = "Cuba", sprite = "flag-cu" });            menu.Add(new MenuJson { pid = 15, parent = "2", mtext = "Denmark", sprite = "flag-dk" });            menu.Add(new MenuJson { pid = 16, parent = "2", mtext = "Egypt", sprite = "flag-eg" });            menu.Add(new MenuJson { pid = 17, parent = "3", mtext = "Finland", sprite = "flag-fi" });            menu.Add(new MenuJson { pid = 18, parent = "3", mtext = "India", sprite = "flag-in" });            menu.Add(new MenuJson { pid = 19, parent = "3", mtext = "Malaysia", sprite = "flag-my" });            menu.Add(new MenuJson { pid = 20, parent = "4", mtext = "New Zealand", sprite = "flag-nz" });            menu.Add(new MenuJson { pid = 21, parent = "4", mtext = "Norway", sprite = "flag-no" });            menu.Add(new MenuJson { pid = 22, parent = "4", mtext = "Romania", sprite = "flag-ro" });            menu.Add(new MenuJson { pid = 23, parent = "5", mtext = "Singapore", sprite = "flag-sg" });            menu.Add(new MenuJson { pid = 24, parent = "5", mtext = "Thailand", sprite = "flag-th" });            menu.Add(new MenuJson { pid = 25, parent = "5", mtext = "Ukraine", sprite = "flag-ua" });            menu.Add(new MenuJson { pid = 26, parent = "11", mtext = "First Place" });            menu.Add(new MenuJson { pid = 27, parent = "12", mtext = "Second Place" });            menu.Add(new MenuJson { pid = 28, parent = "13", mtext = "Third place" });            menu.Add(new MenuJson { pid = 29, parent = "14", mtext = "Fourth Place" });            menu.Add(new MenuJson { pid = 30, parent = "15", mtext = "First Place" });            menu.Add(new MenuJson { pid = 31, parent = "16", mtext = "Second Place" });            menu.Add(new MenuJson { pid = 32, parent = "17", mtext = "Third Place" });            menu.Add(new MenuJson { pid = 33, parent = "18", mtext = "First Place" });            menu.Add(new MenuJson { pid = 34, parent = "19", mtext = "Second Place" });            menu.Add(new MenuJson { pid = 35, parent = "20", mtext = "First Place" });            menu.Add(new MenuJson { pid = 36, parent = "21", mtext = "Second Place" });            menu.Add(new MenuJson { pid = 37, parent = "22", mtext = "Third place" });            menu.Add(new MenuJson { pid = 38, parent = "23", mtext = "Third Place" });            menu.Add(new MenuJson { pid = 39, parent = "24", mtext = "First Place" });            menu.Add(new MenuJson { pid = 40, parent = "25", mtext = "Second Place" });            ViewBag.datasource = menu;            return View();        }    }} </td></tr>
</table>




2. Add the following code in your style section.



[CSS]



<style type="text/css">

        #menujson {

            margin-left: 50px;

        }

        .e-menu li > ul > li > a {

            padding: 3px 24px 3px 35px;

        }

        [class^="mail-"],

        [class*="mail-"] {

            background-image: url("../images/spriteimage.png");

            height: 18px;

            left: 2px;

            top: 4px;

            width: 24px;

        }

        .mail-dz { background-position: -68px -15px;     }

        .mail-am { background-position: 91px -45px;      }

        .mail-bd { background-position: -98px 0;         }

        .mail-cu { background-position: -607px -221px;   }

        .mail-dk { background-position: -67px -15px;     }

        .mail-eg { background-position: 600px -15px;     }

        .mail-fi { background-position: 12441px 12458px; }

        .mail-in { background-position: -307px -103px;   }

        .mail-my { background-position: 240px -102px;    }

        .mail-nz { background-position: -100px -45px;    }

        .mail-no { background-position: -69px -45px;     }

        .mail-pl { background-position: -129px -45px;    }

        .mail-ca { background-position: -1345px -387px;  }

        .mail-cn { background-position: -427px -42px;    }

        .mail-ee { background-position: -706px -15px;    }

        .mail-es { background-position: -1157px -43px    }

    </style>



The following screenshot displays the output for the above code.                                                                                                       

{{ '![](Icons-and-navigation_images/Icons-and-navigation_img1.png)' | markdownify }}
{:.image }


_Figure_ _24__: Menu with Icons_

Navigation

Navigation in Menu control is the default usage to navigate into the other web page. You can navigate to another page in menu item by providing link to the menu items. Navigation in Menu control can be achieved by placing “href” path to the anchor tag. Use the following code sample for navigating in Menu control.

1. Add the following code in your View page.



[CSHTML]

// Add the following code in your CSHTML page.

    <div class="imgframe">

    @Html.EJ().Menu("weblink").Items(items =>

        {

            items.Add().Url("#").Id("searchengine").Text("Search engine").Children(child =>

                {

                    child.Add().Url("http://www.bing.com/").Text("Bing");

                    child.Add().Url("https://www.google.co.in/").Text("Google");

                    child.Add().Url("https://in.yahoo.com/").Text("Yahoo");

                    child.Add().Url("http://www.rediff.com/").Text("Rediff");

                });

            items.Add().Url("http://allthingsd.com/").Text("All things digital");



            items.Add().Url("").Text("Electronics").Children(child =>

                {

                    child.Add().Url("http://www.engadget.com/").Text("Engadget");

                    child.Add().Url("http://www.electronista.com/").Text("Electronista");

                    child.Add().Url("http://www.gearlog.com/").Text("Gearlog");

                });

            items.Add().Url("http://www.centernetworks.com/").Text("Center networks");

            items.Add().Url("http://www.webpronews.com/").Text("Web pronews");



        }).Width("500")

</div>





The following screenshot displays the output for the above code example.            

{{ '![](Icons-and-navigation_images/Icons-and-navigation_img2.png)' | markdownify }}
{:.image }


_Figure_ _25__: Navigation of Menu_

When you click on “Google” that is present under “Search engine”, it navigates to the link that you specified in the sample code. Then the output is as follows.

{{ '![C:/Users/kaliswaran/Desktop/menu2.PNG](Icons-and-navigation_images/Icons-and-navigation_img3.png)' | markdownify }}
{:.image }


_Figure_ _26__: After navigating to a menu item_

