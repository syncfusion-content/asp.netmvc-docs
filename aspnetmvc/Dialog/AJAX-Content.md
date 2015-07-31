---
layout: post
title: AJAX-Content
description: ajax content
platform: ejmvc
control: Dialog
documentation: ug
---

## AJAX Content

The Dialog provides AJAX content support where you can add the HTML content to the Dialog content. 

Configure AJAX Content

The following steps explains you the implementation of AJAX content in the Dialog control. 

1. In the VIEW page set a helper element for rendering the Dialog control. 





[CHTML]

// In the CHTML page add the Dialog widget and set the ContentUrl from the file reference and set ContentType as ajax.



@{Html.EJ().Dialog("dialog").Title("Syncfusion Dialog").ContentUrl("../Content/Dialog/twitter.html").ContentType("ajax").Width(300).Height("200").Render();}





2. Content inside the twitter.html 



[twitter.html]



<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">

<head>

    <title></title>

    <style>

        .twitter-logo {

            background-color: #FFFFFF;

        }



        .cont-list img {

            float: left;

            height: 40px;

            padding-right: 6px;

            padding-left: 6px;

        }



        .comments-list {

            /* background-color: #EFEFEF; */

            height: 210px;

        }



        .comments {

            padding: 10px;

            color: #074B92;

            font-weight: 600;

        }



        .cont-list {

            border-bottom: 1px solid #BBBCBB;

            padding-top: 9px;

            padding-bottom: 9px;

        }



            .cont-list:last-child {

                border-bottom: none;

                padding-bottom: 0;

            }



        .time-panel {

            float: right;

            color: #2382C3;

            margin-right: 10px;

        }



        .headername {

            font-size: 16px;

            font-weight: 600;

            color: #074B92;

        }



        .c-list {

            float: right;

            margin-top: -11px;

            padding-right: 12px;

        }

    </style>

</head>

<body>

    <div>

        <div class="twitter-logo">

            <img src="../Content/Images/twitter.jpg" alt="twitter" />

        </div>

        <div class="comments-list">

            <div class="cont-list">

                <img src="../Content/Images/8.png" alt="contact" />

                <div class="time-panel">1 hr</div>

                <b class="headername">Erik Linden</b><br />

                Orubase is the only mobile application development framework built especially for developing complex line-of-business mobile applications targeting iOS, Android, and Windows Phone platforms in the shortest possible timeframe. 

                <div class="comments">

                    <div class="c-list">Retweet</div>

                    <div class="c-list">Reply</div>

                    <div class="c-list">Share</div>

                </div>

            </div>

            <div class="cont-list">

                <img src="../Content/Images/6.png" alt="contact" />

                <div class="time-panel">2 hr</div>

                <b class="headername">John Louis</b><br />

                All the components in the ASP.NET MVC Essential Studio have been built from the ground up with performance in mind and are extremely lightweight.

                 <div class="comments">

                     <div class="c-list">Retweet</div>

                     <div class="c-list">Reply</div>

                     <div class="c-list">Share</div>

                 </div>

            </div>

        </div>

    </div>

</body>

</html>





3. The output of Dialog with AJAX content.

{{ '![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/dia ajax.PNG](AJAX-Content_images/AJAX-Content_img1.png)' | markdownify }}
{:.image }


_Figure 1__7__: Dialog with “AJAX Content_                                                           

