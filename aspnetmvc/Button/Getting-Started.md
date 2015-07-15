---
layout: post
title: Getting-Started
description: getting started
platform: ejmvc
control: Button
documentation: ug
---

# Getting Started

This section explains you briefly on how to create a Button in your application with ASP.NET MVC.

## Create your first Button in MVC

Essential ASP.NET MVC Button provides support to display a Button control within your webpage and allows you to Click, Toggle Click, Reset, and Submit. Using the following guidelines, you can customize Button for a real-time Multimedia player scenario. This allows you to Play, Pause, Stop, Mute, Unmute a music player. 

The following screenshot illustrates the functionality of Button in Multimedia player control.

Figure 1: Multimedia Player

Create Button Control in MVC

Essential ASP.NET MVC Button control contains built-in features like Click and different display option. You can easily create the Button control by using HTML helper as follows.

1. You can create an MVC Project and add necessary assemblies, styles and scripts to it.  Refer [MVC-Getting Started.](http://help.syncfusion.com/ug/js/Documents/gettingstartedwithmv.htm)
2. Add the following code example to the corresponding view page to render Button.



  &lt;table&gt;

      &lt;tr&gt;                

        &lt;td&gt;                    @Html.EJ().ToggleButton("playpause").Size(ButtonSize.Large).ShowRoundedCorner(true).ContentType(ContentType.TextAndImage).ToggleState(true).DefaultPrefixIcon("e-mediaplay").ActivePrefixIcon("e-mediapause").DefaultText("Play").ActiveText("Pause")



           &lt;/td&gt;

           &lt;td&gt;                    @Html.EJ().Button("mute").Size(ButtonSize.Large).ShowRoundedCorner(true).Text("Mute")

           &lt;/td&gt;

           &lt;td&gt;                   @Html.EJ().Button("unmute").Size(ButtonSize.Large).ShowRoundedCorner(true).Text("Unmute")

           &lt;/td&gt;           

            &lt;td&gt;                    @Html.EJ().Button("stop").Size(ButtonSize.Large).ShowRoundedCorner(true).Text("top")

            &lt;/td&gt;            

         &lt;/tr&gt;

&lt;/table&gt;





Create Multimedia Player

1. Add the Action Result for Audio control in HomeController.cs file.



public ActionResult MyAudio()

        {

            var file = Server.MapPath("../song.mp3");

            return File(file, "audio/mp3");

        }



2. Add the following code example to your view page to display Audio control and render the Button.



  &lt;div class="audiodiv"&gt;

    &lt;audio controls&gt;

        &lt;source src="@Url.Action("MyAudio","Home")" type="audio/mp3" /&gt;

        <p>Your browser does not support HTML 5 audio element</p>

    &lt;/audio&gt;

   &lt;/div&gt;

&lt;div&gt;

&lt;table&gt;

      &lt;tr&gt;                

        &lt;td&gt;                    @Html.EJ().ToggleButton("playpause").Size(ButtonSize.Large).ShowRoundedCorner(true).ContentType(ContentType.TextAndImage).ToggleState(true).ClientSideEvents(e => e.Create("play").Click("pause").Change("play")).DefaultPrefixIcon("e-mediaplay").ActivePrefixIcon("e-mediapause").DefaultText("Play").ActiveText("Pause")



           &lt;/td&gt;

           &lt;td&gt;                    @Html.EJ().Button("mute").Size(ButtonSize.Large).ShowRoundedCorner(true).ClientSideEvents(e => e.Click("mute")).Text("Mute")

           &lt;/td&gt;

           &lt;td&gt;                   @Html.EJ().Button("unmute").Size(ButtonSize.Large).ShowRoundedCorner(true).ClientSideEvents(e => e.Click("unmute")).Text("Unmute")

           &lt;/td&gt;           

            &lt;td&gt;                    @Html.EJ().Button("stop").Size(ButtonSize.Large).ShowRoundedCorner(true).ClientSideEvents(e => e.Click("stop")).Text("stop")

            &lt;/td&gt;            

         &lt;/tr&gt;

&lt;/table&gt;

&lt;/div&gt;



3. Add the following event function to script section in your view page to use Button control feature as the Multimedia player control.





&lt;script type="text/javascript"&gt;

           //getting audio control access and stored in variable v

           var v = document.getElementsByTagName("audio")[0];

            //trigger the audio control using variable v

           function play(e) {

                if (e.isChecked) {

                    v.play();

                }

                else {

                    v.pause();

                }

            }



            function start() {

                v.play();

            }

            function stop() {

                v.pause();

            }

            function mute()

            {                       

                v.volume = 0;

             }

            function unmute()

            {

               v.volume = 1;

            }

 &lt;/script&gt;



4. The following screenshot displays Multimedia player control.



{ ![](Getting-Started_images/Getting-Started_img1.png) | markdownify }
{:.image }


Create Office Ribbon

In this section, you can learn how to create a MS Office Ribbon used to change the style of the selected text. You can achieve this by using ASP.NET MVC Toggle Button control. You can change the styles by toggling the Button. Add the following code example to your view page to display OfficeRibbon control and render the Button.



&lt;table&gt;

   &lt;tr&gt;

     &lt;td&gt;                 

                    @Html.EJ().ToggleButton("Bold").Size(ButtonSize.Mini).ShowRoundedCorner(true).DefaultText("<b>B</b>").ActiveText("B").ClientSideEvents(e => e.Click("bold"))



      &lt;/td&gt;

       &lt;td&gt;

                    @Html.EJ().ToggleButton("italic").Size(ButtonSize.Mini).ShowRoundedCorner(true).DefaultText("I").ActiveText("<li>I</li>").ClientSideEvents(e => e.Click("italic"))



       &lt;/td&gt;

        &lt;td&gt;

                    @Html.EJ().ToggleButton("underline").Size(ButtonSize.Mini).ShowRoundedCorner(true).DefaultText("U").ActiveText("<u>U</u>").ClientSideEvents(e => e.Click("underline"))



        &lt;/td&gt;



      &lt;/tr&gt;



 &lt;/table&gt;



1. Add the following code example in your view page for sample text.



&lt;div class="sample"&gt;

    <span id="sampletext">Hi Welcome!&lt;/span&gt;

&lt;/div&gt;





2. Add the following event function to the script section in your view page to use Button control feature as the Multimedia player control.



&lt;script type="text/javascript"&gt;



            function bold(e) {                

                if (e.isChecked) {



                    $(".sample span").wrap("&lt;b&gt;&lt;/b&gt;");

                } else {



                    $(".sample span").unwrap("&lt;b&gt;&lt;/b&gt;");

                }

            }

            function italic(e) {

                if (e.isChecked) {

                    $(".sample span").wrap("&lt;i&gt;&lt;/i&gt;");

                } else {



                    $(".sample span").unwrap("&lt;i&gt;&lt;/i&gt;");

                }

            }

            function underline(e) {

                if (e.isChecked) {

                    $(".sample span").wrap("&lt;u&gt;&lt;/u&gt;");

                } else {



                    $(".sample span").unwrap("&lt;u&gt;&lt;/u&gt;");

                }

            }



        &lt;/script&gt;





3. The following screenshots display Office Ribbon control.



{ ![](Getting-Started_images/Getting-Started_img2.png) | markdownify }
{:.image }




{ ![](Getting-Started_images/Getting-Started_img3.png) | markdownify }
{:.image }


