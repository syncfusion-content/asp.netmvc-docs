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



  <table>

      <tr>                

        <td>                    @Html.EJ().ToggleButton("playpause").Size(ButtonSize.Large).ShowRoundedCorner(true).ContentType(ContentType.TextAndImage).ToggleState(true).DefaultPrefixIcon("e-mediaplay").ActivePrefixIcon("e-mediapause").DefaultText("Play").ActiveText("Pause")



           </td>

           <td>                    @Html.EJ().Button("mute").Size(ButtonSize.Large).ShowRoundedCorner(true).Text("Mute")

           </td>

           <td>                   @Html.EJ().Button("unmute").Size(ButtonSize.Large).ShowRoundedCorner(true).Text("Unmute")

           </td>           

            <td>                    @Html.EJ().Button("stop").Size(ButtonSize.Large).ShowRoundedCorner(true).Text("top")

            </td>            

         </tr>

</table>





Create Multimedia Player

1. Add the Action Result for Audio control in HomeController.cs file.



public ActionResult MyAudio()

        {

            var file = Server.MapPath("../song.mp3");

            return File(file, "audio/mp3");

        }



2. Add the following code example to your view page to display Audio control and render the Button.



  <div class="audiodiv">

    <audio controls>

        <source src="@Url.Action("MyAudio","Home")" type="audio/mp3" />

        <p>Your browser does not support HTML 5 audio element</p>

    </audio>

   </div>

<div>

<table>

      <tr>                

        <td>                    @Html.EJ().ToggleButton("playpause").Size(ButtonSize.Large).ShowRoundedCorner(true).ContentType(ContentType.TextAndImage).ToggleState(true).ClientSideEvents(e => e.Create("play").Click("pause").Change("play")).DefaultPrefixIcon("e-mediaplay").ActivePrefixIcon("e-mediapause").DefaultText("Play").ActiveText("Pause")



           </td>

           <td>                    @Html.EJ().Button("mute").Size(ButtonSize.Large).ShowRoundedCorner(true).ClientSideEvents(e => e.Click("mute")).Text("Mute")

           </td>

           <td>                   @Html.EJ().Button("unmute").Size(ButtonSize.Large).ShowRoundedCorner(true).ClientSideEvents(e => e.Click("unmute")).Text("Unmute")

           </td>           

            <td>                    @Html.EJ().Button("stop").Size(ButtonSize.Large).ShowRoundedCorner(true).ClientSideEvents(e => e.Click("stop")).Text("stop")

            </td>            

         </tr>

</table>

</div>



3. Add the following event function to script section in your view page to use Button control feature as the Multimedia player control.





<script type="text/javascript">

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

 </script>



4. The following screenshot displays Multimedia player control.



{{ '![](Getting-Started_images/Getting-Started_img1.png)' | markdownify }}
{:.image }


Create Office Ribbon

In this section, you can learn how to create a MS Office Ribbon used to change the style of the selected text. You can achieve this by using ASP.NET MVC Toggle Button control. You can change the styles by toggling the Button. Add the following code example to your view page to display OfficeRibbon control and render the Button.



<table>

   <tr>

     <td>                 

                    @Html.EJ().ToggleButton("Bold").Size(ButtonSize.Mini).ShowRoundedCorner(true).DefaultText("<b>B</b>").ActiveText("B").ClientSideEvents(e => e.Click("bold"))



      </td>

       <td>

                    @Html.EJ().ToggleButton("italic").Size(ButtonSize.Mini).ShowRoundedCorner(true).DefaultText("I").ActiveText("<li>I</li>").ClientSideEvents(e => e.Click("italic"))



       </td>

        <td>

                    @Html.EJ().ToggleButton("underline").Size(ButtonSize.Mini).ShowRoundedCorner(true).DefaultText("U").ActiveText("<u>U</u>").ClientSideEvents(e => e.Click("underline"))



        </td>



      </tr>



 </table>



1. Add the following code example in your view page for sample text.



<div class="sample">

    <span id="sampletext">Hi Welcome!</span>

</div>





2. Add the following event function to the script section in your view page to use Button control feature as the Multimedia player control.



<script type="text/javascript">



            function bold(e) {                

                if (e.isChecked) {



                    $(".sample span").wrap("<b></b>");

                } else {



                    $(".sample span").unwrap("<b></b>");

                }

            }

            function italic(e) {

                if (e.isChecked) {

                    $(".sample span").wrap("<i></i>");

                } else {



                    $(".sample span").unwrap("<i></i>");

                }

            }

            function underline(e) {

                if (e.isChecked) {

                    $(".sample span").wrap("<u></u>");

                } else {



                    $(".sample span").unwrap("<u></u>");

                }

            }



        </script>





3. The following screenshots display Office Ribbon control.



{{ '![](Getting-Started_images/Getting-Started_img2.png)' | markdownify }}
{:.image }




{{ '![](Getting-Started_images/Getting-Started_img3.png)' | markdownify }}
{:.image }


